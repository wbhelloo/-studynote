---
title: 简明Python教程-模块
categories: 简明Python教程
tags: Python简明教程学习笔记
date: 2018-07-12 16:31:54
keywords:
---

### 模块

一个模块可以被其它程序导入并运用其功能（函数）。

编写模块有很多种方法，其中最简单的一种便是创建一个包含**函数**与**变量**、以 `.py `为后缀的文件。

另一种方法是使用撰写 Python 解释器本身的本地语言来编写模块。举例来说，你可以使用 C语言来撰写 Python 模块，并且在编译后，你可以通过标准 Python 解释器在你的 Python 代码中使用它们。

我们在使用 Python 标准库的功能时也同样如此。首先，我们要了解如何使用标准库模块。

<!--more-->

#### 例子:

保存为` module_using_sys.py` ，并在Command Line Arguments内输入参数`We are arguments`。

```python
import sys

print('The command line arguments are:')
for i in sys.argv:
	print(i)
    
print('\n\nThe PYTHONPATH is', sys.path, '\n')
```

#### 输出：

```python
The command line arguments are:
E:/PyCharm/Python36/LearnPython/module_using_sys.py
we
are
arguments

The PYTHONPATH is ['E:/PyCharm/Python36/LearnPython', 'D:\\Program Files\\JetBrains\\PyCharm 2018.1.2\\helpers\\pydev', 'E:\\PyCharm\\Python36', 'D:\\Program Files\\JetBrains\\PyCharm 2018.1.2\\helpers\\pydev', 'D:\\Program Files (x86)\\Python\\Python36venv\\Scripts\\python36.zip', 'D:\\Program Files (x86)\\Python\\Python36\\DLLs', 'D:\\Program Files (x86)\\Python\\Python36\\lib', 'D:\\Program Files (x86)\\Python\\Python36', 'D:\\Program Files (x86)\\Python\\Python36venv', 'D:\\Program Files (x86)\\Python\\Python36venv\\lib\\site-packages', 'D:\\Program Files (x86)\\Python\\Python36venv\\lib\\site-packages\\setuptools-28.8.0-py3.6.egg', 'D:\\Program Files\\JetBrains\\PyCharm 2018.1.2\\helpers\\pycharm_matplotlib_backend']
```

#### *他是如何工作的？*

> 首先，我们通过 `import `语句导入 `sys` 模块，当 Python 运行` import sys `这一语句时，它会开始寻找 `sys `模块。
>
> `sys` 模块中的 argv 变量通过使用点号予以指明，也就是 `sys.argv` 这样的形式。它清晰地表明了这一名称是 `sys `模块的一部分。这一处理方式的另一个优点是这个名称不会与你程序中的其它任何一个` argv` 变量冲突。
>
> `sys.argv `变量是一系列字符串的列表（List）（列表将在后面的章节予以详细解释）。具体而言， `sys.argv `包含了命令行参数（Command Line Arguments）这一列表，也就是使用命令行传递给你的程序的参数。 Python 将命令行参数存储在 `sys.argv `变量中供我们使用。
>
> 上面命令也可以通过命令行运行：` python module_using_sys.py we are arguments `。

#### 注意：

- 在这里要记住的是，运行的脚本名称在 `sys.argv `的列表中总会位列第一。因此，在这一案例中我们将会有如下对应关系： `'module_using_sys.py'` 对应` sys.argv[0] `，` 'we' `对应`sys.argv[1]` ，` 'are'` 对应` sys.argv[2] `， `'arguments'` 对应 `sys.argv[3]` 。要注意到Python 从` 0 `开始计数，而不是 `1`。
- `sys.path `内包含了导入模块的字典名称列表。你能观察到` sys.path `的第一段字符串是空的——这一空字符串代表当前目录也是` sys.path` 的一部分，它与 PYTHONPATH 环境变量等同。这意味着你可以直接导入位于当前目录的模块。否则，你必须将你的模块放置在`sys.path `内所列出的目录中。
- 当前目录指的是程序启动的目录。你可以通过运行` import os`；`print(os.getcwd())` 来查看你的程序目前所处在的目录。

### 按字节码编译的 .pyc 文件

导入一个模块是一件代价高昂的事情，因此 Python 引入了一些技巧使其能够更快速的完成。其中一种方式便是创建按字节码编译的（Byte-Compiled）文件，这一文件以` .pyc` 为其扩展名，是将 Python 转换成中间形式的文件（还记得《介绍》一章中介绍的 Python 是如何工作的吗？）。这一 `.pyc `文件在你下一次从其它不同的程序导入模块时非常有用——它将更加快速，因为导入模块时所需要的一部分处理工作已经完成了。同时，这些按字节码编译的文件是独立于运行平台的。

**注意：**

这些` .pyc `文件通常会创建在与对应的` .py `文件所处的目录中。如果 Python 没有相应的权限对这一目录进行写入文件的操作，那么` .pyc `文件将不会被创建。

### from..import 语句

如果你希望直接将 `argv `变量导入你的程序（为了避免每次都要输入 `sys.` ），那么你可以通过使用` from sys import argv` 语句来实现这一点。

注意：

> 一般来说，你应该尽量避免使用` from...import` 语句，而去使用` import `语句。这是为了避免在你的程序中出现名称冲突，同时也为了使程序更加易读。

#### 例子：

```python
from math import sqrt
print("Square root of 16 is", sqrt(16))
```

#### 输出：

```python
Square root of 16 is 4.0
```

### 模块的 `__name__`

每个模块都有一个名称，而模块中的语句可以找到它们所处的模块的名称。这对于确定模块是独立运行的还是被导入进来运行的这一特定目的来说大为有用。正如先前所提到的，当模块第一次被导入时，它所包含的代码将被执行。我们可以通过这一特性来使模块以不同的方式运行，这取决于它是为自己所用还是从其它的模块中导入而来。这可以通过使用模块的`__name__` 属性来实现。

#### 例子：

保存为` module_using_name.py `。

```python
if __name__ == '__main__':
	print('This program is being run by itself')
else:
	print('I am being imported from another module')
```

#### 输出：

```python
This program is being run by itself
```

#### 通过命令行运行：

```python
>>> import module_using_name
I am being imported from another module
```

#### *它是如何工作的?*

> 每一个 Python 模块都定义了它的` __name__ `属性。如果它与` __main__ `属性相同则代表这一模块是由用户独立运行的，因此我们便可以采取适当的行动。

### 编写你自己的模块

编写你自己的模块很简单，这其实就是你一直在做的事情！这是因为每一个 Python 程序同时也是一个模块。你只需要保证它以` .py `为扩展名即可。下面的案例会作出清晰的解释。

#### 例子：

保存为 `mymodule.py`

```python
def say_hi():
    print('Hi, this is mymodule speaking.')
__version__ = '0.1'
```

上方所呈现的就是一个简单的模块。正如你所看见的，与我们一般所使用的 Python 的程序相比其实并没有什么特殊的区别。我们接下来将看到如何在其它 Python 程序中使用这一模块。

#### 注意：

> 该模块应该放置于与其它我们即将导入这一模块的程序相同的目录下，或者是放置在sys.path 所列出的其中一个目录下。

另一个模块

保存为 `mymodule_demo.py`

```python
import mymodule

mymodule.say_hi()
print('Version', mymodule.__version__)
```

**输出：**

```python
Hi, this is mymodule speaking.
Version 0.1
```

#### *他是如何工作的？*

> 你会注意到我们使用相同的点符来访问模块中的成员。Python 很好地重用了其中的符号，这充满了“Pythonic”式的气息，这使得我们可以不必学习新的方式来完成同样的事情。

下面是一个使用` from...import `语法的范本（保存为 `mymodule_demo2.py` ）：

```python
from mymodule import say_hi, __version__

say_hi()
print('Version', __version__)
```

**输出：**

```
Hi, this is mymodule speaking.
Version 0.1
```

`mymodule_demo2.py `所输出的内容与` mymodule_demo.py `所输出的内容是一样的。

#### 注意：

> 如果导入到` mymodule `中的模块里已经存在了` __version__ `这一名称，那将产生冲突。这可能是因为每个模块通常都会使用这一名称来声明它们各自的版本号。因此，我们大都推荐最好去使用 import 语句，尽管这会使你的程序变得稍微长一些。

还可以使用：

```python
from mymodule import *
```

这将导入诸如 say_hi 等所有公共名称，但不会导入` __version__ `名称，因为后者以双下划线开头。

Python 之禅：

> Python 的一大指导原则是“明了胜过晦涩” 。你可以通过在 Python 中运行` import this`来了解更多内容。

### `dir `函数

内置的` dir() `函数能够返回由对象所定义的名称列表。 如果这一对象是一个模块，则该列表会包括函数内所定义的函数、类与变量。

该函数接受参数。 如果参数是模块名称，函数将返回这一指定模块的名称列表。 如果没有提供参数，函数将返回当前模块的名称列表。

#### 例子：

```python
$ python
>>> import sys

# 给出 sys 模块中的属性名称
>>> dir(sys)
['__displayhook__', '__doc__',
'argv', 'builtin_module_names',
'version', 'version_info']
# 此处只展示部分条目

# 给出当前模块的属性名称
>>> dir()
['__builtins__', '__doc__',
'__name__', '__package__','sys']

# 创建一个新的变量 'a'
>>> a = 5
>>> dir()
['__builtins__', '__doc__', '__name__', '__package__', 'a']

# 删除或移除一个名称
>>> del a

>>> dir()
['__builtins__', '__doc__', '__name__', '__package__']
```

#### 它是如何工作的?

首先我们看到的是` dir `在被导入的 `sys `模块上的用法。我们能够看见它所包含的一个巨大的属性列表。

随后，我们以不传递参数的形式使用` dir `函数。在默认情况下，它将返回当前模块的属性列表。要注意到被导入模块的列表也会是这一列表的一部分。

观察了 `dir` 函数的操作，我们定义了一个新的变量` a `并为其赋予了一个值，然后在检查`dir `返回的结果，我们就能发现，同名列表中出现了一个新的值。我们通过` del` 语句移除了一个变量或是属性，这一变化再次反映在 `dir` 函数所处的内容中。

**关于 del 的一个小小提示：**

> 这一语句用于删除一个变量或名称，当这一语句运行后，在本例中即 `del a` ，你便不再能访问变量` a `——它将如同从未存在过一般。

注意：

> `dir() `函数能对任何对象工作。例如运行` dir(str) `可以访问`str` （`String`，字符串）类的属性。
>
> 同时，还有一个 `vars() `函数也可以返回给你这些值的属性，但只是可能，它并不能针对所有类都能正常工作。

### 包

现在，你必须开始遵守用以组织你的程序的层次结构。变量通常位于函数内部，函数与全局变量通常位于模块内部。如果你希望组织起这些模块的话，应该怎么办？这便是包（Packages）应当登场的时刻。

包是指一个包含模块与一个特殊的 `__init__.py `文件的文件夹，后者向 Python 表明这一文件夹是特别的，因为其包含了 Python 模块。

让我们这样设想：你想创建一个名为`“world”`的包，其中还包含着` “asia”`、`“africa”`等其它子包，同时这些子包都包含了诸如`“india”`、` “madagascar”`等模块。

下面是你会构建出的文件夹的结构：

```python
<some folder present in the sys.path>/
	- world/
		- __init__.py
		- asia/
			- __init__.py
			- india/
				- __init__.py
				- foo.py
		- africa/
			- __init__.py
			- madagascar/
				- __init__.py
				- bar.py
```

包是一种能够方便地分层组织模块的方式。你将在 **标准库** 中看到许多有关于此的实例。

### 总结：

如同函数是程序中的可重用部分那般，模块是一种可重用的程序。包是用以组织模块的另一种层次结构。Python 所附带的标准库就是这样一组有关包与模块的例子。

我们已经了解了如何使用这些模块并创建你自己的模块。接下来，我们将学习一些有趣的概念，它们被称作**数据结构**。