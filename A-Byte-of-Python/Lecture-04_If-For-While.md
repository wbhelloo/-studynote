---
title: 简明Python教程-控制流语句
categories: 简明Python教程
tags: Python简明教程学习笔记
date: 2018-07-05 16:32:49
keywords:
---

### 控制流语句

在 Python 中有三种控制流语句——` if`、`for `和 `while `。

#### `if` 语句

`if `语句用以检查条件：如果 条件为真（True），我们将运行一块语句（称作 if-block 或 if块），否则 我们将运行另一块语句（称作 else-block 或 else 块），其中 else 从句是可选的。<!--more-->

例子：

```python
#Python if.py
number = 23
guess = int(input('Enter an integer:'))

if guess == number:
    # 新块从这里开始
    print('Congratulations, you guessed it.')
    print('(but you do not win any prizes!)')
    # 新块在这里结束
elif guess < number:
    # 另一代码块
    print('No, it is a little higher than that')
    # 你可以在此做任何你希望在该代码块内进行的事情
else:
    print('No, it is a little lower than that')
    # 你必须通过猜测一个大于（>）设置数的数字来到达这里。

print('Done')
# 这最后一句语句将在
# if 语句执行完毕后执行。
```

输出：

```python
# python if.py
Enter an integer : 50
No, it is a little lower than that
Done

# python if.py
Enter an integer : 22
No, it is a little higher than that
Done

# python if.py
Enter an integer : 23
Congratulations, you guessed it.
(but you do not win any prizes!)
Done
```

*它是如何工作的*

> 在这个程序中，我们根据用户猜测的数字来检查这一数字是否是我们之前所设置的。我们将变量number 设为任何我们所希望的整数，例如`23` ，然后，我们通过` input() `函数来获取用户的猜测数。所谓函数是一种可重复使用的程序。
>
> `input()` 函数将以字符串的形式返回我们所输入的内容。然后我们通过` int` 将这个字符串转换成一个整数并将其储存在变量 `guess` 中。实际上，` int `是一个类`（Class）`，我们可以使用它将一串字符串转换成一个整数。
>
> 接下来，我们将用户提供的猜测数与我们所选择的数字进行对比，如果它们相等，我们就打印一条成功信息。
>
> 然后，我们检查猜测数是否小于我们设置的数字，如果是，我们将告诉用户他们必须猜一个更高一些的数字。在这里我们使用的是`elif`语句，它们实际上将两个相连的` if else-if else`语句合并成一句 `if-elif-else `语句。
>
> 当 Python 完整执行了`if `语句及与其相关的` elif `和 `else `子句后，它将会移动至包含`if `语句的代码块的下一句语句中。在本例中，也就是主代码块（程序开始执行的地方），其下一句语句就是 `print('Done')` 语句。
>
> 在完成这些工作后，Python 会发现已行至程序末尾并宣告工作的完成。

##### **注意：**

> - 在这里我们使用缩进来告诉 Python 哪些语句分别属于哪个块，这便是为什么在 Python 中缩进如此重要。
> - `if`、`elif `和 `else` 语句在结尾处包含一个冒号——我们借此向 Python 指定接下来会有一块语句在后头。
> - 你可以在 `if `块的 一个 if 语句中设置另一个` if` 语句，并可以如此进行下去——这被称作嵌套的` if `语句。
> - `elif `和`else` 部分都是可选的，一个最小规模且有效的 if 语句是这样的：
>
> ```python
> if True:
> 	print('Yes, it is true')
> ```

#### `while` 语句

`while` 语句能够让你在条件为真的前提下重复执行某块语句，` while` 语句是 循环`（Looping）` 语句的一种， `while` 语句同样可以拥有 `else `子句作为可选选项。

例子：

```python
#Python while.py
number = 23
running = True

while running:
    guess = int(input('Enter an integer:'))

    if guess == number:
        print('Congratulations, you guessed it.')
        # 这将导致 while 循环中止
        running = False
    elif guess < number:
        print('No, it is a little higher than that.')
    else:
        print('No, it is a little lower than that.')
else:
    print('The while loop is over.')
    # 在这里你可以做你想做的任何事

print('Done')
```

输出：

```python
#Python while.py
Enter an integer:50
No, it is a little lower than that.
Enter an integer:22
No, it is a little higher than that.
Enter an integer:23
Congratulations, you guessed it.
The while loop is over.
Done
```

*它是如何工作的？*

> 在这一程序中，我们依旧通过猜数游戏来演示，不过新程序的优点在于能够允许用户持续猜测直至他猜中为止——而无需像`if`所做的那样，每次猜测都要重新运行程序。
>
> 首先我们将 `input` 与` if `语句移到 while 循环之中，并在 `while` 循环开始前将变量`running `设置为` True `。程序开始时，我们首先检查变量` running `是否为` True` ，之后再执行相应的 `while` 块。在这一代码块被执行之后，将会重新对条件进行检查，在本例中也就是`running` 变量。如果它依旧为` True `，我们将再次执行 `while` 块，否则我们将继续执行可选的` else` 块，然后进入到下一个语句中。
>
> `else `代码块在 while 循环的条件变为 `False` 时开始执行；如果 while 循环中存在一个 else 代码块，它将总是被执行，除非你通过 break 语句来中断这一循环。
>
> `True` 和` False` 被称作**布尔**`（Boolean）`型，你可以将它们分别等价地视为` 1 `与` 0 `。

#### for 循环

`for...in` 语句是另一种循环语句，其特点是会在一系列对象上进行**迭代（Iterates）**，意即它会遍历序列中的每一个项目。

例子：

```python
# Python for.py
for i in range(1, 5):
    print(i)
else:
    print('The for loop is over')
```

输出：

```pytho
1
2
3
4
The for loop is over
```

*它是如何工作的?*

> 我们通过内置的` range `函数生成这一数字序列，使用 `range `时，需要提供两个数字，`range` 将会返回一个数字序列，从第一个数字开始，至第二个数字结束。例子：`range(1,5) `将输出序列` [1, 2, 3, 4]`，在默认情况下，` range` 将会以` 1` 逐步递增，如果我们向 `range `提供第三个数字，则这个数字将成为逐步递增的加数。举个例子来说明，` range(1,5,2)` 将会输出` [1, 3] `。
>
> 然后 `for `循环就会在这一范围内展开递归——` for i in range(1,5) `等价于 `for i in [1,2, 3, 4]` ，这个操作将依次将队列里的每个数字（或是对象）分配给` i `，一次一个，然后以每个` i` 的值执行语句块，在本例中，我们这一语句块所做的就是打印出这些值。

##### 注意：

> `range(n,m)`这一序列扩展直到第`m-1`个数字，也就是说，它不会包括第`m`个数字在内。
>
> `range()` 每次只会生成一个数字，如果你希望获得完整的数字列表，要在使用` range()` 时调用` list() `。例如下面这样：` list(range(5))` ，它将会返回` [0, 1, 2,3, 4]`。
>
> `else` 部分是可选的，当循环中包含他时，它总会在` for `循环结束后开始执行，除非程序遇到了` break` 语句。

#### break 语句

`break` 语句用以中断`（Break）`循环语句，也就是中止循环语句的执行，即使循环条件没有变更为` False `，或队列中的项目尚未完全迭代时依旧中断语句。

**注意：**

> 如果你 中断 了一个` for` 或` while `循环，任何相应循环中的` else`块都将不会被执行。

例子：

```python
#Python break.py
while True:
    s = input("Enter something:")
    if s == "quit":
        break
    print("Length of the string is",len(s))
print("Done")
```

输出：

```python
Enter something:Programming is fun
Length of the string is 18
Enter something:When the work is done
Length of the string is 21
Enter something:if you wanna make your work also fun:
Length of the string is 37
Enter something:use Python!
Length of the string is 11
Enter something:quit
Done
```

它是如何工作的?

> 通过检查用户输入的是否是 `quit` 这一特殊条件来判断是否应该终止程序。我们通过中断循环并转进至程序末尾来结束这一程序。
>
> 输入字符串的长度可以通过内置的 `len `函数来计算。

##### **注意：**

> `break `语句同样可以适用于` for `循环。

#### continue 语句

`continue` 语句用以告诉 Python 跳过当前循环块中的剩余语句，并继续该循环的下一次迭代。

输入：

```python
#Python continue.py
while True:
    s = input('Enter something:')
    if s == "quit":
        break
    if len(s)<3:
        print("Too small")
        continue
    print("Input is of sufficient length")
```

输出：

```python
Enter something:1
Too small
Enter something:12
Too small
Enter something:123
Input is of sufficient length
Enter something:quit
```

*它是如何工作的？*

> 在本程序中，我们读取用户的输入，只有在输入的字符串长度小于`3` 字符我们才会对其进行处理。为此，我们使用内置的` len `函数和来获取字符串的长度，如果其长度小于` 3`，我们便通过使用 `continue` 语句跳过代码块中的其余语句。否则，循环中的剩余语句将被执行。

##### 注意：

> `continue` 语句同样能用于 `for `循环。

#### 总结

我们已经了解了三种控制流语句—— `if` ， `while` 和 `for `——及其相关的` break` 与`continue` 语句是如何工作的。这些语句是 Python 中一些最常用的部分，因此，熟练使用它们是必要的。