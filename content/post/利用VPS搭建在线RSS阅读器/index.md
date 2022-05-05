+++
author = "WNO-IQ"
title = "Use VPS to build online feed reader - Miniflux"
date = "2022-04-15"
keywords = ["RSS","Fever API","VPS","Feed reader","miniflux"]
description = "A guidance to use VPS to build Miniflux"
tags = [
    "RSS"
]
categories = [
    "分享"
]
image = "enpre.png"
+++

## Choosing program

There is a variety of online RSS readers, but many projects stop upgrading. [FreshRSS](https://github.com/FreshRSS/FreshRSS) is a project based on PHP which updates recently. But I donnot want to use PHP, so I choose to use [Miniflux](https://github.com/miniflux/v2) which is based on Golang.
<br>

## Screenshots

![Image 1](enpre.png)![Image 2](zhpre.png)
<br>

## Start from zero

I am noob of Linux. So I checked the instruction step by step and searched for info from Google.
You can also check [Installation Instructions](https://miniflux.app/docs/installation.html) of Miniflux directly.

Main steps：

- Install Postgresql
- Configure database
- Install Miniflux
- Configure Miniflux

<br>

### Install Postgresql

Make sure u can use `sudo` before installation.

```Shell
sudo apt update
sudo apt install postgresql postgresql-contrib
```

After installation，PostgreSQL service will automatically start up.

### Configure database

During installation of PostgreSQL, it will create user `postgres`. The user is the SUPERUSER of PostgreSQL, which is equivalent of `root` of MySQL.

- The we need to use `postgres` to log in the database

```Shell
sudo su - postgres
```

- Create an account for miniflux
  `createuser -P miniflux`

- Filling password
  Create a database for user `miniflux`
  `createdb -O miniflux miniflux2`

- Create hstore extension

```Shell
psql miniflux -c 'create extension hstore'
```

- Since hstore needs `SUPERUSER` privilege，we need to give the privilege to `miniflux` before run the migration, and remove it after migration.

```Shell
psql ALTER USER miniflux WITH SUPERUSER;
# Run the migrations (miniflux -migrate)
psql ALTER USER miniflux WITH NOSUPERUSER;
```

### Download miniflux

For some reasons, I cannot use docker, so I choose manual installation here.

Precompiled binary is provided, so it's EZ to install.

- Download it on ur server.

```Shell
wget https://github.com/miniflux/v2/releases/download/2.0.36/miniflux-linux-amd64
```

- I choose to put it in `/usr/local/bin`, and make the file executable

```Shell
chmod +x miniflux
```

- Migrate database
  If u don't set the database as above, u should set the directory of database before migration.

```Shell
export DATABASE_URL=...
```

#### Database Connection Parameters

Miniflux uses the Golang library pq to communicate with PostgreSQL. The list of connection parameters are available on this page.

The default value for `DATABASE_URL` is `user=postgres password=postgres dbname=miniflux2 sslmode=disable`.

You could also use the URL format `postgres://postgres:postgres@localhost/miniflux2?sslmode=disable`.

> Password that contains special characters like ^ might be rejected since Miniflux 2.0.3. Golang v1.10 is now validating the password and will return this error: `net/url: invalid userinfo`. To avoid this issue, do not use the URL format for `DATABASE_URL` or make sure the password is URL encoded.

- Make sure the connection is well configured and execute:

```Shell
miniflux -migrate
```

- If shell warns：`password authentication failed for user “postgres”`, we can:

1. Open `/etc/postgresql/11/main/pg_hba.conf`
2. Edit the method, turn `md5` to `trust` and then save.
   ![pg_hba.conf](pg_hba.png)

- Create admin user

```Shell
miniflux -create-admin
```

Then u can run miniflux with command `miniflux`, but I recommand to create a configuration file fisrt, so miniflux can be configured according to the file. Otherwise it is thorny to change the environmental variable one by one.

```Shell
miniflux -config-dump
```

It will output all te parameters，and copy all of them. Create a file in `/etc` called `miniflux.conf` and paste in the file. So you can change the configuration in the file. Details of [Configuration Parameters](https://miniflux.app/docs/configuration.html) can be looked up here.

- Start up Miniflux with configuration file

```Shell
miniflux -c /etc/miniflux.conf
```

### 💡Mention

- You should configure a process manager like systemd or supervisord to supervise the Miniflux daemon.
- Miniflux is deployed on port 8080 by default. If you would like to run it on port 80 or 443, you can use Reverse-Proxy or other methods which are all illustrated in [How to's✍](https://miniflux.app/docs/howto.html) here.
- More information can be checked in official document：[_🔗Link_](https://miniflux.app/docs/index.html)

<br>

## Settings in user interface

- Use the admin account created before to log in. You can change languages, time zone, theme, create new users, configure FeverAPI...
- You can import feeds by entring url each time or use opml file to import.
- There are many projects of Miniflux in Github [_🔗Link_](https://github.com/search?p=1&q=miniflux&type=Repositories)

<br>

## Reference

[Miniflux Document](https://miniflux.app/docs/index.html)
[how-to-install-postgresql-on-ubuntu-18-04(in Chinese)](https://www.myfreax.com/how-to-install-postgresql-on-ubuntu-18-04/)
[Postgresql error(in Chinese)](https://blog.csdn.net/qq_44964308/article/details/104638675)
