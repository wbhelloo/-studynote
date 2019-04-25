---
title: 简明Python教程-函数
categories: 简明Python教程
tags: Python简明教程学习笔记
date: 2018-07-07 11:27:21
keywords:
---

### 函数

**函数（Functions）**是指可重复使用的程序片段。它允许你为某个代码块赋予名字，允许你通过这一特殊的名字在你的程序任何地方来运行代码块，并可重复任何次数，这就是所谓的**调用（Calling）**函数。

函数可以通过关键字` def` 来定义。这一关键字后跟一个函数的标识符名称，再跟一对圆括号，其中可以包括一些变量的名称，再以冒号结尾，结束这一行。随后而来的语句块是函数的一部分。<!--more-->

例子：

```python
#python function1.py
def say_hello():
    # 该块属于这一函数
    print('hello world')
# 函数结束

say_hello() # 调用函数
say_hello() # 再次调用函数
```

输出：

```python
hello world
hello world
```

*它是如何工作的?*

> 我们以上文解释过的方式定义名为 `say_hello` 的函数。这个函数不使用参数，因此在括号中没有声明变量。函数的参数只是输入到函数之中，以便我可以传递不同的值给它，并获得相应的结果。

注意：

> 我们可以两次调用相同的函数，这意味着我们不必重新把代码再写一次。

### 函数参数

函数中的参数通过将其放置在用以定义函数的一对圆括号中指定，并通过逗号予以分隔。当我们调用函数时，我们以同样的形式提供需要的值。

注意：

> 在定义函数时给定的名称称作**“形参”（Parameters）**，在调用函数时你所提供给函数的值称作**“实参”（Arguments）**。

例子：

```python
def print_max(a, b):
    if a > b:
        print(a, 'is maximum')
    elif a == b:
        print(a, 'is equal to', b)
    else:
        print(b, 'is maximum')

# 直接传递字面值
print_max(3, 4)

x = 5
y = 7
# 以参数的形式传递变量
print_max(x, y)
```

输出：

```python
4 is maximum
7 is maximum
```

它是如何工作的？

>在这里，我们将函数命名为 `print_max` 并使用两个参数分别称作` a `和 `b `。我们使用一个简单的 `if...else `语句来找出更大的那个数，并将它打印出来。
>
>第一次调用函数` print_max `时，我们以**实参**的形式直接向函数提供这一数字。在第二次调用时，我们将变量作为**实参**来调用函数。 `print_max(x, y) `将使得**实参**` x` 的值将被赋值给**形参**`a `，而**实参**` y` 的值将被赋值给**形参**` b` 。在两次调用中， `print_max `都以相同的方式工作。

### 局部变量

当你在一个函数的定义中声明变量时，它们不会以任何方式与身处函数之外但具有相同名称的变量产生关系，也就是说，这些变量名只存在于函数这一**局部（Local）**。这被称为变量的**作用域（Scope）**。所有变量的**作用域**是它们被定义的块，从定义它们的名字的定义点开始。

例子：

```python
x = 50

def func(x):
    print('x is', x)
    x = 2
    print('Changed local x to', x)

func(x)
print('x is still', x)
```

输出：

```python
x is 50
Changed local x to 2
x is still 50
```

它是如何工作的?

> 当我们第一次打印出存在于函数块的第一行的名为 x 的值时，Python 使用的是在函数声明之上的主代码块中声明的这一参数的值。
>
> 接着，我们将值` 2 `赋值给 `x `。` x `是我们这一函数的局部变量。因此，当我们改变函数中`x` 的值的时候，主代码块中的` x `则不会受到影响。
>
> 随着最后一句 `print` 语句，我们展示出主代码块中定义的 `x `的值，由此确认它实际上不受先前调用的函数中的局部变量的影响。

### global 语句

如果你想给一个在程序顶层的变量赋值（也就是说它不存在于任何作用域中，无论是函数还是类），那么你必须告诉 Python 这一变量并非**局部**的，而是**全局（Global）**的。我们需要通过 **global 语句**来完成这件事。因为在不使用 **global 语句**的情况下，不可能为一个定义于函数之外的变量赋值。

例子：

```python
x = 50

def func():
    global x
    print('x is', x)
    x = 2
    print('Changed global x to', x)

func()
print('Value of x is', x)
```

输出：

```python
x is 50
Changed global x to 2
Value of x is 2
```

它是如何工作的?

>  global 语句用以声明 `x `是一个全局变量——因此，当我们在函数中为 `x `进行赋值时，这一改动将影响到我们在主代码块中使用的` x `的值。

### 默认参数值

可以通过在函数定义时附加一个赋值运算符（ = ）来为参数指定默认参数值。

注意：

> 默认参数值应该是常数。更确切地说，默认参数值应该是不可变的。

例子：

```python
# python function_default.py
def say(message, times=1):
    print(message * times)

say('Hello')
say('World', 5)
```

输出：

```python
Hello
WorldWorldWorldWorldWorld
```

*它是如何工作的?*

> 名为 `say `的函数用以按照给定的次数打印一串字符串。如果我们没有提供一个数值，则将按照默认设置，只打印一次字符串。我们通过为参数` times` 指定默认参数值 `1 `来实现这一点。
>
> 在第一次使用 `say `时，我们只提供字符串因而函数只会将这个字符串打印一次。在第二次使用 `say` 时，我们既提供了字符串，同时也提供了一个参数` 5` ，声明我们希望说`（Say）`这个字符串五次。

注意:

>只有那些位于参数列表末尾的参数才能被赋予默认参数值，意即在函数的参数列表中拥有默认参数值的参数不能位于没有默认参数值的参数之前。

### 关键字参数

**关键字参数（Keyword Arguments）**，使用命名（关键字）而非位置来指定函数中的参数。

这样做有两大优点：其一，我们不再需要考虑参数的顺序，函数的使用将更加容易。其二，我们可以只对那些我们希望赋予的参数以赋值，只要其它的参数都具有默认参数值。

例子：

```python
def func(a, b=5, c=10):
    print('a is', a, 'and b is', b, 'and c is', c)

func(3, 7)
func(25, c=24)
func(c=50, a=100)
```

输出：

```python
a is 3 and b is 7 and c is 10
a is 25 and b is 5 and c is 24
a is 100 and b is 5 and c is 50
```

它是如何工作的?

> 名为 `func` 的函数有一个没有默认参数值的参数，后跟两个各自带有默认参数值的参数。
> 在第一次调用函数时， `func(3, 7) `，参数 `a `获得了值` 3` ，参数` b` 获得了值` 7` ，而 `c`获得了默认参数值 `10 `。
> 在第二次调用函数时，` func(25, c=24) `，由于其所处的位置，变量 `a `首先获得了值` 25`。然后，由于命名——即关键字参数——指定，变量 `c` 获得了值` 24` 。变量` b` 获得默认参数值`5 `。
> 在第三次调用函数时， `func(c=50, a=100) `，我们全部使用关键字参数来指定值。在这里要注意到，尽管 `a `在` c `之前定义，但我们还是在变量 `a `之前指定了变量` c `。

### 可变参数

如果想定义的函数里面能够有任意数量的变量，也就是参数数量是可变的，可以通过使用星号来实现。

例子：

```python
def total(a=5, *numbers, **phonebook):
    print('a', a)

    #遍历元组中的所有项目
    for single_item in numbers:
        print('single_item', single_item)

    #遍历字典中的所有项目
    for first_part, second_part in phonebook.items():
        print(first_part,second_part)

print(total(10,1,2,3,Jack=1123,John=2231,Inge=1560))
```

输出：

```python
a 10
single_item 1
single_item 2
single_item 3
Jack 1123
John 2231
Inge 1560
None
```

*它是如何工作的?*

> 当我们声明一个诸如 `*param `的星号参数时，从此处开始直到结束的所有位置参数`（Positional Arguments）`都将被收集并汇集成一个称为`“param”`的**元组**`（Tuple）`。
>
> 类似地，当我们声明一个诸如` **param` 的双星号参数时，从此处开始直至结束的所有关键字参数都将被收集并汇集成一个名为 `param` 的**字典**`（Dictionary）`
>
> *后面章节，详细 讨论元祖和字典。*

### return 语句

`return` 语句用于从函数中返回，也就是中断函数。我们也可以选择在中断函数时从函数中返回一个值。

例子：

```python
def maximum(x, y):
    if x > y:
        return x
    elif x == y:
        return 'The numbers are equal'
    else:
        return y
print(maximum(2, 3))
```

输出：

```pyhton
3
```

*它是如何工作的?*

> `maximum `函数将会返回参数中的最大值，在本例中是提供给函数的数值。它使用一套简单的`if...else `语句来找到较大的那个值并将其返回。
>
> 要注意到如果` return` 语句没有搭配任何一个值则代表着 返回 `None` 。` None `在 Python 中一个特殊的类型，代表着虚无。举个例子， 它用于指示一个变量没有值，如果有值则它的值便是 `None`（虚无） 。

注意：

每一个函数都在其末尾隐含了一句`return None` ，除非你写了你自己的` return` 语句。你可以运行 `print(some_function())` ，其中 `some_function` 函数不使用` return` 语句.

例子：

```python
def some_function():
	pass
```

Python 中的 `pass `语句用于指示一个没有内容的语句块。

提示：

> 有一个名为 max 的内置函数已经实现了“找到最大数”这一功能，所以尽可能地使用这一内置函数。

### DocStrings

Python 有一个非常优美的功能，称作**文档字符串（Documentation Strings）**，当程序实际运行时，我们可
以通过一个函数来获取文档！

例子：

```python
def print_max(x, y):
    '''打印两个数值中的最大数。

    这两个数都应该是整数'''
    # 如果可能，将其转换至整数类型
    x = int(x)
    y = int(y)

    if x > y:
        print(x, 'is maximum')
    else:
        print(y, 'is maximum')

print_max(3, 5)
print(print_max.__doc__)
```

输出：

```python
5 is maximum
打印两个数值中的最大数。

    这两个数都应该是整数
```

*它是如何工作的?*

> 函数的第一行逻辑行中的字符串是该函数的 **文档字符串（DocString）**，注意文档字符串也适用于后面相关章节将提到的**模块（Modules）**与**类（Class）** 。
>
> 我们可以通过使用函数的 __doc__ （注意其中的双下划线）属性（属于函数的名称）来获取函数 print_max 的文档字符串属性。

关于字符串文档的约定：

> 文档字符串所约定的是一串多行字符串，其中第一行**以某一大写字母开始**，以句号结束。第二行为**空行**，后跟的**第三行开始是任何详细的解释说明**。在此强烈建议你在你所有重要功能的所有文档字符串中都遵循这一约定。

### 总结

我们已经了解了许多关于函数的知识，但我们依旧还未覆盖到所有类型的函数。不过，我们已经学到了大部分我们每天都会使用到的 Python 函数。
接下来，我们将了解如何创建并使用 Python 模块。