# 乾坤大挪移之Linux系统编程

![codeRain](..\pictures\codeRain.gif)

## :alarm_clock:PreLearning

开始记一些有关系统编程的笔记。基础的大概在总结中都有，此文档相当于一个日志性质的文件，借以往昔思来者 :full_moon_with_face:借此来勉励自己吧。

来记一下之前的概要：

### 什么是软件系统？

   <img src="..\pictures\ExampleSoftwareSys.jpg" alt="ExampleOfSoftwareSystem" style="zoom:80%;" />

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

   

<img src="..\pictures\ViewOfSys.png" alt="ViewOfsystem" style="zoom:80%;" />

### 软件栈和软件的分层结构

1. #### **软件的栈结构**

<img src="..\pictures\SoftwareStack.png" alt="SoftwareStack" style="zoom:50%;float=left" />

2. #### **系统的分层**

<img src="..\pictures\SystemLayers.png" alt="SystemLayers" style="zoom:67%;" />

3. #### **操作系统的抽象**

   **artificial：**

<img src="..\pictures\importanceOfOS.png" alt="importanceOfOS" style="zoom:67%;" />

​	**real:**

​	<img src="..\pictures\abstractOfOS.png" alt="abstractOfOS" style="zoom: 50%;" />

3. #### **进程（线程）的抽象——对CPU的抽象**

   ![abstractOfCPU](..\pictures\abstractOfCPU.png)

4. #### **Files文件——对外存和外设的抽象**

5. #### **虚拟内存——对物理内存和外存的抽象**

   <img src="..\pictures\abstractOfVirtualMemory.png" alt="abstractOfVirtualMemory" style="zoom:67%;" />

   ps: 详情见计组相关知识。

6. ### **Linux组织结构**

   ![Linux组织结构](..\pictures\Linux组织结构.png)