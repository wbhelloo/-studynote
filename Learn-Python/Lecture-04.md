

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

## 04 Python基础_条件判断

计算机之所以能做很多自动化的任务，因为它可以自己做条件判断。

比如，输入用户年龄，根据年龄打印不同的内容，在Python程序中，用if语句实现：

### 条件判断


```python
age = 20
if age >= 18:
    print('your age is ', age)
    print('adult')
```

    your age is  20
    adult


也可以给if添加一个else语句，意思是，如果if判断是False，不要执行if的内容，去把else执行了：


```python
age = 3
if age >= 18:
    print('your age is', age)
    print('adult')
else:
    print('your age is', age)
    print('teenager')
```

    your age is 3
    teenager



```python
age = 3
if age >= 18:
    print('adult')
elif age >= 6:
    print('teenager')
else:
    print('kid')
```

    kid


> 注意不要少写了冒号:

`elif`是`else if`的缩写，完全可以有多个`elif`，所以`if`语句的完整形式就是：

    if <条件判断1>:
        <执行1>
    elif <条件判断2>:
        <执行2>
    elif <条件判断3>:
        <执行3>
    else:
        <执行4>


```python
age = 20
if age >= 6:
    print('teenager')
elif age >= 18:
    print('adult')
else:
    print('kid')
```

    teenager


if语句是从上往下判断，如果在某个判断上是True，把该判断对应的语句执行后，就忽略掉剩下的elif和else，所以上面的程序打印的是teenager。

if判断条件还可以简写，比如写：


```python
x = 1
if x:
    print('True')
```

    True


只要x是非零数值、非空字符串、非空list等，就判断为True，否则为False。

### 再看 input 

再看一个有问题的条件判断。用input()读取用户的输入，这样可以自己输入，程序运行得更有意思：


```python
birth = input("birth:")
if birth <  2000:
    print('00前')
else:
    print('00后')
```

    birth:10000



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-8-5315bdc1a478> in <module>
          1 birth = input("birth:")
    ----> 2 if birth <  2000:
          3     print('00前')
          4 else:
          5     print('00后')


    TypeError: '<' not supported between instances of 'str' and 'int'


输入10000，结果报错.

这是因为`input()`返回的数据类型是`str`，`str`不能直接和整数比较，必须先把`str`转换成整数。Python提供了`int()`函数来完成这件事情.


```python
s = input('birth: ')
birth = int(s)
if birth < 2000:
    print('00前')
else:
    print('00后')
```

    birth: 10000
    00后


再次运行，就可以得到正确地结果。但是，如果输入abc呢？又会得到一个错误信息.


```python
s = input('birth: ')
birth = int(s)
if birth < 2000:
    print('00前')
else:
    print('00后')
```

    birth: abc



    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-10-fb7d9761dc6e> in <module>
          1 s = input('birth: ')
    ----> 2 birth = int(s)
          3 if birth < 2000:
          4     print('00前')
          5 else:


    ValueError: invalid literal for int() with base 10: 'abc'


`int()`函数发现一个字符串并不是合法的数字时就会报错，程序就退出了。

### 练习

小明身高1.75，体重80.5kg。请根据BMI公式（体重除以身高的平方）帮小明计算他的BMI指数，并根据BMI指数：

- 低于18.5：过轻

- 18.5-25：正常

- 25-28：过重

- 28-32：肥胖

- 高于32：严重肥胖


```python
length = float(input("请输入身高(例如: 1.70): "))
weight = float(input("请输入体重(例如: 76.00): "))
BMI = weight / (length * length)
print("你的BMI得分是：%.02f" % BMI)

if(BMI > 32.00):
    result = "严重肥胖"
elif(28.00 < BMI <= 32.00):
    result = "肥胖"
elif(25.00 < BMI <= 28.00):
    result = "过重"
elif(18.50 < BMI <= 25.00):
    result = "正常"
else:
    result = "过轻"

print("检测结果：%s " % result)
```

    请输入身高(例如: 1.70):1.76
    请输入体重(例如: 76.00):76.7
    你的BMI得分是：24.76
    检测结果：正常


完
