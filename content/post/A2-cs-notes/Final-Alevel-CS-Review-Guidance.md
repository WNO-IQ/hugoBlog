+++
author = "WNO-IQ"
title = "Final Alevel CS Review Guidance"
date = "2022-05-12"
description = "A final CS note"
tags = [
    "Study",
    "Notes"
]
categories = [
    "a2-cs-notes"
]
image = "cs-note-img/wallhaven-wq5m26.png"
+++

# Data Representation
## User-defined data types
![](cs-note-img/Pastedimage20220511190506.png)
### Non-composite types
- enumerated
    - `TYPE Courses = (English,Chinese,Maths)`
- pointer
    - `TYPE SelectParts = ^Parts  // It reference the memory location in thich the part is stored`
### Define & Use composite data types
- set, record and class/object
- Pseudocode example of class:
```pseudocode
TYPE School
    DECLARE StudentNumber : INTEGEAR
    DECLARE Courses : (English,Chinese,Maths)
    DECLARE StudentList : ARRAY[0:200] OF STRING
ENDTYPE
```
<br>

## File organisation and access
### Organisation
- Serial
 ![](cs-note-img/Pastedimage20220511192816.png)

- Sequential
![](cs-note-img/Pastedimage20220511192827.png)

- Random
    - Only that the access can be to any record in the file without sequential reading of the file.
    - A separate index file is created which has two fields per record.
    - The first field has the key field value and the second field has a value for the position of this key field value in the main file.

### Access
- Sequential
- Direct

<br>

## Floating-point numbers, representation and manipulation
- Overflow
- Underflow
- Rounding errors

![](cs-note-img/Pastedimage20220511193711.png)
![](cs-note-img/Pastedimage20220511193233.png)
![](cs-note-img/Pastedimage20220511193208.png)

----

# Communication and internet technologies
## Protocols
### Importance
![](cs-note-img/Pastedimage20220511194104.png)
### TCP/IP
![](cs-note-img/Pastedimage20220511194418.png)
![](cs-note-img/Pastedimage20220511194108.png)
### Bittorrent
- file sharing
- peer-to-peer

![](cs-note-img/Pastedimage20220511194119.png)

### Other protocols
- FTP
- IMAP, SMTP, POP3
- HTTP
- ......



<br>

## Circuit switching, packet switching
### Packet
![](cs-note-img/Pastedimage20220511194048.png)
### Circuit
-  A method of data transfer in which the message is sent over a dedicated communication channel.


----

# Hardware and Virtual Machines
## Processors, Parallel Processing and Virtual Machines
### Reduced Instruction Set Computers (RISC)
### Complex Instruction Set Computers (CISC)
### Parallel processing
- SISD
- SIMD
- MISD
- MIMD

![](cs-note-img/Pastedimage20220511195523.png)
![](cs-note-img/Pastedimage20220511195457.png)

<br>

## Logic Circuits
### Half-adder

![](cs-note-img/Pastedimage20220511201803.png)

- 2 input
    - 2 output
        - carry bit
        - sum bit

<br>

### Full-adder
- 3 input
    - 2 output   
        - carry bit
        - sum bit

<br>

### Flip-flop
#### SR
-   It can be constructed with two NAND gates or two NOR gates.
-   Used as a storage device for 1 bit in the RAM, since it’s values can be altered
-   Issue: When the both the input signals are 1 (invalid state) the flip-flop sets the value of Q and Q’ to 0.

![](cs-note-img/Pastedimage20220511201405.png)

#### JK
- The J acts as a set input and the K as a clear input.
-   There is a clock input to synchronise the inputs.
-   When both the input signals are one, Q toggles.

![](cs-note-img/Pastedimage20220511201448.png)

#### Usage
- Flip-flops are used to build
    -   Data storage elements
    -   Digital circuits

<br>

## Boolean Algebra

![](cs-note-img/Pastedimage20220511201901.png)

<br>

### Karnaugh maps
![](cs-note-img/Pastedimage20220511201954.png)


----

# System Software
## Purposes of an Operating System (OS)
- OS provides utility software, user interface (GUI,CLI), resources management, multi-tasking, a platform to run code......


![](cs-note-img/Pastedimage20220511202507.png)
![](cs-note-img/Pastedimage20220511202502.png)
![](cs-note-img/Pastedimage20220511202437.png)
![](cs-note-img/Pastedimage20220511202443.png)
![](cs-note-img/Pastedimage20220511202447.png)
![](cs-note-img/Pastedimage20220511202900.png)
![](cs-note-img/Pastedimage20220511202915.png)
<br>

## Translation Software

![](cs-note-img/Pastedimage20220511202937.png)
![](cs-note-img/Pastedimage20220511202956.png)
<br>


### BNF notation
![](cs-note-img/Pastedimage20220512090545.png)

<br>

### RPN expression
![](cs-note-img/Pastedimage20220512083731.png)
- `::=`
- `|`

----

# Security
## Encryption, Encryption Protocols and Digital certificates
- public key, private key, plain text, cipher text, encryption
- <mark style="background: #FFF3A3A6;">symmetric</mark> key cryptography and <mark style="background: #FFF3A3A6;">asymmetric</mark> key cryptography

<br>

### Symmetric key encryption
![](cs-note-img/Pastedimage20220512093231.png)
![](cs-note-img/Pastedimage20220512093357.png)

<br>

### Asymmetric key encryption
![](cs-note-img/Pastedimage20220512095223.png)
![](cs-note-img/Pastedimage20220512095353.png)

#### Private keys & public key
![](cs-note-img/Pastedimage20220512091128.png)

<br>

### Digital certificate
![](cs-note-img/Pastedimage20220512091041.png)
![](cs-note-img/Pastedimage20220512091102.png)
<br>

### Digital signature
![](cs-note-img/Pastedimage20220512091149.png)
![](cs-note-img/Pastedimage20220512092527.png)
![](cs-note-img/Pastedimage20220512092653.png)
<br>

### Quantum cryptography
![](cs-note-img/Pastedimage20220512093850.png)

<br>

### SSL & TLS
![](cs-note-img/Pastedimage20220512095609.png)
![](cs-note-img/B5629FD36BB6453BB2B402113D793E0E.jpg)
![](cs-note-img/Pastedimage20220512095708.png)

<br>

### How to establish a secure connection
![](cs-note-img/Pastedimage20220512091200.png)
![](cs-note-img/AB6B3D4112E947F696C2FBCFDF8869B7.jpg)


----

# Artificial Intelligence (AI)
[Please check the note released before🔗](https://hugo-blog-fawn.vercel.app/p/chapter-22-artificial-intelligence-ai/)


----

# Computational thinking and problem-solving
## Algorithms
[Please check the note released before🔗](https://hugo-blog-fawn.vercel.app/p/chapter-23-algorithms/)


## Recursion
![](cs-note-img/Pastedimage20220512103904.png)
![](cs-note-img/Pastedimage20220512103946.png)
<br>

### Description
- have a base case
- have a general case
- reach the base case aft er a finite (limited) number of calls to itself.
### Benefits
- More elegant
- Use less program code than iterative solutions
### Drawbacks
- Large amounts of memory usage and processor time

### How to implement recursion (<mark style="background: #FFF3A3A6;">Stack</mark>)
- Each time a subroutine is called, a stack frame is pushed onto the stack.
- A stack frame consists of the return address and the values of the local variables.
- When a subroutine completes, the corresponding stack frame is popped off the stack.


----

# Further Programming
## Programming Paradigms
- A programming style/classification
// characteristics/features that programming language has/uses

### Low-level Programming
- Programs use the instruction set of a processor

#### Addressing mode
- immediate
- direct
- indirect
- indexe
- relative


### Imperative Programming (<mark style="background: #FFF3A3A6;">Sequence of commands</mark>)

![](cs-note-img/Pastedimage20220512110107.png)

### Object Oriented Programming

![](cs-note-img/Pastedimage20220512110120.png)
![](cs-note-img/OOPfeaturs.png)
![](cs-note-img/09002AFA2D795A865B9F000C646C0E9B.jpg)

<br>

### Declarative Programming (<mark style="background: #FFF3A3A6;">Focus on the result</mark>)
- The programmer doesn’t tell the computer what to do. To get information, the programmer poses a query (sets a goal). It’s up to the logic programming system to work out how to get the answer.
- Declarative programming languages include SQL and Prolog.

## File Processing and Exception Handling
### Record
#### Pseudocode

```Pseudocode
TYPE CarRecord
    DECLARE VehicleID : STRING // unique identifier and record key
    DECLARE Registration : STRING
    DECLARE DateOfRegistration : DATE
    DECLARE EngineSize : INTEGER
    DECLARE PurchasePrice : CURRENCY
ENDTYPE

DECLARE Car : ARRAY[1:100] OF CarRecord // store the details of 100 cars

```


#### Python3
```Python
class CarRecord:              # declaring a class without other methods
    def __init__(self):       # constructor
        self.VehicleID = ""
        self.Registration = ""
        self.DateOfRegistration = None
        self.EngineSize = 0
        self.PurchasePrice = 0.00

ThisCar = CarRecord()         # instantiates a car record
ThisCar.EngineSize = 2500     # assign a value to a field
Car = [CarRecord() for i in range(100)] # make a list of 100 car records
Car[1].EngineSize = 2500 # assign value to a field of the 2nd car in list
```

### File processing
#### Psedocode
|Structured English|Pseudocode|
|:----|:----|
|Create a file and open it for writing|OPENFILE \<filename> FOR WRITE|
|Open a file in append mode|OPENFILE \<filename> FOR APPEND|
|Open a file for reading|OPENFILE \<filename> FOR READ|
|Open a file for random access|OPENFILE \<filename> FOR RANDOM|
|Close a file|CLOSEFILE \<filename>|
|Write a record to a file|PUTRECORD \<filename>, \<identifier>|
|Read a record from a file|GETRECORD \<filename>, \<identifier>|
|Move to a specific disk address within the file|SEEK \<filename>, \<address>|
|Test for end of file|EOF(\<filename>)|

### Python3
```Python3
file = open("filename",mode=?)   //create a file object
```
#### Recommanded mode parameter
- `'w'` for write
- `'r'` for read
- `'a'` for append
- `'+'` let the file can be read and write at the same time
    - If the mode is `'w'`, you cannot use `file.read([size])`,`file.readline([size])` and `file.readlines([sizeint])`
    - If the mode is `'w+'`, there is no worry of reading the file
- `'b'` for open/write/append a binary file
     - for example: `'wb'`, `'wb+'`

<br>

#### Detail mode parameters
<table class="reference">
<tbody><tr><th style="width:10%">模式</th><th>描述</th></tr>
<tr><td>t</td><td>文本模式 (默认)。</td></tr>
<tr><td>x</td><td>写模式，新建一个文件，如果该文件已存在则会报错。</td></tr>
<tr><td>b</td><td>二进制模式。</td></tr>
<tr><td>+</td><td>打开一个文件进行更新(可读可写)。</td></tr>
<tr><td>r</td><td>以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。</td></tr>
<tr><td>rb</td><td>以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。一般用于非文本文件如图片等。</td></tr>
<tr><td>r+</td><td>打开一个文件用于读写。文件指针将会放在文件的开头。</td></tr>
<tr><td>rb+</td><td>以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。一般用于非文本文件如图片等。</td></tr>
<tr><td>w</td><td>打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。</td></tr>
<tr><td>wb</td><td>以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。</td></tr>
<tr><td>w+</td><td>打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。</td></tr> 
<tr><td>wb+</td><td>以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。</td></tr>
<tr><td>a</td><td>打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。</td></tr> 
<tr><td>ab</td><td>以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。</td></tr> 
<tr><td>a+</td><td>打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。</td></tr> 
<tr><td>ab+</td><td>以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。</td></tr>
</tbody></table>



<br>

#### Some file fuctions
<table class="reference">
<tbody><tr>
<th style="width:5%">序号</th><th>方法及描述</th></tr>
<tr><td>1</td><td><p><a href="https://www.runoob.com/python3/python3-file-close.html">file.close()</a></p><p>关闭文件。关闭后文件不能再进行读写操作。</p></td></tr>
<tr><td>6</td><td><p><a href="https://www.runoob.com/python3/python3-file-read.html">file.read([size])</a></p><p>从文件读取指定的字节数，如果未给定或为负则读取所有。</p></td></tr>
<tr><td>7</td><td><p><a href="https://www.runoob.com/python3/python3-file-readline.html">file.readline([size])</a></p><p>读取整行，包括 "\n" 字符。</p></td></tr>
<tr><td>8</td><td><p><a href="https://www.runoob.com/python3/python3-file-readlines.html">file.readlines([sizeint])</a></p><p>读取所有行并返回列表，若给定sizeint&gt;0，返回总和大约为sizeint字节的行, 实际读取值可能比 sizeint 较大, 因为需要填充缓冲区。</p></td></tr>
<tr><td>9</td><td><p><a href="https://www.runoob.com/python3/python3-file-seek.html">file.seek(offset[, whence])</a></p><p>移动文件读取指针到指定位置</p></td></tr>
<tr><td>10</td><td><p><a href="https://www.runoob.com/python3/python3-file-tell.html">file.tell()</a></p><p>返回文件当前位置。</p></td></tr>
<tr><td>11</td><td><p><a href="https://www.runoob.com/python3/python3-file-truncate.html">file.truncate([size])</a></p><p>从文件的首行首字符开始截断，截断文件为 size
 个字符，无 size 表示从当前位置截断；截断之后后面的所有字符被删除，其中 windows 系统下的换行代表2个字符大小。 </p></td></tr>
<tr><td>12</td><td><p><a href="https://www.runoob.com/python3/python3-file-write.html">file.write(str)</a></p><p>将字符串写入文件，返回的是写入的字符长度。</p></td></tr>
<tr><td>13</td><td><p><a href="https://www.runoob.com/python3/python3-file-writelines.html">file.writelines(sequence)</a></p><p>向文件写入一个序列字符串列表，如果需要换行则要自己加入每行的换行符。</p></td></tr>
</tbody></table>

<br>

### Exception
![](cs-note-img/Pastedimage20220512135315.png)
![](cs-note-img/Pastedimage20220512135502.png)
![](cs-note-img/Pastedimage20220512135622.png)
<br>

#### Code language
##### Pseudocode
```Pseudocode
TRY
    <statementsA>
EXCEPT
    <statementsB>
ENDTRY
```

```Pseudocode
# With FINALLY
TRY
    <statementsA>
EXCEPT
    <statementsB>
FINALLY
    <statementsC>
ENDTRY
```
- TRY
- EXCEPT
- FINALLY - The statements (`<statementsC>`) in this block will be executed regardless of whether there was an exception or not.


##### Python3
```Python
# Basic try and exception examples
file = open("test.txt",mode='r')


try:
    file.readlines()
except EOFError:
    print("reach the end of file")
    file.close()
```

```Python
try:
    file = open("test.txt",mode='w')
    file.write("line 1")
    file.close()
except IOError:
    print("cannot find the file")
```

```Python
try:  
    runoob()  
except AssertionError as error:  
    print(error)  
else:  
    try:  
        with open('file.log') as file:  
            read_data = file.read()  
    except FileNotFoundError as fnf_error:  
        print(fnf_error)  
finally:  
    print('这句话，无论异常是否发生都会执行')
```

```Python
import sys  

try:  
    f = open('myfile.txt')  
    s = f.readline()  
    i = int(s.strip())  
except OSError as err:  
    print("OS error: {0}".format(err))  
except ValueError:  
    print("Could not convert data to an integer.")  
except:  
    print("Unexpected error:", sys.exc_info()[0])
```
- More info
[Python3 错误和异常 | 菜鸟教程 (runoob.com)🔗](https://www.runoob.com/python3/python3-errors-execptions.html)