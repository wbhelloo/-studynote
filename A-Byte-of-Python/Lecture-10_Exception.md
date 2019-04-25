---
title: 简明Python教程-异常
categories: 简明Python教程
tags: Python简明教程学习笔记
abbrlink: 89616b86
date: 2018-07-22 20:40:15
keywords:
---

### 异常

当程序出现意外时就会发生异常（`Exception`）。例如，当程序想要读取一个文件，而那个文件不存在，怎么办？又或者你在程序执行时不小心把它删除了，怎么办？这些情况要通过**异常**来进行处理。

类似地，如果程序中出现了一些无效的语句该，怎么办？Python 将会对此进行处理，举起（`Raises`） 它的小手来告诉你哪里出现了一个错误（`Error`）。

<!--more-->

### 错误

你可以想象一个简单的 `print` 函数调用。如果我们把` print` 误拼成` Print `会怎样？(首字母是大写)。在例子中，Python 会抛出（`Raise`）一个语法错误。

```python
>>> Print ("Hello World!")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'Print' is not defined
>>> print ("Hello World!")
Hello World!
```

我们可以看到一个 `NameError `错误被抛出，同时 Python 还会打印出检测到的错误发生的位置。这就是错误处理器（`Error Handler`） 对这个错误所做的事情。

### 异常

我们将尝试（`Try`）去读取用户的输入内容。按下 [`ctrl-d`] 来看看会发生什么事情。

```python
>>> s = input('Enter something --> ')
Enter something --> Traceback (most recent call last):
File "<stdin>", line 1, in <module>
EOFError
```

此处 Python 指出了一个称作` EOFError `的错误，代表着它发现了一个文件结尾（`End ofFile`）符号（由 `ctrl-d `实现）在不该出现的时候出现了。

### 处理异常`try..except `

我们可以通过使用 `try..except `来处理异常状况。一般来说我们会把通常的语句放在` try `代码块中，将我们的错误处理器代码放置在` except `代码块中。

#### 例子：

（保存文` exceptions_handle.py`）

```python
try:
    text = input('Enter something -->')
except EOFError:
    print('Why did you do an EOF on me?')
except KeyboardInterrupt:
    print('You cancelled the operation.')
else:
    print('You entered {}'.format(text))
```

#### 输出：

```python
# Press ctrl + d
$ python exceptions_handle.py
Enter something --> Why did you do an EOF on me?

# Press ctrl + c
$ python exceptions_handle.py
Enter something --> ^CYou cancelled the operation.

$ python exceptions_handle.py
Enter something --> No exceptions
You entered No exceptions
```

#### ***它是如何工作的?***

> 我们将所有可能引发异常和错误的语句放在` try` 代码块中，并将相应的错误或异常的处理器（`Handler`）放在 `except` 子句或代码块中。 `except `子句可以处理某种特定的错误或异常，或者是一个在括号中列出的错误或异常。如果没有提供错误或异常的名称，它将处理所有错误与异常。
>
> 要注意到至少必须有一句 `except`字句与每一句` try `字句相关联。
>
> 如果没有任何错误或异常被处理，那么将调用 Python 默认处理器，终端程序会执行并打印出错误信息。我们还可以拥有一个` else `子句与 `try..except` 代码块相关联，` else `子句将在没有发生异常的时候执行。

### 抛出异常

你可以通过 `raise` 语句来引发一次异常，具体方法是提供错误名或异常名以及要抛出（`Thrown`）异常的对象。
你能够引发的错误或异常必须是直接或间接从属于 `Exception`（异常） 类的派生类。

#### 例子：

（保存为` exceptions_raise.py `）

```python
# encoding=UTF-8
class ShortInputException(Exception):
    '''一个由用户定义的异常类'''
    def __init__(self, length, atleast):
        Exception.__init__(self)
        self.length = length
        self.atleast = atleast

try:
    text = input('Enter something --> ')
    if len(text) < 3:
        raise ShortInputException(len(text), 3)
    # 其他工作能在此处继续正常运行
except EOFError:
    print('Why did you do an EOF on me?')
except ShortInputException as ex:
    print(('ShortInputException: The input was ' +
           '{0} long, expected at least {1}')
          .format(ex.length, ex.atleast))

else:
    print('No exception was raised.')
```

输出：

```python
Enter something --> a
ShortInputException: The input was 1 long, expected at least 3

Enter something --> 123
No exception was raised.
```

***它是如何工作的?***

> 在本例中，我们创建了我们自己的异常类。这一新的异常类型叫作` ShortInputException `。它包含两个字段——获取给定输入文本长度的` length` ，程序期望的最小长度` atleast `。
>
> 在` except `子句中，我们调用了错误类，将该类存储`as`（为） 相应的错误名或异常名。这类似于函数调用中的**形参**与**实参**。在这个特殊的 `except` 子句中我们使用异常对象的` length`与 `atleast `字段来向用户打印一条合适的信息。

### `Try ... Finally`

假设程序正在读取一份文件，你应该如何确保无论是否发生异常，文件对象均会被正确关闭？这可以通过 finally 块来完成。

#### 例子：

（保存该程序为 `exceptions_finally.py`）

```python
import sys
import time
f = None
try:
    f = open("poem.txt")
    # 我们常用的文件阅读风格
    while True:
        line = f.readline()
        if len(line) == 0:
            break
        print(line, end='')
        sys.stdout.flush()
        print("Press ctrl+c now")
        # 为了确保它能运行一段时间
        time.sleep(2)
except IOError:
    print("Could not find file poem.txt")
except KeyboardInterrupt:
    print("!! You cancelled the reading from the file.")
finally:
    if f:
        f.close()
    print("(Cleaning up: Closed the file)")
```

#### 输出：

```python
(Python36venv) E:\PyCharm\Python36\LearnPython_OOP>python exceptions_finally.py
Programming is fun
Press ctrl+c now
!! You cancelled the reading from the file.
(Cleaning up: Closed the file)
```

***它是如何工作的?***

> 我们按照正常流程进行文件读取，同时通过使用 `time.sleep` 函数在每打印一行后，插入两秒休眠，使程序运行变慢（通常情况下 Python 运行非常快）。当程序在处在运行中时，按下` ctrl + c `来中断或取消程序。
> 你会注意到` KeyboardInterrupt` 异常被抛出，之后程序退出。不过，在程序退出之前，`finally`子句得到执行，文件对象被关闭。
> 另外要注意到，我们在` print` 之后使用了` sys.stout.flush() `，以便它能被立即打印到屏幕上。

### `with` 语句

在` try `块中获取资源，然后在` finally` 块中释放资源是一种常见的模式。因此，还有一个`with` 语句使得这一过程可以以一种干净的姿态得以完成。

#### 例子：

（保存为` exceptions_using_with`.py）

```python
with open("poem.txt") as f:
    for line in f:
        print(line, end='')
```

输出：

```python
Programming is fun
When the work is done
if you wanna make your work also fun:
use Python!
```

***它是如何工作的?***

> 程序输出的内容应与上一个案例所呈现的相同。本例的不同之处在于我们使用的是 open 函数与 with 语句——我们将关闭文件的操作交给 `with open` 来自动完成。
> 在幕后发生的事情是有一项 `with `语句所使用的协议（`Protocol`）。它会获取由 `open `语句返回的对象，在本案例中就是`“thefile”`。
> 它总会在代码块开始之前调用` thefile.__enter__ `函数，并且总会在代码块执行完毕之后调用` thefile.__exit__ `。
> 因此，我们在` finally` 代码块中编写的代码应该格外留心 `__exit__ `方法的自动操作。这能够帮助我们避免重复显式使用` try..finally `语句。

### 总结

我们已经讨论了 `try..except `和`try..finally `语句的用法。同时我们也已经看到了如何创建我们自己的异常类型，还有如何抛出异常。

接下来，我们将学习 Python 的标准库。