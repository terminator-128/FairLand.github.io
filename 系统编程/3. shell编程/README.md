# SHELL

shell:shell:既是一种命令语言，又是一种程序设计:computer:语言（即Shell脚本）。

- 作为一种基于命令的语言，Shell交互式地解释和执行用户输入的命令。
- 作为程序设计语言，Shell中可以定义各种变量，传递参数，并提供许多高级语言所具有的流程控制结构。

Shell虽然不是Linux系统内核的一部分，但它调用了系统内可得大部分功能来执行程序、创建文档并以并行的方式协调各个程序的运行。本章将学习Shell的相関概念以及Shell编程相关的知识。

[TOC]



## Shell概述

Shell的愿意为"壳"（:shell: ），它包裹在内核之外，处于用户与内核之间。其主要功能为接收用户 :information_desk_person: 输入的命令，找到命令所在位置 :triangular_flag_on_post: ，并加以执行。

<img src="..\..\pictures\ShellKernalUser.png" style="zoom: 50%;" />

在计算机科学 :computer: 中，可以认为Shell是包裹在内核外的命令接口 ，又因为其最重要的功能是命令解释，所以也可以认为Shell是一个命令解释器。

---

### Shell的分类

Shell的种类很多常见的有BSh、CSh、KSh、bash等。下标简单的说明了常见的Shell。

<img src="..\..\pictures\ShellKind.png" style="zoom:48%;" />

用户可通过`ls /bin/*sh` 查看系统中安装的shell。

---

### Shell的功能

Shell最重要的功能是命令解释。