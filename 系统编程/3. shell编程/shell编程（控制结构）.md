# Shell编程——控制语句

[TOC]

---



## 一、Shell中的条件语句

条件语句是程序中不可或缺的组成部分，程序中往往需要先对某些条件进行判断，在根据判断的结果采取不同的方案。Shell中也有条件语句，常用的条件语句为：if语句、Select语句和case语句。

### 1. 条件判断

​	在学习Shell中的条件语句之前，需要先掌握Shell条件判断语句的书写方法。

​	条件判断是条件语句的核心，Shell中通常使用test命令或[命令对条件进行判断，判断的内容可以是变量或文件。

<!--前文提到，每个脚本程序的末尾最好加上exit命令，以便提供该脚本返回值给其他脚本程序，而这些退出码往往应用于条件判断中。-->

#### (1) test and [

###### （1）test命令的语法格式

```shell
test [-option] args
```

假设要检测某个文件是否存在，可以使用如下语句进行判断：

```shell
if test -f file
then
	:
fi
```

###### （2）[ 命令的语法格式

```shell
test -f file 等价于 [ -f file ]
```

```shell
if [ -f file ]
then
	:
fi
```

> 需要注意的是，[ 命令也是命令，命令与选项及参数之间应有空格。因此在[ ]符号与[ ]符号中的检查条件之间需要留出空格，否则会产生错误。

上述代码也可写作也可写作：

```shell
if [ -f file ]; then
:
fi
```

#### (2) 条件判断语句分类

Shell中的条件判断语句通常可以分为三类：字符串比较、算数比较和针对文件的条件测试。

###### 1. 字符串比较

字符串比较中常用的判断条件如下表：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/condition_judge_script.png" style="zoom:80%;" />

###### 2. 算数比较

算数比较中比较的内容一般为整数，常用的判断条件如下表：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/condition_judge_script_number.png" style="zoom:80%;" />

###### 3. 文件测试

文件测试中通常是针对文件的属性做出判断，常用的判断条件如下表所示：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/condition_judge_script_file.png" style="zoom:80%;" />

---

### 2. if 条件语句

Shell中的if条件语句分为：单分支if语句、双分支if语句和多分支if语句。

##### （1）单分支 if 语句

```shell
if [条件判断语句]; then
	:
fi
```

##### （2）双分支 if 语句

```shell
if [条件判断语句]; then
	:
else
	:
fi
```

##### （3）多分支 if 语句

```shell
if [条件判断语句]; then
	:
elif [条件判断语句]; then
	:
else
	:
fi
```

---

### 3. select 语句

select 语句格式如下：

```shell
select 变量 in 列表
do
	:
	[break]
done
```

<!--Shell中select语句可以将选项列表做出类似目录的形式，以交互的形式选择列表中的数据，传入select语句中的主体部分加以执行。-->

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_select_script_use.jpg" style="zoom:80%;" />

运行中：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_select_script_use_runtime.jpg" style="zoom:80%;" />

输入3，回车。

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_select_script_use_runtime2.jpg" style="zoom:80%;" />

---

### 4. case 语句

​	case语句可以将一个变量的内容与多个选项进行匹配，若匹配成功，则执行该条件下对应的语句。

case语句的格式如下：

```shell
case var in
	选项 1)···;;
	选项 2)···;;
	:
	* )···
esac
exit 0
```

例：实现四则运算：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_script_fournumber_calculate.jpg" style="zoom:80%;" />

运行结果:

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_script_fournumber_calculate_runtime.jpg" style="zoom:80%;" />

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/case_another_shell.png" style="zoom: 60%;float:left" />

---



## 二、Shell中的循环语句

循环式编程语言中不可或缺的重要部分，可以将重复运算凝聚在简短程序中，大大减少代码量。

Shell脚本中常用的循环有for循环、while循环和until循环。:film_strip:

---

### 1. for 循环

for循环的格式如下：

```shell
for 变量 in 变量列表
do
	:
done
```

> 其中变量是当前循环中使用的一个对象，用来接受变量列表中的一个元素；变量列表是整个循环要操作的对象的集合，可以是字符串集合或文件名、参数等，变量列表的值会被逐个赋给变量。

<!--每个变量可以用引号单独引起来，但是不能将整个列表置于一对引号中，因为一对引号引起来的值会被视为一个变量-->

---

### 3. while 循环

while循环的格式如下：

```shell
while [ 表达式 ]
do
	:
done
```

>  非语法格式中的中括号不能省略。

例：用while计算整数1~100的和。

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_while_script .jpg" style="zoom:80%;" />

运行结果：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/shell_while_script_runtime.jpg" style="zoom:80%;" />

---

### 4. until 循环

until 循环的格式如下：

```shell
until [ 表达式 ]
do
	…
done
```

> until 循环与 while循环的格式基本相同，不同的是，当until 循环为假的时候才能继续执行循环的命令。

---