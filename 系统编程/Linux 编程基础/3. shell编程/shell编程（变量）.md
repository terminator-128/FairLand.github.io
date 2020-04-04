# Shell编程——变量

Shell编程即Shell脚本编程，其本质是利用Shell功能编写程序。这个程序实质上是一个纯文本文件。

[TOC]

---



## 一、第一个Shell程序

Shell脚本有一套相对完善的语法规则，包括变量、数组的定义与使用、函数的构造以及流程控制等。下面通过一个简单的Shell程序来认识Shell脚本编程。

- 创建first文件

```Linux
# vi first
```

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/ShellProgramming.png" style="zoom:48%;" />

- 执行脚本文件

  - 将脚本本身所谓一个可执行文件

    - 提升文件权限

      ```shell
      chmod +x first
      ```

    - 将文件当作可执行程序执行

      ```shell 
      ./first
      ```

  - 将脚本文件作为一个参数，传递给Shell解释器进行解析。

    ```shell
    sh first
    ```

- 输出结果到终端

  ```shell
  data is:
  first Shell script
  ```

---



## 二、Shell中的变量

变量的讲解分为变量的定义、引用、分类以及运算方法。

### 1. 变量的定义

​	Shell中的变量在使用之前无需定义，可以在使用的时候创建。不同于C语言等高级语言中的变量，Shell中的变量没有细致的分类。一般情况下，Shell中的变量保存一个串。Shell不关心这个串的含义，只需在需要时，才会使用一些工具程序转换为明确的类型。

​	Shell变量的变量名由字母、数字和下画线组成，开头只能是字母或下画线。

```Linux
变量名=值
```

- 若变量名中出现其他字符，则表示变量名到此前为止。
- 给变量赋值时，等号两边不能有空格。
- 若要给变量赋值，可在等号后跟一个换行符，即缺省以上格式中“值”的部分；若字符串中包含空格，则必须将值放在引号（单引号/双引号）中。

Shell中可以使用readonly将某个变量设置为制度变量，使用方法如下：

```shell
readonly 变量名
```

此时若要重新为变量var赋值，则会提示bash:name:readonly: variable。

---

### 2. 变量的引用

Shell中使用$符号来引用变量，若要输出上文定义的变量，可以使用以下方式：

```shell
echo $var
```

在定义时，使用双引号或单引号来标注变量皆可，但是在引用时，其效果略有差异。

在Shell脚本中定义变量并进行引用。

```shell
1	#!/bin/sh
2	var="hello itheima"
3	echo $var
4	echo "$var"
5	echo '$var'
6	exit 0
```

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/out_var_shell.jpg" style="zoom:80%;" />

- 若由双引号引起来的字符串有变量的引用，则会输出变量中储存的值。
- 若由单引号引起来的字符串中有变量的引用，则会原样输出。

下表为Shell中变量常见的引用：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/Shell_var_interface.jpg" style="zoom:80%;" />

---

### 3. 变量的输入

​	Shell脚本中通过echo关键字打印变量，通过read关键字读取变量。当脚本需要从命令行读取数据时，只需在其中添加如下的read语句即可：

```shell
read 变量名
```

​	当脚本执行到该语句时，终端会等待用户输入，用户输入的信息将被保存到read之后的变量中。

---

### 4. 变量的分类

​	在之前的案例中，出现的变量称为局部变量或本地变量，这些变量定义在脚本中只在脚本中生效。

​	除此之外，Shell还有一些独特的变量，包括环境变量、位置变量、标准变量和特殊变量。

#### （1）环境变量

- 环境变量又称为永久变量，与局部变量相对。用于创建该变量的Shell和从该Shell派生的子Shell或进程中。

- 为了区别于局部变量，环境变量中的字母全部大写。

- 因为在系统启动时Shell自动登录，所以Shell中执行的用户进程均为子进程（紫禁城:clown_face:）环境变量可用于所有用户进程。

- 环境变量使用export设定或定义。

  [^]: 若要讲一个已经存在的本地变量修改为环境变量，可以使用以下方法：

  ```shell
  export 变量名
  ```

  若要定义一个环境变量：

  ```shell
  export 变量名=值
  ```

#### （2）位置变量

​	位置变量即执行脚本时传入脚本中对ing脚本位置的变量。

<!--类似函数的参数，引用方法为$符号加上参数的位置，如$加上参数的位置，如$0、$1、$2···。其中 $0比较特殊，表示脚本的名称，其余的表示脚本的第一个参数、第二个参数···。-->

假设当前有一个名为loca的脚本，其中的内容如下：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_location_var.jpg" style="zoom:80%;" />

执行脚本时使用的命令与输出结果如下：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/location_var_runtime.jpg" style="zoom:80%;" />

使用shift 可以移动位置变量对应的参数，shift每执行一次，参数序列左移一个位置。移除的参数不可再用。

假如代码:paw_prints:如下：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_use_of_shift.jpg" style="zoom:80%;" />

则其运行结果为:grey_question: ：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_use_shift_runtime.jpg" style="zoom:80%;" />



#### （3）标准变量

​	标准变量也是环境变量，在bash环境建立时形成。该变量自动解析，通过查看/etc目录下的profile文件可以查看系统中的标准环境变量。

<!--可以使用`env`命令查看系统中的环境变量，包括环境变量和标准变量。-->

#### （4）特殊变量

​	Shell中还有一些特殊的变量，这些变量及其含义分别如下：

- \#	传递到脚本或函数的参数数量
- ?     前一个命令执行情况，0表示成功，其他值表示失败。
- $     运行当前脚本的当前进程id号
- ！    运行脚本的最后一个命令
- \*      传递给脚本或函数的全部参数  

[^例如]: 查看传递到脚本的参数数量：

```shell
echo $#
```

---

### 5. 变量的运算

Shell中的变量没有明确的类型，变量值都以字符串的形式存储，但Shell中也可能进行一些算术运算。那么Shell中的算术运算是如何实现的呢？Shell中的运算一般通过两个命令实现：let和expr。

#### （1）let

​	let命令可以进行算术运算和数值表达式。使用let的格式如下：

```shell
let expression
```

命令行中的运算可以直接套用以上格式实现。下面通过实例来展示let在脚本中的使用方法。

假设现有一个名为file的文件，其内容如下：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/Shell_let_command_use.jpg" style="zoom:80%;" />

该脚本的运行结果为：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/Shell_let_command_use_runtime.jpg" style="zoom:80%;" />

let命令也可以用如下形式代替：

```Linux
let i+=3  等价于  ((i+=3))
```

#### （2）expr

​	expr命令用于对整形变量进行算术运算。使用expr命令时可以使两个数值直接进行运算，例如进行加法运算3+5，我们可以在命令行中输入以下命令：

```shell
$ expr 3+5
8
```

<!--需要注意的是：-->

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/Shell_expr_use.png" style="zoom: 33%;float:left" />

以下是使用expr的实例：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/Shell_expr_use_runtime.png" style="zoom: 33%;float:left" />