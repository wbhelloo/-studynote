---
title: 简明Python教程-标准库
lang: zh-cn
categories: 简明Python教程
tags: Python简明教程学习笔记
abbrlink: d645c4f
date: 2018-07-25 11:00:37
keywords:
---

### 标准库

Python 标准库（Python Standrad Library）中包含了大量常用的模块，也是标准Python 安装包中的一部分。熟悉 Python 标准库十分重要，因为只要你熟知这些库可以做什么事，才能熟练的利用这些库解决问题。

我们将探索标准库中的一些常用模块，你可以在 Python 安装包中附带的文档中的“库概览（**Library Reference**）” 中查找到所有模块的全部细节。<!--more-->

下面我们来了解一些常用的模块。

> 注意：如果你觉得本章内容过于超前，你可以先跳过本章。不过，我强烈建议你在适应利用 Python 进行编程后再来看看本章。

### SYS模块

sys 模块包括了一些针对特定系统的功能，我们已经了解过 `sys.argv `列表中包括了命令行参数。

假如，我们需要查看正在使用 Python 的软件版本， sys 模块会给我们相关的信息。

```python
>>> import sys
>>> sys.version_info
sys.version_info(major=3, minor=5, micro=1, releaselevel='final', serial=0)
>>> sys.version_info.major == 3
True
```

#### *它是如何工作的?*

> sys 模块包含一个 `version_info` 元组，它可以提供版本信息。第一个条目是主版本信息，我们可以调出这些信息并使用它。

### 日志模块

如果你想将一些调试（`Debugging`）信息或一些重要的信息储存在某个地方，以便你可以检查你的程序是否如你所期望那般运行，应该怎么做？你该如何将这些信息“储存在某个地方”？这可以通过 logging 模块来实现。

#### 例子：

（保存为` stdlib_logging.py`）

```python
import os
import platform
import logging
if platform.platform().startswith('Windows'):
	logging_file = os.path.join(os.getenv('HOMEDRIVE'),
							  os.getenv('HOMEPATH'),
							  'test.log')
else:
logging_file = os.path.join(os.getenv('HOME'),
						  'test.log')

print("Logging to", logging_file)

logging.basicConfig(
    level=logging.DEBUG,
    format='%(asctime)s : %(levelname)s : %(message)s',
    filename=logging_file,
    filemode='w',
)

logging.debug("Start of the program")
logging.info("Doing something")
logging.warning("Dying now")
```

#### 输出：

```python
2018-07-25 11:13:23,104 : DEBUG : Start of the program
2018-07-25 11:13:23,104 : INFO : Doing something
2018-07-25 11:13:23,105 : WARNING : Dying now
```

如果你不能运行` cat` 命令，你可以通过一款文本编辑器打开 `test.log` 文件。

#### *它是如何工作的?*

> 我们使用了三款标准库中的模块—— `os `模块用以**和操作系统交互**，` platform `模块用以**获取平台——操作系统——的信息**， `logging `模块用来**记录（Log）信息**。
>
> 首先，我们通过检查 `platform.platform()` 返回的字符串来确认我们正在使用的操作系统（有关更多信息，请参阅` import platform`; `help(platform`) ）。如果它是 Windows，我们将找出其主驱动器（`Home Drive`），主文件夹（`Home Folder`）以及我们希望存储信息的文件名。将这三个部分汇聚到一起，我们得到了有关文件的全部位置信息。对于其它平台而言，我们需要知道的只是用户的主文件夹位置，这样我们就可获得文件的全部位置信息。
>
> 我们使用 `os.path.join() `函数来将这三部分位置信息聚合到一起。使用这一特殊函数，而非仅仅将这几段字符串拼凑在一起的原因是，这个函数会确保完整的位置路径符合当前操作系统的预期格式。
>
> 然后我们配置 logging 模块，让它以特定的格式将所有信息写入我们指定的文件。
>
> 最后，无论这些信息是用以调试，提醒，警告甚至是其它关键的消息，我们都可以将其聚合并记录。一旦程序开始运行，我们可以检查这一文件，从而我们能知道程序运行过程中究竟发生了什么，哪怕在用户运行时什么信息都没有显示。

### 每周模块系列

标准库中还有许多模块值得学习，例如一些用以调试（`Debugging`）的模块， 处理命令行选项的模块，正则表达式（`Regular Expressions`）模块 等等，等等。
进一步探索标准库的最好方法是阅读由 **Doug Hellmann** 撰写的优秀的 **Python Module of theWeek** 系列（你还可以阅读它的实体书或是阅读 Python 官方文档）。

### 总结

我们已经探索了 Python 标准库中提供的诸多的模块的一些功能。在此强烈建议你浏览Python 标准库文档来了解所有可以使用的模块。
接下来，我们将介绍 Python 的其它各个方面，让我们继续学习吧。

