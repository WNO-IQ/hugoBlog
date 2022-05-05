+++
author = "我无IQ"
title = "利用VPS搭建在线RSS阅读器Miniflux"
date = "2022-04-15"
keywords = ["RSS","Fever API","VPS","Feed reader","miniflux"]
description = "利用VPS搭建在线RSS阅读器Miniflux"
tags = [
    "RSS"
]
categories = [
    "分享"
]
image = "zhpre.png"
+++

## 起因

最近看到个虚拟主机挺便宜的，而且商家说还能用宝塔面板的全功能，感觉挺神奇的就买了一年体验了一下。 买来之后也不知道干什么，毕竟我其他网站全是部署在 Vercel 上的，后来想了想不如搭建一个在线 RSS 阅读器算了，把资讯全收集起来，可以提高上网冲浪 🏄‍ 的效率
<br>

## 挑选程序

搭建在线 RSS 阅读器的程序挺多的，但由于 RSS 的使用人数感觉并不是很多，很多 RSS 的项目都停止更新了。 近期有更新的项目有基于 PHP 的 [FreshRSS](https://github.com/FreshRSS/FreshRSS)，部署很方便，甚至都可以部署在虚拟主机上。 但是由于我买的这个“虚拟主机”支持宝塔面板全功能，也就是说可以用终端，感觉和 VPS 差不多，所以我就采用了基于 Go 的 [Miniflux](https://github.com/miniflux/v2)
<br>

## 截图展示

![Image 1](enpre.png)![Image 2](zhpre.png)
<br>

## 从零安装

我也是什么都不会的小白，一路看教程过来的，就做个简单的过程介绍吧。
当然你也可以直接看 miniflux 的 [Installation Instructions](https://miniflux.app/docs/installation.html)

主要步骤有：

- 安装 Postgresql 数据库
- 设置数据库
- 下载 miniflux 并设置权限
- 设置 miniflux

<br>

### 安装 Postgresql 数据库

安装前确保你有`sudo`的权限嗷，然后我们再去安装下 Postgresql，程序的要求是`Only PostgreSQL >= 9.5 is supported`

```Shell
sudo apt update
sudo apt install postgresql postgresql-contrib
```

如果提示有什么依赖没有装那就自己装一下吧= =
安装完成后，PostgreSQL 服务将自动启动。

### 设置数据库

在安装 PostgreSQL 时会自动创建 postgres 用户。该用户是 PostgreSQL 的超级用户，它等效于 MySQL 根用户。

- 然后我们需要用`postgres`用户来登录到数据库

```Shell
sudo su - postgres
```

- 给 miniflux 创建个用户
  `createuser -P miniflux`

- 然后按照提示输个两遍设置给 miniflux 的密码
  密码设置完后给 ta 建个数据库
  `createdb -O miniflux miniflux2`

- 创建 hstore 扩展

```Shell
psql miniflux -c 'create extension hstore'
```

- 由于 hstore 需要 superuser 权限，我们需要在 migration 前赋予 miniflux 这个数据库用户权限，然后在操作完后可以移除 ta 的权限

```Shell
psql ALTER USER miniflux WITH SUPERUSER;
# Run the migrations (miniflux -migrate) 这个操作之后才会用到
psql ALTER USER miniflux WITH NOSUPERUSER;
```

### 下载 miniflux 并设置权限

我的商家的虚拟主机虽然能用终端，但是用不了 docker，所以这里我选择的是手动安装。

由于作者提供了已经编译好的程序，安装就很方便了。

- 找个地方下载程序

```Shell
wget https://github.com/miniflux/v2/releases/download/2.0.36/miniflux-linux-amd64
```

- 我这里是把 ta 放在`/usr/local/bin`这个目录里面，然后给 ta 允许执行的权限

```Shell
chmod +x miniflux
```

- 迁移数据库
  如果你的数据库是按照上述设置装在 localhost 上的那就直接运行，不然要提前设置下数据库的路径

```Shell
export DATABASE_URL=...
```

下面是作者关于数据库连接参数的说明：

#### Database Connection Parameters

Miniflux uses the Golang library pq to communicate with PostgreSQL. The list of connection parameters are available on this page.

The default value for `DATABASE_URL` is `user=postgres password=postgres dbname=miniflux2 sslmode=disable`.

You could also use the URL format `postgres://postgres:postgres@localhost/miniflux2?sslmode=disable`.

> Password that contains special characters like ^ might be rejected since Miniflux 2.0.3. Golang v1.10 is now validating the password and will return this error: `net/url: invalid userinfo`. To avoid this issue, do not use the URL format for `DATABASE_URL` or make sure the password is URL encoded.

- 确保数据库连接设置没问题之后运行

```Shell
miniflux -migrate
```

- 若运行上面的命令时报错，出现：`password authentication failed for user “postgres”`，我们可以：

1. 打开`/etc/postgresql/11/main/pg_hba.conf`
2. 修改认证方式，将 md5“全部”改为 trust，然后保存。
   ![pg_hba.conf](pg_hba.png)

- 创建管理员用户

```Shell
miniflux -create-admin
```

然后可以直接用命令`miniflux`运行了，但是我推荐这里可以先创建一个配置文件，让 miniflux 根据这个配置文件运行，不然一个一个改环境变量来配置太麻烦了。

```Shell
miniflux -config-dump
```

ta 会把所有的参数全输出一遍，然后你可以把这些参数全复制一下，在`/etc`目录下新建一个文件`miniflux.conf`，把复制的东西粘贴一下，在这个文件里修改配置。 你可以在 [Configuration Parameters](https://miniflux.app/docs/configuration.html) 这里查看各个参数的设置和含义。

- 修改完之后用这个命令启动，ta 就会根据这个配置文件启动了

```Shell
miniflux -c /etc/miniflux.conf
```

### 💡 注意

- Miniflux 需要一个进程管理器来确保 miniflux 进程，例如 systemd 或者 supervisord
- Miniflux 默认是运行在 8080 端口上的，想要通过 80/443 端口访问的话可以设置反向代理或者用其他的方式 [官方文档里有写 ✍ How to's](https://miniflux.app/docs/howto.html)
- 更多内容可以在官方文档上查看：[_🔗Link_](https://miniflux.app/docs/index.html)

<br>

## 网站设置

- 用之前的创建的管理员账号登录，设置里可以修改语言、时区、主题、新建用户、设置 FeverAPI 等。
- 在‘源’里面可以一个一个导入或者通过 opml 文件批量导入 RSS 订阅
- Github 上有很多关于 Miniflux 的项目 [_🔗Link_](https://github.com/search?p=1&q=miniflux&type=Repositories)

<br>

## 关于这个虚拟主机

这个是“虚拟主机”的[🔗 链接](https://yun.blankwings.net/vhost/vhost.html)，￥ 80 起一年，感兴趣的可以看看（非利益相关，不是广告，也没收钱）

<br>

## 参考

[Miniflux Document](https://miniflux.app/docs/index.html)
[how-to-install-postgresql-on-ubuntu-18-04/](https://www.myfreax.com/how-to-install-postgresql-on-ubuntu-18-04/)
[Postgresql error](https://blog.csdn.net/qq_44964308/article/details/104638675)
