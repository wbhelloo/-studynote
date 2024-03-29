

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

## Python基础

以`#`开头的语句是注释


```python
# print absolute value of an integer
a = 100
if a > 0:
    print(a)
else:
    print(-a)
```

    100


### 数据类型和变量

#### 十六进制

十六进制， 用`ox`前缀和0-9，a-f表示，例如`0xab`


```python
0xab
```




    171




```python
0x16
```




    22




```python
0xf
```




    15



#### 浮点数

浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的，比如，1.23x10^9和12.3x10^8是完全相等的。


```python
1.23
```




    1.23




```python
1.23e9
```




    1230000000.0




```python
1.23e-9
```




    1.23e-09



#### 字符串

字符串是以 `单引号'`或 `双引号"` 括起来的任意文本，


```python
'abc'
```




    'abc'




```python
"abcd"
```




    'abcd'



如果'本身也是一个字符，那就可以用`""`括起来，比如`"I'm OK"`包含的字符是`I`，`'`，`m`， `空格`，`O`，`K`这6个字符。


```python
"I'm OK!"
```




    "I'm OK!"




```python
print("I'm OK!")
```

    I'm OK!


如果字符串内部既包含`'`又包含`"`怎么办？可以用转义字符`\`来标识，比如:


```python
'I\'m\"ok\"!'
```




    'I\'m"ok"!'




```python
print('I\'m \"ok\"!')
```

    I'm "ok"!


转义字符\可以转义很多字符，比如 `\n` 表示换行， `\t`表示制表符，字符`\`本身也要转义，所以 `\\` 表示的字符就是 `\`


```python
print("I'm ok")
```

    I'm ok



```python
print('I\'m learning \nPython.')
```

    I'm learning 
    Python.



```python
print('\\\n\\')
```

    \
    \



```python
print('\\\t\\')
```

    \	\


如果字符串里面有很多字符都需要转义，就需要加很多 `\`，为了简化，Python还允许用 `r''` 表示 `''`内部的字符串默认不转义


```python
print(r'\\\t\\')
```

    \\\t\\


如果字符串内部有很多换行，用\n写在一行里不好阅读，为了简化，Python允许用`'''...'''`的格式表示多行内容，


```python
print('line1\nline2\nline3\n')
```

    line1
    line2
    line3
    



```python
print('''line1
... line2
... line3''')
```

    line1
    line2
    line3



```python
print(r'''hello,\n world''')
```

    hello,\n world


#### 布尔值


```python
True
```




    True




```python
False
```




    False




```python
3>2
```




    True




```python
1< 2
```




    True



布尔值可以用`and`、`or`和`not`运算。


```python
True and True
```




    True




```python
True and False
```




    False




```python
5>2 and 1<-1
```




    False



`or`运算是或运算，只要其中有一个为`True`，`or`运算结果就是`True`：


```python
True or False
```




    True




```python
5>2 or 1<-1
```




    True



`not` 运算时非运算， 它时一个单目运算符，把`True`变为`False`, `False`变为`True`


```python
not True
```




    False




```python
not 1<-1
```




    True



#### 空值

空值是Python里一个特殊的值，用`None`表示。`None`不能理解为`0`，因为`0`是有意义的，而`None`是一个特殊的空值。

#### 变量

变量不仅可以是数字，还可以是任意数据类型

变量在程序中就是用一个变量名表示了，变量名必须是大小写英文、数字和_的组合，且不能用数字开头，比如：


```python
a = 1
```

变量`a`是一个整数


```python
t_007 = "T007"
```

变量`t_007`是一个字符串。


```python
Answer = True
```

变量`Answer`是一个布尔值`True`

在Python中，`等号=` 是赋值语句，可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量，


```python
a = 123
print(a)
a = "ABC"
print(a)
```

    123
    ABC


这种变量本身类型不固定的语言称之为**动态语言**，与之对应的是**静态语言**。**静态语言**在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。


```python
x = 10
x = x + 2
print(x)
```

    12


如果从数学上理解`x = x + 2`那无论如何是不成立的，在程序中，赋值语句先计算右侧的表达式`x + 2`，得到结果`12`，再赋给变量`x`。由于`x`之前的值是`10`，重新赋值后，`x`的值变成`12`。

#### 变量在计算机内存中的表示


```python
a = "ABC"
```

当我们写 `a = "ABC"` 时

Python解释器干了两件事情：

在内存中创建了一个'ABC'的字符串；

在内存中创建了一个名为a的变量，并把它指向'ABC'。


```python
a = "ABC"
b = a
a = "DEF"
print(b)
```

    ABC


#### 常量

所谓常量就是不能变的变量，比如常用的数学常数 `π` 就是一个常量。在Python中，通常用全部大写的变量名表示常量.


```python
PI = 3.1415926
```

但事实上`PI`仍然是一个变量，Python根本没有任何机制保证`PI`不会被改变，所以，用全部大写的变量名表示常量只是一个习惯上的用法.

#### 整数的除法为什么也是精确的?

在Python中，有两种除法，一种除法是 `/`


```python
10 / 3
```




    3.3333333333333335



`/` 除法计算结果是 **浮点数**，即使是两个整数*恰好整除*，结果也是**浮点数**


```python
9 / 3
```




    3.0



还有一种除法是``//``，称为**地板除**，两个**整数**的除法仍然是**整数**


```python
10 // 3
```




    3



> 整数的地板除`//`永远是整数，即使除不尽。

因为`//`除法只取结果的整数部分，所以Python还提供一个`余数`运算，可以得到两个整数相除的**余数**


```python
10 % 3
```




    1



无论整数做`//`除法还是`取余数%`，结果永远是整数，所以，整数运算结果永远是精确的。

### 小结：

- Python支持多种数据类型，在计算机内部，可以把任何数据都看成一个“对象”，而变量就是在程序中用来指向这些数据对象的，对变量赋值就是把数据和变量给关联起来。

- 对变量赋值`x = y`是把变量x指向真正的对象，该对象是变量y所指向的。随后对变量y的赋值不影响变量x的指向。

- Python的整数没有大小限制, 而某些语言的整数根据其存储长度是有大小限制的，例如Java对32位整数的范围限制在`-2147483648-2147483647`。

- Python的浮点数也没有大小限制，但是超出一定范围就直接表示为inf（无限大）。

完
