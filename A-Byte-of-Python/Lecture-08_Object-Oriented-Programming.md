---
title: 简明Python教程-面向对象编程
categories: 简明Python教程
tags: Python简明教程学习笔记
date: 2018-07-18 11:16:28
keywords:
---

### 面向对象编程

目前，我们编写的所有程序中，都是围绕函数设计我们的程序，也就是那些能够处理数据的代码块。这称作**面向过程（Procedure-oriented）的编程方式**。还有另外一种编写程序的方式，它将数据与功能进行组合，并将其包装在被称作**“对象”**的东西内。

<!--more-->

**类**与**对象**是**面向对象编程**的两个主要方面。一个**类**（Class）能够创建一种新的**类型**（Type），其中**对象**（Object）就是类的**实例**（Instance）。可以这样来类比：你可以拥有**类型** int 的变量，也就是说存储整数的变量是 int 类的**实例（对象）**。

**对象**可以使用属于它的普通**变量**来存储数据，这种从属于对象或类的变量叫作**字段**（Field）。对象还可以使用属于类的**函数**来实现某些功能，这种函数叫作类的**方法**（Method）。这两个术语很重要，它有助于我们区分函数与变量，哪些是独立的，哪些又是属于类或对象的。总之**，字段与方法通称类的属性（Attribute）**。

字段有两种类型——它们属于某一类的各个实例或对象，或是从属于某一类本身。它们被分别称作**实例变量**（Instance Variables）与**类变量**（Class Variables）。

通过` class `关键字可以创建一个类。这个类的**字段**与**方法**可以在缩进代码块中予以列出。

#### `self`

**类方法**与**普通函数**区别是——类方法必须多加一个`self`参数在参数列表开头，但是不需要在调用这个功能时为这个参数赋值，Python 会为它提供。注意，如果你有一个没有参数的方法，你仍然需要添加一个参数—— self 。

#### 类

最简单的类（Class）可以通过下面的案例来展示（保存为 `oop_simplestclass.py` ）：

```python
class Person:
    pass # 一个空的代码块

p = Person()
print(p)
```

输出：

```python
<__main__.Person object at 0x000001C0D765B550>
```

***它是如何工作的?***

> 通过使用 `class 类的名称`来创建一个新类。在它之后是一个缩进的语句块，代表这个类的主体。在本例中，我们创建的是一个空代码块，使用 pass 语句予以标明。
>
> 然后，我们通过采用`类的名称()`，给这个类创建一个对象（或是实例，我们将在后面的章节中了解有关实例的更多内容）。为了验证我们的操作是否成功，我们通过直接将它们打印出来来确认变量的类型。结果显示在 Person 类的 __main__ 模块中拥有了一个实例。
>
> 注意，本例中还会打印出计算机内存中存储对象的地址。案例中给出的地址会与你在你的电脑上所能看见的地址不相同，因为 Python 会在它找到的任何空间来存储对象。

#### 方法

我们已经知道**类**与**对象**一可以像函数一样带有方法（Method），唯一的不同在于拥有一个额外的 `self `变量。现在让我们来看看下面的例子（保存为`oop_method.py` ）。

```python
class Person:
    def say_hi(self):
        print('Hello, how are you?')

p = Person()
p.say_hi()
# 上面两行同样可以写成
# Person().say_hi()
```

输出：

```python
Hello, how are you?
```

***它是如何工作的?***

> 通过示例我们可以明白` self` 是如何工作的了。要注意到` say_hi `这一方法不需要参数，但是依旧在函数定义中给出` self` 变量。

#### `__init__` 方法

`__init__` 方法会在类的对象被实例化（Instantiated）时立即运行。这一方法可以对象进行初始化（Initialization）操作。这里你要注意在` init `前后加上的双下划线。

例子：

（保存为 `oop_init.py `）：

```python
class Person:
	def __init__(self, name):
		self.name = name
	def say_hi(self):
		print('Hello, my name is', self.name)
        
p = Person('Swaroop')
p.say_hi()
# 上面两行也可以写作
# Person('Swaroop').say_hi()
```

输出：

```python
Hello, my name is Swaroop
```

***它是如何工作的?***

> 在本例中，我们定义一个接受 `name` 参数（当然还有 `self` 参数）的` __init__ `方法。在这里，我们创建了一个字段，同样称为` name` 。要注意到尽管它们的名字都是`“name”`，但这是两个不相同的变量，因为` self.name `中的点号意味着这个叫作`“name”`的东西是某个叫作`“self”`的对象的一部分，而另一个` name` 则是一个局部变量。
> 当我们在 Person 类下创建新的实例 `p` 时，我们采用的方法是先写下类的名称，后跟括在括号中的参数，形如：` p = Person('Swaroop') `。
> 我们不会特别的调用` __init__ `方法。 这正是这个方法的特殊之处所在。

#### 类变量与对象变量

我们已经了解了类与对象的功能部分（即方法），现在让我们来学习它们的数据部分。数据部分——也就是字段——只不过是绑定（Bound）到类与对象的命名空间（Namespace）的普通变量。这就说明这些名称仅在这些类与对象所存在的上下文中有效，这就是它们被称作“命名空间”的原因。

**字段（Field）**有两种类型——**类变量**与**对象变量**，它们根据究竟是**类**还是**对象**拥有这些变量来进行区分。
**类变量**（Class Variable）是共享的（Shared）——它们可以被属于该类的所有**实例**访问。该类变量只拥有一个副本，当任何一个对象对类变量作出改变时，发生的变动将在其它所有实例中都会得到体现。
**对象变量**（Object variable）由类的每一个独立的对象或实例所拥有。在这种情况下，每个对象都拥有属于它自己的字段的副本，也就是说，它们不会被共享，也不会以任何方式与其它不同实例中的相同名称的字段产生关联。下面一个例子可以帮助理解（保存为`oop_objvar.py `）：

```python
# coding=UTF-8
class Robot:
    """表示有一个带有名字的机器人。"""

    # 一个类变量，用来计数机器人的数量
    population = 0

    def __init__(self, name):
        """初始化数据"""
        self.name = name
        print("(Initializing {})".format(self.name))

        # 当有人被创建时，机器人
        # 将会增加人口数量
        Robot.population += 1

    def die(self):
        """我挂了。"""
        print("{} is being destroyed!".format(self.name))

        Robot.population -= 1

        if Robot.population == 0:
            print("{} was the last one.".format(self.name))
        else:
            print("There are still {:d} robots working.".format(Robot.population))

    def say_hi(self):
        """来自机器人的诚挚问候

        没问题，你做得到。"""
        print("Greetings, my masters call me {}.".format(self.name))

    @classmethod
    def how_many(cls):
        """打印出当前的人口数量"""
        print("We have {:d} robots.".format(cls.population))

droid1 = Robot("R2-D2")
droid1.say_hi()
Robot.how_many()

droid2 = Robot("C-3PO")
droid2.say_hi()
Robot.how_many()

print("\nRobots can do some work here.\n")

print("Robots have finished their work. So let's destroy them.")
droid1.die()
droid2.die()

Robot.how_many()
```

输出：

```python
(Initializing R2-D2)
Greetings, my masters call me R2-D2.
We have 1 robots.
(Initializing C-3PO)
Greetings, my masters call me C-3PO.
We have 2 robots.

Robots can do some work here.

Robots have finished their work. So let's destroy them.
R2-D2 is being destroyed!
There are still 1 robots working.
C-3PO is being destroyed!
C-3PO was the last one.
We have 0 robots.
```

***它是如何工作的?***

> 在本例中，` population `属于` Robot` **类**，因此它是一个**类变量**。` name `变量属于一个**对象**（通过使用 `self `分配），因此它是一个**对象变量**。
>
> 因此，我们通过 `Robot.population `而非` self.population `引用 `population` 类变量。我们对于 `name` 对象变量采用 `self.name `标记法加以称呼，这是这个对象中所具有的方法。要记住这个类变量与对象变量之间的简单区别。同时你还要注意当一个对象变量与一个类变量名称相同时，类变量将会被隐藏。
>
> 除了` Robot.popluation `，我们还可以使用` self.__class__.population` ，因为每个对象都通过`self.__class__ `属性来引用它的类。
>
> `how_many `实际上是一个属于类而非属于对象的方法。这就意味着我们可以将它定义为一个`classmethod`（类方法） 或是一个 `staticmethod`（静态方法） ，这取决于我们是否需要知道这一方法属于哪个类。由于我们已经引用了一个类变量，因此我们使用` classmethod`（类方法） 。
>
> 我们使用装饰器（Decorator）将 `how_many `方法标记为**类方法**。
>
> 你可以将装饰器想象为调用一个包装器（Wrapper）函数的快捷方式，因此启用`@classmethod` 装饰器等价于调用：
>
> ```python
> how_many = classmethod(how_many)
> ```
>
> 你会观察到` __init__ `方法会使用一个名字以初始化 Robot 实例。在这一方法中，我们将population 按 1 往上增长，因为我们多增加了一台机器人。你还会观察到 `self.name `的值是指定给每个对象的，这体现了对象变量的本质。
>
> 你需要记住你只能使用` self `来引用同一对象的变量与方法。这被称作属性引用（`AttributeReference`）。
>
> 在本程序中，我们还会看见针对类和方法的 文档字符串（`DocStrings`） 的使用方式。我们可以在运行时通过 `Robot.__doc__ `访问类的 文档字符串，对于方法的文档字符串，则可以使用`Robot.say_hi.__doc__ `。
>
> 在 `die` 方法中，我们简单地将 `Robot.population `的计数按 1 向下减少。
> 所有的类成员都是公开的。但有一个例外：如果你使用数据成员并在其名字中使用双下划线作为前缀，形成诸如 `__privatevar` 这样的形式，Python 会使用名称调整（`Namemangling`）来使其有效地成为一个私有变量。
> 因此，你需要遵循这样的约定：任何在类或对象之中使用的变量其命名应以下划线开头，其它所有非此格式的名称都将是公开的，并可以为其它任何类或对象所使用。请记得这只是一个约定，Python 并不强制如此（除了双下划线前缀这点）。

#### 继承

面向对象编程的一大优点是对代码的**重用**（Reuse），重用的一种实现方法就是通过**继承**（Inheritance）机制。继承最好是想象成在类之间实现类型与子类型（Type and Subtype）关系的工具。

现在假设你希望编写一款程序来记录一所大学里的老师和学生信息。有一些特征是他们都具有的，例如姓名、年龄和地址。另外一些特征是独有的，如教师的薪水、课程与假期，学生的成绩和学费。

你可以为每一种类型创建独立的类，并对它们进行处理。但增添一条共有信息要分别对两个独立的类进行修改。这很快就会使程序变得笨重。

一个更好的方法是创建一个**公共类**叫作 `SchoolMember`，然后让教师和学生从这个类中**继承**（`Inherit`），也就是说他们将成为这一类型（类）的**子类型**，而我们还可以向这些子类型中添加某些子类特有的特征。

这种方法有诸多优点。如果我们增加或修改了` SchoolMember `的任何功能，它将自动反映在子类型中。举个例子，你可以通过简单地向 `SchoolMember` 类进行操作，来为所有老师与学生添加一条新的 ID 卡字段。不过，对某一子类型作出的改动并不会影响到其它子类型。另一大优点是你可以将某一老师或学生对象看作 `SchoolMember` 的对象并加以引用，这在某些情况下会非常有用，例如，清点学校的总人员数，这被称作**多态性**（`Polymorphism`），

在上文设想的情况中，` SchoolMember `类会被称作**基类**（`Base Class`） 或是**超类**（`Superclass`）。 `Teacher `和 `Student `类会被称作**派生类**（`Derived Classes`） 或是**子类**（`Subclass`）。

例子：

（保存为 `oop_subclass.py`）

```python
# coding=UTF-8

class SchoolMember:
    '''代表任何学校里的成员。'''
    def __init__(self, name, age):
        self.name = name
        self.age = age
        print('(Initialized SchoolMember: {})'.format(self.name))

    def tell(self):
        '''告诉我有关我的细节。'''
        print('Name:"{}" Age:"{}"'.format(self.name, self.age), end=" ")

class Teacher(SchoolMember):
    '''代表一位老师。'''
    def __init__(self, name, age, salary):
        SchoolMember.__init__(self, name, age)
        self.salary = salary
        print('(Initialized Teacher: {})'.format(self.name))

    def tell(self):
        SchoolMember.tell(self)
        print('Salary: "{:d}"'.format(self.salary))

class Student(SchoolMember):
    '''代表一位学生。'''
    def __init__(self, name, age, marks):
        SchoolMember.__init__(self, name, age)
        self.marks = marks
        print('(Initialized Student: {})'.format(self.name))

    def tell(self):
        SchoolMember.tell(self)
        print('Marks: "{:d}"'.format(self.marks))

t = Teacher('Mrs. Shrividya', 40, 30000)
s = Student('Swaroop', 25, 75)

# 打印一行空白行
print()

members = [t, s]
for member in members:
    # 对全体师生工作
    member.tell()
```

输出：

```python
(Initialized SchoolMember: Mrs. Shrividya)
(Initialized Teacher: Mrs. Shrividya)
(Initialized SchoolMember: Swaroop)
(Initialized Student: Swaroop)

Name:"Mrs. Shrividya" Age:"40" Salary: "30000"
Name:"Swaroop" Age:"25" Marks: "75"
```

***它是如何工作的?***

> 要想使用继承，在定义类时我们需要在类后面跟一个包含**基类**名称的元组。然后，我们会注意到基类的` __init__ `方法是通过 `self `变量被显式调用的，因此我们可以初始化对象的**基类**部分。需要注意的是，我们在` Teacher `和` Student` **子类**中定义了`__init__` 方法，Python 不会自动调用**基类** `SchoolMember `的构造函数，你必须自己调用它。相反，如果我们没有在一个子类中定义一个` __init__ `方法，Python 将会自动调用**基类**的构造函数。
>
> 我们可以通过在**方法名**前面加上**基类**名作为前缀，再传入` self `和其余变量，来调用基类的方法。
>
> 注意，当我们使用` SchoolMember `类的 `tell `方法时，我们可以将 `Teacher` 或`Student` 的实例看作 `SchoolMember` 的实例。同时，我们发现被调用的是子类型的` tell `方法，而不是` SchoolMember `的 `tell` 方法。理解这一问题的一种思路是 Python 总会从当前的实际类型中开始寻找方法，如果它找不到，它就会在该类所属的基本类中寻找，这个基本类是在定义子类时后跟的元组指定的。
>
> 超类`tell()`方法的`end=" "`，目的是不在行末尾打印`\n`(换行符)，即允许下一次打印在同一行继续。

#### 总结

我们已经探索了有关类和对象的各个方面，还有与它们相关的各类术语。我们还了解了面向对象编程的益处与陷阱。Python 是高度面向对象的，从长远来看，了解这些概念对你大有帮助。