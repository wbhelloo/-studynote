---
title: 简明Python教程-安装
categories: 简明Python教程
tags: Python简明教程学习笔记
date: 2018-07-02 16:56:06
keywords:
description:
---

### 简明 Python 教程

> 《A Byte of Python》（简明 Python 教程）是一本由 Swaroop C H 编写，旨在于介绍如何使用 Python 语言进行编程的自由图书。

> 你可以通过[http://python.swaroopch.com/](http://python.swaroopch.com/) 在线阅读本书英文原版。
>
> 中文译版可通过 [https://bop.mol.uno](https://bop.mol.uno) 在线阅读。

#### 关于 Python

官方对 Python 的介绍如下：<!-- more -->

> Python 是一款易于学习且功能强大的编程语言。 它具有高效率的数据结构，能够简单又有效地实现面向对象编程。Python 简洁的语法与动态输入之特性，加之其解释性语言的本质，使得它成为一种在多种领域与绝大多数平台都能进行脚本编写与应用快速开发工作的理想语言。

##### 名字背后的故事

Python 的创造者吉多·范罗苏姆（Guido van Rossum）采用 BBC 电视节目《蒙提·派森的飞行马戏团（Monty Python's Flying Circus，一译巨蟒剧团）》的名字来为这门编程语言命名。尽管他本人并不特别喜欢蟒蛇这种通过在猎物身边卷曲自己的身体以此来碾碎猎物身体来进食的动物。

##### Python 的特色

简单、易于学习、自由且开放、高级语言、跨平台性、解释性、面向对象、可扩展性、可扩展性、可扩展性。

#### 安装

本书中提及“**Python 3**”时，我们指的是任何大于等于 3.5.1 的 Python 发行版。

##### 在 Windows 中安装

访问 https://www.python.org/downloads/ 并下载最新版本的 **Python**。在本书撰写的时点，最新版本为 **Python 3.5.1**。 其安装过程与其它 Windows 平台的软件的安装过程无异。
**注意：**请务必确认你勾选了 ***Add Python 3.5 to PATH*** 选项。

##### 在 Windows 下运行 Python 命令提示符

对于 Windows 用户来说，如果你已经正确并恰当地设置了 **PATH环境 变量**，你可以在命令行中运行解释程序。
要想在 Windows 中运行终端，点击开始并点击 运行 。在对话中输入 `cmd` 并按下回车键。然后，输入 `python` 以确保其没有任何错误。

#### 第一步

接下来我们将看见如何在 Python 中运行一个传统的“Hello World”程序。

##### 使用解释器提示符

在你的操作系统中打开终端（Terminal）程序，然后通过输入 `python` 并按下` [enter] `键来打开 Python 提示符（Python Prompt）。

当你启动 Python 后，你会看见在你能开始输入内容的地方出现了 `>>>` 。这个被称作Python解释器提示符（Python Interpreter Prompt） 。

在 Python 解释器提示符，输入：

```
>>> print("Hello World")
```

在输入完成后按下 `[enter]` 键。你将会看到屏幕上打印出 `Hello World` 字样。

##### 如何退出解释器提示符

如果你使用的是 Windows 命令提示符，可以按下 `[ctrl + z]`组合键并敲击 `[enter]` 键来退出。

#### 选择一款编辑器

当我们希望运行某些程序时，总不能每次都在解释器提示符中输入我们的程序。因此我们需要将它们保存为文件，从而我们便可以多次地运行这些程序。

要想创建我们的 Python 源代码文件，我们需要一款能够让你输入并保存代码的编辑器软件。一款优秀的面向程序员的编辑器能够帮助你的编写源代码文件工作变得轻松得多,故而选择一款编辑器确实至关重要。

如果你对应从哪开始还没有概念，我推荐你使用 **PyCharm** 教育版 软件，它在 Windows、Mac OS X、GNU/Linux 上都可以运行。

##### PyCharm

PyCharm 教育版是一款能够对你编写 Python 程序的工作有所帮助的免费编辑器。

创建一个新的文件时，在 **项目** 上右击并选择 ` -> New -> Python File `

运行程序时，`右键-> Run '你的文件名'`。