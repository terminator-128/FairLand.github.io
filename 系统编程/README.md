# 乾坤大挪移之Linux系统编程

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/codeRain.gif" alt="codeRain" style="zoom:80%;" />

## :alarm_clock:用户权限与SHELL编程——March 8,2020

### 一、Linux系统的用户与权限

​	在Linux中一切都是文件，由于所有的配置文件都是文本，所以你只需要一个最简单的Editor就可以修改。由于修改文本文件的简单性，而Linux必须保证安全性。如是设计出用户（组）和权限这两个概念，既保障了安全性又没有添加复杂性。

​	**Unix一切皆为文件，且支持多用户。**每个用户都是使用文件（输入命令就是使用可执行文件）来使用计算机系统的，因此需要控制不同用户对计算机里的不同文件具有不同的权限（read\write\execute）。

​	Linux引入了三个文件来管理用户（组）：

1. /etc/passwd	存放用户信息。:first_quarter_moon_with_face:
2. /etc/shadow    存放用户密码信息。:first_quarter_moon:
3. /etc/group        存放组信息。:full_moon:

然后，在文件系统中的每个文件的开头添加了用户（组）和文件之间的权限信息。

### 二、Linux中的进程

​	简单来说，**进程就是运行起来的程序。**把磁盘上的可执行文件加载到内存，并创建相应的管理数据结构，然后这个执行文件的过程创造一个进程。

​	**输入一条命令，通常Shell就会创建一个进程来运行这条命令所代表的可执行文件。**也就是说，这个可执行文件加载到内存并变成了一个进程。

可通过以下指令来查看执行的命令的实质:

```lua
type [命令]
```

###### #:clown_face:虽然进程这个概念好像之前并不清楚具体是什么，其实我们早就接触过（例如Window任务管理器下的一系列条目就是一系列进程）。

:dango:**进程是Linux系统的核心概念。**

### 三、管道与重定位:baguette_bread:

​	进程是用来处理数据、处理文件的，那么不可避免地与其他程序交换数据，也可能从文件里获取:minidisc:数据或者将处理好的数据输出到文件中。

​	**管道就是用来解决进程之间交换数据的问题。**

​	顾名思义，一个进程将处理好的数据放到管道里，数据顺着管道流向另一端连接的进程，另一端的进程就获取了数据。要注意的是管道是半双工的，同一时间只能从一端流向另一端。

​	而**重定位则解决了进程从哪里读数据以及处理好的数据输出到哪里的问题**。一般默认的读入的标准设备是键盘，输出的标准设备是显示器，因为**Linux中万物皆是文件，其实这些设备也是文件，我们重定位就是将这些设备文件替换成别的文件。**

### Linux Shell编程

- **Shell其实就是个命令解释器:apple: ，Shell将用户程序及其输入翻译成操作系统内核能识别的指令，并且操作系统内核执行完将返回的输出通过Shell再现给用户。**

- **SHELL 也是一门编程语言，即SHELL脚本，SHELL是解释执行的脚本语言，可直接调用Linux命令。**通过编写SHELL脚本，可以将一些经常要是用的命令*文件化*、*自动化*。这样就不用了每次手动输入命令，费时费力。

Plus 有关/proc文件系统:egg:推荐两篇 blog

- https://blog.csdn.net/juzihongle1/article/details/77184541?tdsourcetag=s_pctim_aiomsg
- https://blog.csdn.net/goldlevi/article/details/7705178?tdsourcetag=s_pctim_ai

## :alarm_clock:PreLearning

开始记一些有关系统编程的笔记。基础的大概在总结中都有，此文档相当于一个日志性质的文件，借以往昔思来者 :full_moon_with_face:借此来勉励自己吧。

来记一下之前的概要：

### 什么是软件系统？

   <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/ExampleSoftwareSys.jpg" alt="ExampleOfSoftwareSystem" style="zoom:80%;" />

   A platform, application, or other structure that:

   - 由多个module建构:
     - sys's architecture defines the interfaces of and relationships between the modules.

   - 通常构成复杂:
     - in terms of its implementation, performance, management...
   - hopefully :clown_face:meets some requirements...
     - Performance.
     - Security.
     - Fault tolerance.
     - Data consistency.

   

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/ViewOfSys.png" alt="ViewOfsystem" style="zoom:80%;" />

### 软件栈和软件的分层结构

1. #### **软件的栈结构**

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SoftwareStack.png" alt="SoftwareStack" style="zoom:50%;float=left" />

2. #### **系统的分层**

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SystemLayers.png" alt="SystemLayers" style="zoom:67%;" />

3. #### **操作系统的抽象**

   **artificial：**

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/importanceOfOS.png" alt="importanceOfOS" style="zoom:67%;" />

​	**real:**

​	<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/abstractOfOS.png" alt="abstractOfOS" style="zoom: 50%;" />

3. #### **进程（线程）的抽象——对CPU的抽象**

   <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/abstractOfCPU.png" alt="abstractOfCPU" style="zoom:80%;" />

4. #### **Files文件——对外存和外设的抽象**

5. #### **虚拟内存——对物理内存和外存的抽象**

   <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/abstractOfVirtualMemory.png" alt="abstractOfVirtualMemory" style="zoom:67%;" />

   ps: 详情见计组相关知识。

6. ### **Linux组织结构**

   <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/Linux组织结构.png" alt="Linux组织结构" style="zoom: 80%;" />