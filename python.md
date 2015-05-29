# Python 教程 #
[廖雪峰](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/)

用Python可以做什么？可以做日常任务，比如自动备份你的MP3；可以做网站，很多著名的网站包括YouTube就是Python写的；可以做网络游戏的后台，很多在线游戏的后台都是Python开发的。总之就是能干很多很多事啦。

Python当然也有不能干的事情，比如写操作系统，这个只能用C语言写；写手机应用，只能用Objective-C（针对iPhone）和Java（针对Android）；写3D游戏，最好用C或C++。

## Python 简介 ##
[Python Documentation contents](https://docs.python.org/2/contents.html)

Python是著名的“龟叔”Guido van Rossum在1989年圣诞节期间，为了打发无聊的圣诞节而编写的一个编程语言。

Python就为我们提供了非常完善的基础代码库，覆盖了网络、文件、GUI、数据库、文本等大量内容，被形象地称作“内置电池（batteries included）”。用Python开发，许多功能不必从零编写，直接使用现成的即可。

除了内置的库外，Python还有大量的第三方库，也就是别人开发的，供你直接使用的东西。当然，如果你开发的代码通过很好的封装，也可以作为第三方库给别人使用。

许多大型网站就是用Python开发的，例如YouTube、Instagram，还有国内的豆瓣。很多大公司，包括Google、Yahoo等，甚至NASA（美国航空航天局）都大量地使用Python。

龟叔给Python的定位是**“优雅”、“明确”、“简单”**，所以Python程序看上去总是简单易懂，初学者学Python，不但入门容易，而且将来深入下去，可以编写那些非常非常复杂的程序。

那Python适合开发哪些类型的应用呢？

首选是网络应用，包括网站、后台服务等等；

其次是许多日常需要的小工具，包括系统管理员需要的脚本任务等等；

另外就是把其他语言开发的程序再包装起来，方便使用。

最后说说Python的缺点。

第一个缺点就是运行速度慢，和C程序相比非常慢，因为Python是解释型语言，你的代码在执行时会一行一行地翻译成CPU能理解的机器码，这个翻译过程非常耗时，所以很慢。而C程序是运行前直接编译成CPU能执行的机器码，所以非常快。

第二个缺点就是代码不能加密。如果要发布你的Python程序，实际上就是发布源代码，这一点跟C语言不同，C语言不用发布源代码，只需要把编译后的机器码（也就是你在Windows上常见的xxx.exe文件）发布出去。要从机器码反推出C代码是不可能的，所以，凡是编译型的语言，都没有这个问题，而解释型的语言，则必须把源码发布出去。

这个缺点仅限于你要编写的软件需要卖给别人挣钱的时候。好消息是目前的互联网时代，靠卖软件授权的商业模式越来越少了，靠网站和移动应用卖服务的模式越来越多了，后一种模式不需要把源码给别人。

## 安装 Python ##
因为Python是跨平台的，它可以运行在Windows、Mac和各种Linux/Unix系统上。在Windows上写Python程序，放到Linux上也是能够运行的。

安装后，你会得到Python解释器（就是负责运行Python程序的），一个命令行交互环境，还有一个简单的集成开发环境。

目前，Python有两个版本，一个是2.x版，一个是3.x版，这两个版本是不兼容的，因为现在Python正在朝着3.x版本进化，在进化过程中，大量的针对2.x版本的代码要修改后才能运行，所以，目前有许多第三方库还暂时无法在3.x上使用。

**两者的区别是什么？？？**

[Python Releases for Windows](https://www.python.org/downloads/windows/)

[环境变量设置方法](http://jingyan.baidu.com/article/48206aeafdcf2a216ad6b316.html)

[Python Tools for Visual Studio](http://pytools.codeplex.com/)

### Python 解释器 ###
当我们编写Python代码时，我们得到的是一个包含Python代码的以.py为扩展名的文本文件。要运行代码，就需要Python解释器去执行.py文件。

#### CPython ####
当我们从Python官方网站下载并安装好Python 2.7后，我们就直接获得了一个官方版本的解释器：CPython。这个解释器是用C语言开发的，所以叫CPython。在命令行下运行python就是启动CPython解释器。

CPython是使用最广的Python解释器。

#### IPython ####
IPython是基于CPython之上的一个交互式解释器，也就是说，IPython只是在交互方式上有所增强，但是执行Python代码的功能和CPython是完全一样的。

CPython用>>>作为提示符，而IPython用In [序号]:作为提示符。

#### PyPy ####
PyPy是另一个Python解释器，它的目标是执行速度。PyPy采用JIT技术，对Python代码进行动态编译（注意不是解释），所以可以显著提高Python代码的执行速度。

绝大部分Python代码都可以在PyPy下运行，但是PyPy和CPython有一些是不同的，这就导致相同的Python代码在两种解释器下执行可能会有不同的结果。如果你的代码要放到PyPy下执行，就需要了解PyPy和CPython的不同点。

#### Jython ####
Jython是运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行。

#### IronPython ####
IronPython和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码。

#### 小结 ####
Python的解释器很多，但使用最广泛的还是CPython。如果要和Java或.Net平台交互，最好的办法不是用Jython或IronPython，而是通过网络调用来交互，确保各程序之间的独立性。

另外，不是所有代码都能在Web版本的IPython中执行，出于安全原因，很多操作（比如文件操作）是受限的，所以有些代码必须在本地环境执行代码。

## 第一个 Python 程序 ##
在Python交互式命令行下，可以直接输入代码，然后执行，并立刻得到结果。

    >>> 100+200
	300
	>>> print 'hello, world'
	hello, world
	>>> exit()

用单引号或者双引号括起来的文本在程序中叫字符串。
### 使用文本编辑器 ###
在Python的交互式命令行写程序，好处是一下就能得到结果，坏处是没法保存。

[Sublime Text](http://www.sublimetext.com/)

[Notepad++](http://notepad-plus-plus.org/)

	C:\Workspace>python hello.py
	hello, world

必须要以.py结尾，其他的都不行。此外，文件名只能是英文字母、数字和下划线的组合。

#### 直接运行 py 文件 ####
在Mac和Linux上是可以的，在.py文件的第一行加上：

	#!/usr/bin/env python

然后，通过命令：

	$ chmod a+x hello.py
	$ ./hello.py

用Python开发程序，完全可以一边在文本编辑器里写代码，一边开一个交互式命令窗口，在写代码的过程中，把部分代码粘到命令行去验证，事半功倍！
### 输入和输出 ###
#### 输出 ####
	>>> print 'The quick brown fox', 'jumps over', 'the lazy dog'
	The quick brown fox jumps over the lazy dog

print会依次打印每个字符串，遇到逗号“,”会输出一个空格。
#### 输入 ####
	>>> name = raw_input()
	mym
	>>> name
	'mym'

raw_input和print是在命令行下面最基本的输入和输出，但是，用户也可以通过其他更高级的图形界面完成输入和输出，比如，在网页上的一个文本框输入自己的名字，点击“确定”后在网页上看到输出信息。

从raw_input()读取的内容永远以字符串的形式返回。

	>>> birth = int(raw_input('birth: '))
	1991
## Python 基础 ##
	# print absolute value of an integer:
	a = 100
	if a >= 0:
	    print a
	else:
	    print -a
### 数据类型和变量 ###
在Python中，能够直接处理的数据类型有以下几种：整数、浮点数、字符串、布尔值（True、False, and、or、not）、空值（None），列表、字典等。

转义字符\可以转义很多字符，比如\n表示换行，\t表示制表符。

为了简化，Python还允许用r' '表示' '内部的字符串默认不转义。

如果字符串内部有很多换行，用\n写在一行里不好阅读，为了简化，Python允许用'''......'''的格式表示多行内容。

	>>> print '\\\t\\'
	\       \
	>>> print r'\\\t\\'
	\\\t\\
	>>> print '''line1
	... line2
	... line3'''
	line1
	line2
	line3
	#上面是在交互式命令行内输入（...为自动生成的），如果写成程序，就是：
	print '''line1
	line2
	line3'''

多行字符串'''...'''还可以在前面加上r使用，请自行测试。（默认不转义）

在Python中，等号=是赋值语句，可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量。这种变量本身类型不固定的语言称之为动态语言。

理解变量在计算机内存中的表示也非常重要：

	a = 'ABC'

Python解释器干了两件事情：

1. 在内存中创建了一个'ABC'的字符串；
2. 在内存中创建了一个名为a的变量，并把它指向'ABC'。

也可以把一个变量a赋值给另一个变量b，这个操作实际上是把变量b指向变量a所指向的数据。
#### 小结 ####
Python支持多种数据类型，在计算机内部，可以把任何数据都看成一个“对象”，而变量就是在程序中用来指向这些数据对象的，对变量赋值就是把数据和变量给关联起来。
### 字符串和编码 ###
#### 字符编码 ####
ASCII编码是1个字节，而Unicode编码通常是2个字节（如果要用到非常偏僻的字符，就需要4个字节）。

如果统一成Unicode编码，乱码问题从此消失了。但是，如果你写的文本基本上全部是英文的话，用Unicode编码比ASCII编码需要多一倍的存储空间，在存储和传输上就十分不划算。

所以，本着节约的精神，又出现了把Unicode编码转化为“可变长编码”的UTF-8编码。UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，常用的英文字母被编码成1个字节，汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节。如果你要传输的文本包含大量英文字符，用UTF-8编码就能节省空间。

现在计算机系统通用的字符编码工作方式：

在**计算机内存**中，统一使用Unicode编码，当需要保存到硬盘或者需要传输的时候，就转换为UTF-8编码。

用记事本编辑的时候，从文件读取的UTF-8字符被转换为Unicode字符到内存里，编辑完成后，保存的时候再把Unicode转换为UTF-8保存到文件。

浏览网页的时候，服务器会把动态生成的Unicode内容转换为UTF-8再传输到浏览器。

所以你看到很多网页的源码上会有类似<meta charset="UTF-8" /\>的信息，表示该网页正是用的UTF-8编码。
#### Python 的字符串 ####
	>>> ord('A')
	65
	>>> chr(65)
	'A'

	>>> print u'中文'
	中文
	>>> u'中'
	u'\u4e2d'

	>>> u'ABC'.encode('utf-8')
	'ABC'
	>>> u'中文'.encode('utf-8')
	'\xe4\xb8\xad\xe6\x96\x87'

	>>> len(u'ABC')
	3
	>>> len('ABC')
	3
	>>> len(u'中文')
	2
	>>> len('\xe4\xb8\xad\xe6\x96\x87')
	6
	
	>>> 'abc'.decode('utf-8')
	u'abc'
	>>> '\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
	u'\u4e2d\u6587'
	>>> print '\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
	中文

	>>> u'中文'.encode('gb2312')
	'\xd6\xd0\xce\xc4'

由于Python源代码也是一个文本文件，所以，当你的源代码中包含中文的时候，在保存源代码时，就需要务必指定保存为UTF-8编码。当Python解释器读取源代码时，为了让它按UTF-8编码读取，我们通常在文件开头写上这两行：

	#!/usr/bin/env python
	# -*- coding: utf-8 -*-

[Python中使用中文](http://www.cnblogs.com/rollenholt/archive/2011/08/01/2123889.html)

[编码格式简介（ANSI、GBK、GB2312、UTF-8、GB18030和 UNICODE）](http://blog.csdn.net/ldanduo/article/details/8203532/)
#### 格式化 ####
	>>> 'Hello, %s' % 'world'
	'Hello, world'
	>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
	'Hi, Michael, you have $1000000.'

	>>> '%2d-%02d' % (3, 1)
	' 3-01'
	>>> '%.2f' % 3.1415926
	'3.14'

%d：整数，%f：浮点数，%s：字符串，%x：十六进制整数

如果你不太确定应该用什么，%s永远起作用，它会把任何数据类型转换为字符串。

有些时候，字符串里面的%是一个普通字符怎么办？这个时候就需要转义，用%%来表示一个%。

由于历史遗留问题，Python 2.x版本虽然支持Unicode，但在语法上需要'xxx'和u'xxx'两种字符串表示方式。

在Python 3.x版本中，把'xxx'和u'xxx'统一成Unicode编码，即写不写前缀u都是一样的，而以字节形式表示的字符串则必须加上b前缀：b'xxx'。
### 使用list和tuple ###
#### list ####
	>>> classmates = ['Michael', 'Bob', 'Tracy']
	>>> classmates
	['Michael', 'Bob', 'Tracy']
	
	>>> len(classmates)
	3
	
	>>> classmates[2]
	'Tracy'
	
	#如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素：
	>>> classmates[-1]
	'Tracy'

	>>> classmates.append('Adam')
	>>> classmates
	['Michael', 'Bob', 'Tracy', 'Adam']
	
	>>> classmates.insert(1, 'Jack')
	>>> classmates
	['Michael', 'Jack', 'Bob', 'Tracy', 'Adam']
	
	>>> classmates.pop()
	'Adam'
	>>> classmates
	['Michael', 'Jack', 'Bob', 'Tracy']
	
	>>> classmates.pop(1)
	'Jack'
	>>> classmates
	['Michael', 'Bob', 'Tracy']
	
	>>> classmates[1] = 'Sarah'
	>>> classmates
	['Michael', 'Sarah', 'Tracy']
	
	#list里面的元素的数据类型也可以不同，比如：
	>>> L = ['Apple', 123, True]

	>>> s = ['python', 'java', ['asp', 'php'], 'scheme']
	>>> len(s)
	4
	
	>>> p = ['asp', 'php']
	>>> s = ['python', 'java', p, 'scheme']

要拿到'php'可以写p[1]或者s[2][1]，因此s可以看成是一个二维数组，类似的还有三维、四维……数组，不过很少用到。

	>>> L = []
	>>> len(L)
	0

	>>> a = ['c', 'b', 'a']
	>>> a.sort()
	>>> a
	['a', 'b', 'c']
#### tuple ####
另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改。

tuple所谓的“不变”是说，tuple的每个元素，**指向永远不变**。即指向'a'，就不能改成指向'b'，指向一个list，就不能改成指向其他对象，但指向的这个list本身是可变的！

	>>> classmates = ('Michael', 'Bob', 'Tracy')
	
	>>> t = ()
	>>> t
	()
	
	#定义一个只有1个元素的tuple：
	>>> t = (1,)
	>>> t
	(1,)

	>>> t = (1)
	>>> t
	1
	#定义的不是tuple，是1这个数！这是因为括号()既可以表示tuple，又可以表示数学公式中的小括号，这就产生了歧义，因此，Python规定，这种情况下，按小括号进行计算，计算结果自然是1。
	#所以，只有1个元素的tuple定义时必须加一个逗号，来消除歧义

### 条件判断和循环 ###
#### 条件判断 ####
	age = 3
	if age >= 18:
	    print 'adult'
	elif age >= 6:
	    print 'teenager'
	else:
	    print 'kid'

#### 循环 ####
	names = ['Michael', 'Bob', 'Tracy']
	for name in names:
	    print name
	
	>>> range(5)
	[0, 1, 2, 3, 4]
	
	sum = 0
	for x in range(101):
	    sum = sum + x
	print sum

	sum = 0
	n = 99
	while n > 0:
	    sum = sum + n
	    n = n - 2
	print sum

交互模式下

	>>> sum = 0
	>>> for x in range(101):
	... 	sum = sum + x
	...
	>>> sum
	5050

IndentationError: expected an indented block

说明此处需要缩进
### 使用dict和set ###
#### dict ####
Python内置了字典：dict的支持，dict全称dictionary，在其他语言中也称为map，使用键-值（key-value）存储，具有极快的查找速度。

	>>> d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
	>>> d['Michael']
	95

	>>> d['Bob'] = 67
	>>> d['Bob']
	67

要避免key不存在的错误，有两种办法，一是通过in判断key是否存在：

	>>> 'Thomas' in d
	False

二是通过dict提供的get方法，如果key不存在，可以返回None，或者自己指定的value：

	>>> d.get('Thomas')
	>>> d.get('Thomas', -1)
	-1

	>>> d.pop('Bob')
	75
	>>> d
	{'Michael': 95, 'Tracy': 85}

和list比较，dict有以下几个特点：

1. 查找和插入的速度极快，不会随着key的增加而增加；
2. 需要占用大量的内存，内存浪费多。

而list相反：

1. 查找和插入的时间随着元素的增加而增加；
2. 占用空间小，浪费内存很少。

所以，dict是用空间来换取时间的一种方法。

dict可以用在需要高速查找的很多地方，在Python代码中几乎无处不在，正确使用dict非常重要，需要牢记的第一条就是**dict的key必须是不可变对象**。

这是因为dict根据key来计算value的存储位置，如果每次计算相同的key得出的结果不同，那dict内部就完全混乱了。这个通过key计算位置的算法称为哈希算法（Hash）。
#### set ####
set和dict类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在set中，没有重复的key。

要创建一个set，需要提供一个list作为输入集合：

	>>> s = set([1, 2, 3])
	>>> s
	set([1, 2, 3])
	
	>>> s = set([1, 1, 2, 2, 3, 3])
	>>> s
	set([1, 2, 3])
	
	>>> s.add(4)
	>>> s
	set([1, 2, 3, 4])
	>>> s.add(4)
	>>> s
	set([1, 2, 3, 4])
	
	>>> s.remove(4)
	>>> s
	set([1, 2, 3])

set可以看成数学意义上的无序和无重复元素的集合，因此，两个set可以做数学意义上的交集、并集等操作：

	>>> s1 = set([1, 2, 3])
	>>> s2 = set([2, 3, 4])
	>>> s1 & s2
	set([2, 3])
	>>> s1 | s2
	set([1, 2, 3, 4])

set和dict的唯一区别仅在于没有存储对应的value，但是，set的原理和dict一样，所以，同样不可以放入可变对象，因为无法判断两个可变对象是否相等，也就无法保证set内部“不会有重复元素”。
#### 再议不可变对象 ####
	>>> a = 'abc'
	>>> a.replace('a', 'A')
	'Abc'
	>>> a
	'abc'

对于不变对象来说，调用对象自身的任意方法，也不会改变该对象自身的内容。相反，这些方法会创建新的对象并返回，这样，就保证了不可变对象本身永远是不可变的。
## 函数 ##
借助抽象，我们才能不关心底层的具体计算过程，而直接在更高的层次上思考问题。

写计算机程序也是一样，函数就是最基本的一种代码抽象的方式。
### 调用函数 ###

### 定义函数 ###
	def my_abs(x):
	    if x >= 0:
	        return x
	    else:
	        return -x

#### 空函数 ####
如果想定义一个什么事也不做的空函数，可以用pass语句。pass语句什么都不做，那有什么用？实际上pass可以用来作为占位符，比如现在还没想好怎么写函数的代码，就可以先放一个pass，让代码能运行起来。pass还可以用在其他语句里，缺少了pass，代码运行就会有语法错误。

	def nop():
	    pass
	
	if age >= 18:
	    pass

#### 参数检查 ####
	def my_abs(x):
	    if not isinstance(x, (int, float)):
	        raise TypeError('bad operand type')
	    if x >= 0:
	        return x
	    else:
	        return -x

字符串：str
#### 返回值 ####
	import math
	
	def move(x, y, step, angle=0):
	    nx = x + step * math.cos(angle)
	    ny = y - step * math.sin(angle)
	    return nx, ny
	
	>>> x, y = move(100, 100, 60, math.pi / 6)
	>>> print x, y
	151.961524227 70.0
	
	>>> r = move(100, 100, 60, math.pi / 6)
	>>> print r
	(151.96152422706632, 70.0)

Python的函数返回多值其实就是返回一个tuple。
#### 小结 ####
定义函数时，需要确定函数名和参数个数；

如果有必要，可以先对参数的数据类型做检查；

函数体内部可以用return随时返回函数结果；

函数执行完毕也没有return语句时，自动return None。

函数可以同时返回多个值，但其实就是一个tuple。
### 函数的参数 ###
Python的函数定义非常简单，但灵活度却非常大。除了正常定义的必选参数外，还可以使用默认参数、可变参数和关键字参数，使得函数定义出来的接口，不但能处理复杂的参数，还可以简化调用者的代码。
#### 默认参数 ####
	def power(x, n=2):
	    s = 1
	    while n > 0:
	        n = n - 1
	        s = s * x
	    return s

设置默认参数时，有几点要注意：

一是必选参数在前，默认参数在后，否则Python的解释器会报错；

二是如何设置默认参数。当函数有多个参数时，把变化大的参数放前面，变化小的参数放后面。变化小的参数就可以作为默认参数。

使用默认参数有什么好处？最大的好处是能降低调用函数的难度。

	def enroll(name, gender, age=6, city='Beijing'):
	    print 'name:', name
	    print 'gender:', gender
	    print 'age:', age
	    print 'city:', city
	
	enroll('Bob', 'M', 7)
	enroll('Adam', 'M', city='Tianjin')

	def add_end(L=[]):
	    L.append('END')
	    return L
	
	>>> add_end([1, 2, 3])
	[1, 2, 3, 'END']
	
	>>> add_end()
	['END', 'END']
	>>> add_end()
	['END', 'END', 'END']

Python函数在定义的时候，默认参数L的值就被计算出来了，即[]，因为默认参数L也是一个变量，它指向对象[]，每次调用该函数，如果改变了L的内容，则下次调用时，默认参数的内容就变了，不再是函数定义时的[]了。

所以，定义默认参数要牢记一点：**默认参数必须指向不变对象**！

	def add_end(L=None):
	    if L is None:
	        L = []
	    L.append('END')
	    return L

为什么要设计str、None这样的不变对象呢？因为不变对象一旦创建，对象内部的数据就不能修改，这样就减少了由于修改数据导致的错误。此外，由于对象不变，多任务环境下同时读取对象不需要加锁，同时读一点问题都没有。我们在编写程序时，如果可以设计一个不变对象，那就尽量设计成不变对象。
#### 可变参数 ####
	def calc(*numbers):
	    sum = 0
	    for n in numbers:
	        sum = sum + n * n
	    return sum

	>>> nums = [1, 2, 3] #list
	>>> calc(*nums)
	14

定义可变参数和定义list或tuple参数相比，仅仅在参数前面加了一个*号。在函数内部，参数numbers接收到的是一个tuple，因此，函数代码完全不变。但是，调用该函数时，可以传入任意个参数，包括0个参数。

#### 关键字参数 ####
可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。

	def person(name, age, **kw):
	    print 'name:', name, 'age:', age, 'other:', kw
	
	>>> person('Michael', 30)
	name: Michael age: 30 other: {}
	
	>>> person('Bob', 35, city='Beijing')
	name: Bob age: 35 other: {'city': 'Beijing'}
	>>> person('Adam', 45, gender='M', job='Engineer')
	name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}
	
	>>> kw = {'city': 'Beijing', 'job': 'Engineer'}
	>>> person('Jack', 24, city=kw['city'], job=kw['job'])
	name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
	
	>>> kw = {'city': 'Beijing', 'job': 'Engineer'}
	>>> person('Jack', 24, **kw)
	name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
#### 参数组合 ####
在Python中定义函数，可以用必选参数、默认参数、可变参数和关键字参数，这4种参数都可以一起使用，或者只用其中某些，但是请注意，参数定义的顺序必须是：**必选参数、默认参数、可变参数和关键字参数**。

	def func(a, b, c=0, *args, **kw):
	    print 'a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw
	
	>>> func(1, 2)
	a = 1 b = 2 c = 0 args = () kw = {}
	>>> func(1, 2, c=3)
	a = 1 b = 2 c = 3 args = () kw = {}
	>>> func(1, 2, 3, 'a', 'b')
	a = 1 b = 2 c = 3 args = ('a', 'b') kw = {}
	>>> func(1, 2, 3, 'a', 'b', x=99)
	a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99}
	
	#通过一个tuple和dict，你也可以调用该函数：
	>>> args = (1, 2, 3, 4)
	>>> kw = {'x': 99}
	>>> func(*args, **kw)
	a = 1 b = 2 c = 3 args = (4,) kw = {'x': 99}

**对于任意函数，都可以通过类似func(\*args, \*\*kw)的形式调用它**，无论它的参数是如何定义的。
#### 小结 ####
Python的函数具有非常灵活的参数形态，既可以实现简单的调用，又可以传入非常复杂的参数。

默认参数一定要用不可变对象，如果是可变对象，运行会有逻辑错误！

要注意定义可变参数和关键字参数的语法：

*args是可变参数，args接收的是一个tuple；

**kw是关键字参数，kw接收的是一个dict。

以及调用函数时如何传入可变参数和关键字参数的语法：

可变参数既可以直接传入：func(1, 2, 3)，又可以先组装list或tuple，再通过\*args传入：func(\*(1, 2, 3))；

关键字参数既可以直接传入：func(a=1, b=2)，又可以先组装dict，再通过\*\*kw传入：func(\*\*{'a': 1, 'b': 2})。

使用**\*args和\*\*kw是Python的习惯写法**，当然也可以用其他参数名，但最好使用习惯用法。
### 递归函数 ###
递归函数的优点是定义简单，逻辑清晰。理论上，所有的递归函数都可以写成循环的方式，但循环的逻辑不如递归清晰。

使用递归函数需要注意防止栈溢出。在计算机中，函数调用是通过栈（stack）这种数据结构实现的，每当进入一个函数调用，栈就会加一层栈帧，每当函数返回，栈就会减一层栈帧。由于栈的大小不是无限的，所以，递归调用的次数过多，会导致栈溢出。

解决递归调用栈溢出的方法是通过尾递归优化，事实上尾递归和循环的效果是一样的，所以，把循环看成是一种特殊的尾递归函数也是可以的。

**尾递归**是指，在函数返回的时候，调用自身本身，并且，return语句不能包含表达式。这样，编译器或者解释器就可以把尾递归做优化，使递归本身无论调用多少次，都只占用一个栈帧，不会出现栈溢出的情况。

尾递归调用时，如果做了优化，栈不会增长，因此，无论多少次调用也不会导致栈溢出。

遗憾的是，大多数编程语言没有针对尾递归做优化，Python解释器也没有做优化，所以，即使把上面的fact(n)函数改成尾递归方式，也会导致栈溢出。

有一个针对尾递归优化的decorator，可以参考源码：

http://code.activestate.com/recipes/474088-tail-call-optimization-decorator/

	def fact(n):
	    return fact_iter(1, 1, n)
	
	def fact_iter(product, count, max):
	    if count > max:
	        return product
	    return fact_iter(product * count, count + 1, max)
#### 小结 ####
使用递归函数的优点是逻辑简单清晰，缺点是过深的调用会导致栈溢出。

针对尾递归优化的语言可以通过尾递归防止栈溢出。**尾递归事实上和循环是等价的**，**没有循环语句的编程语言只能通过尾递归实现循环**。

Python标准的解释器没有针对尾递归做优化，任何递归函数都存在栈溢出的问题。
## 高级特性 ##
在Python中，代码不是越多越好，而是越少越好。代码不是越复杂越好，而是越简单越好。
### 切片 ###
取list、tuple、字符串的部分元素。

初始：结尾（不包含）：步长

[0:3]

[:3]

[-1:]

[-2:-1]

[:10:2]

[::5]

[:]原样复制一个list
### 迭代 ###
只要是可迭代对象，无论有无下标，都可以迭代。list、tuple、dict、string

因为dict的存储不是按照list的方式顺序排列，所以，迭代出的结果顺序很可能不一样。

默认情况下，dict迭代的是key。如果要迭代value，可以用for value in d.itervalues()，如果要同时迭代key和value，可以用for k, v in d.iteritems()。

通过collections模块的Iterable类型判断一个对象是否是可迭代对象。

	>>> for ch in 'ABC':
	...     print ch
	...

	>>> from collections import Iterable
	>>> isinstance('abc', Iterable) # str是否可迭代
	True
	>>> isinstance([1,2,3], Iterable) # list是否可迭代
	True
	>>> isinstance(123, Iterable) # 整数是否可迭代
	False

	>>> for i, value in enumerate(['A', 'B', 'C']): #下标循环，Java
	...     print i, value
	...
	0 A
	1 B
	2 C
	
	>>> for x, y in [(1, 1), (2, 4), (3, 9)]: #两个变量
	...     print x, y
	...


### 列表生成式 ###
列表生成式即List Comprehensions，是Python内置的非常简单却强大的可以用来创建list的生成式。

要生成list [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]可以用range(1, 11)

写列表生成式时，把要生成的元素x * x放到前面，后面跟for循环，就可以把list创建出来。

	>>> [x * x for x in range(1, 11)]
	[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

for循环后面还可以加上if判断。

	>>> [x * x for x in range(1, 11) if x % 2 == 0]
	[4, 16, 36, 64, 100]

还可以使用两层循环，可以生成全排列。

	>>> [m + n for m in 'ABC' for n in 'XYZ']
	['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']

列表生成式也可以使用两个变量来生成list。

	>>> d = {'x': 'A', 'y': 'B', 'z': 'C' }
	>>> [k + '=' + v for k, v in d.iteritems()]
	['y=B', 'x=A', 'z=C']

把一个list中所有的字符串变成小写：

	>>> L = ['Hello', 'World', 'IBM', 'Apple']
	>>> [s.lower() for s in L]
	['hello', 'world', 'ibm', 'apple']

运用列表生成式，可以写出非常简洁的代码。例如，列出当前目录下的所有文件和目录名，可以通过一行代码实现。

	>>> import os # 导入os模块
	>>> [d for d in os.listdir('.')] # os.listdir可以列出文件和目录
	['hello.py']
### 生成器 ###
通过列表生成式，我们可以直接创建一个列表。但是，受到内存限制，列表容量肯定是有限的。而且，创建一个包含100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占用的空间都白白浪费了。

所以，如果列表元素可以按照某种算法推算出来，那我们是否可以在循环的过程中不断推算出后续的元素呢？这样就不必创建完整的list，从而节省大量的空间。在Python中，这种一边循环一边计算的机制，称为生成器（Generator）。

要创建一个generator，有很多种方法。第一种方法很简单，只要把一个列表生成式的[]改成()，就创建了一个generator

	>>> L = [x * x for x in range(10)]
	>>> L
	[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
	>>> g = (x * x for x in range(10))
	>>> g
	<generator object <genexpr> at 0x104feab40>

	>>> g.next()
	0
	>>> g.next()
	1

	>>> g.next()
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	StopIteration

	>>> g = (x * x for x in range(10))
	>>> for n in g:
	...     print n
	...

如果推算的算法比较复杂，用类似列表生成式的for循环无法实现的时候，还可以用函数来实现。

	def fib(max):
	    n, a, b = 0, 0, 1
	    while n < max:
	        print b
	        a, b = b, a + b
	        n = n + 1

仔细观察，可以看出，fib函数实际上是定义了斐波拉契数列的推算规则，可以从第一个元素开始，推算出后续任意的元素，这种逻辑其实非常类似generator。

也就是说，上面的函数和generator仅一步之遥。要把fib函数变成generator，只需要把print b改为yield b就可以了。

	def fib(max):
	    n, a, b = 0, 0, 1
	    while n < max:
	        yield b
	        a, b = b, a + b
	        n = n + 1

	>>> for n in fib(6):
	...     print n
	...

函数是顺序执行，遇到return语句或者最后一行函数语句就返回。而变成generator的函数，在每次调用next()的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行。
#### 小结 ####
generator是非常强大的工具，在Python中，可以简单地把列表生成式改成generator，也可以通过函数实现复杂逻辑的generator。

要理解generator的工作原理，它是在for循环的过程中不断计算出下一个元素，并在适当的条件结束for循环。对于函数改成的generator来说，遇到return语句或者执行到函数体最后一行语句，就是结束generator的指令，for循环随之结束。
## 函数式编程 ##
### 高阶函数 ###
变量可以指向函数。函数名也是变量。

既然变量可以指向函数，函数的参数能接收变量，那么一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。
#### map/reduce ####
[MapReduce: Simplified Data Processing on Large Clusters](http://research.google.com/archive/mapreduce.html)

Python内建了map()和reduce()函数。

map()函数接收两个参数，一个是函数，一个是序列，map将传入的函数依次作用到序列的每个元素，并把结果作为新的list返回。

reduce把一个函数作用在一个序列[x1, x2, x3...]上，这个函数必须接收两个参数，reduce把结果继续和序列的下一个元素做累积计算。

字符串str也是一个序列。
#### filter ####
Python内建的filter()函数用于过滤序列。

和map()类似，filter()也接收一个函数和一个序列。和map()不同的时，filter()把传入的函数依次作用于每个元素，然后根据返回值是True还是False决定保留还是丢弃该元素。

	def not_empty(s):
	    return s and s.strip()
	
	filter(not_empty, ['A', '', 'B', None, 'C', '  '])
	# 结果: ['A', 'B', 'C']
#### sorted ####
	def cmp_ignore_case(s1, s2):
	    u1 = s1.upper()
	    u2 = s2.upper()
	    if u1 < u2:
	        return -1
	    if u1 > u2:
	        return 1
	    return 0
	
	>>> sorted(['bob', 'about', 'Zoo', 'Credit'], cmp_ignore_case)
	['about', 'bob', 'Credit', 'Zoo']
### 返回函数 ###

	def count():
	    fs = []
	    for i in range(1, 4):
	        def f():
	             return i*i
	        fs.append(f)
	    return fs
	
	f1, f2, f3 = count()
	
	>>> f1()
	9
	>>> f2()
	9
	>>> f3()
	9

原因就在于返回的函数引用了变量i，但它并非立刻执行。等到3个函数都返回时，它们所引用的变量i已经变成了3，因此最终结果为9。

返回闭包时牢记的一点就是：返回函数不要引用任何循环变量，或者后续会发生变化的变量。

如果一定要引用循环变量怎么办？方法是再创建一个函数，用该函数的参数绑定循环变量当前的值，无论该循环变量后续如何更改，已绑定到函数参数的值不变：

	>>> def count():
	...     fs = []
	...     for i in range(1, 4):
	...         def f(j):
	...             def g():
	...                 return j*j
	...             return g
	...         fs.append(f(i))
	...     return fs
	... 
	>>> f1, f2, f3 = count()
	>>> f1()
	1
	>>> f2()
	4
	>>> f3()
	9

缺点是代码较长，可利用lambda函数缩短代码。
### 匿名函数 ###
当我们在传入函数时，有些时候，不需要显式地定义函数，直接传入匿名函数更方便。

	>>> map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9])
	[1, 4, 9, 16, 25, 36, 49, 64, 81]
	
	def f(x):
	    return x * x

关键字lambda表示匿名函数，冒号前面的x表示函数参数。

匿名函数有个限制，就是只能有一个表达式，不用写return，返回值就是该表达式的结果。

用匿名函数有个好处，因为函数没有名字，不必担心函数名冲突。此外，匿名函数也是一个函数对象，也可以把匿名函数赋值给一个变量，再利用变量来调用该函数：

	>>> f = lambda x: x * x
	>>> f
	<function <lambda> at 0x10453d7d0>
	>>> f(5)
	25

同样，也可以把匿名函数作为返回值返回，比如：

	def build(x, y):
	    return lambda: x * x + y * y

Python对匿名函数的支持有限，只有一些简单的情况下可以使用匿名函数。

### 装饰器 ###
由于函数也是一个对象，而且函数对象可以被赋值给变量，所以，通过变量也能调用该函数。

	>>> def now():
	...     print '2013-12-25'
	...
	>>> f = now
	>>> f()
	2013-12-25

函数对象有一个__name__属性，可以拿到函数的名字：

	>>> now.__name__
	'now'
	>>> f.__name__
	'now'

现在，假设我们要增强now()函数的功能，比如，在函数调用前后自动打印日志，但又不希望修改now()函数的定义，这种在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。

本质上，decorator就是一个返回函数的高阶函数。所以，我们要定义一个能打印日志的decorator，可以定义如下：

	def log(func):
	    def wrapper(*args, **kw):
	        print 'call %s():' % func.__name__
	        return func(*args, **kw)
	    return wrapper

观察上面的log，因为它是一个decorator，所以接受一个函数作为参数，并返回一个函数。我们要借助Python的@语法，把decorator置于函数的定义处：

	@log
	def now():
	    print '2013-12-25'

调用now()函数，不仅会运行now()函数本身，还会在运行now()函数前打印一行日志：

	>>> now()
	call now():
	2013-12-25

把@log放到now()函数的定义处，相当于执行了语句：

	now = log(now)

由于log()是一个decorator，返回一个函数，所以，原来的now()函数仍然存在，只是现在同名的now变量指向了新的函数，于是调用now()将执行新函数，即在log()函数中返回的wrapper()函数。

wrapper()函数的参数定义是(*args, **kw)，因此，wrapper()函数可以接受任意参数的调用。在wrapper()函数内，首先打印日志，再紧接着调用原始函数。

如果decorator本身需要传入参数，那就需要编写一个返回decorator的高阶函数，写出来会更复杂。比如，要自定义log的文本：

	def log(text):
	    def decorator(func):
	        def wrapper(*args, **kw):
	            print '%s %s():' % (text, func.__name__)
	            return func(*args, **kw)
	        return wrapper
	    return decorator

这个3层嵌套的decorator用法如下：

	@log('execute')
	def now():
	    print '2013-12-25'

执行结果如下：

	>>> now()
	execute now():
	2013-12-25

和两层嵌套的decorator相比，3层嵌套的效果是这样的：

	>>> now = log('execute')(now)

我们来剖析上面的语句，首先执行log('execute')，返回的是decorator函数，再调用返回的函数，参数是now函数，返回值最终是wrapper函数。

以上两种decorator的定义都没有问题，但还差最后一步。因为我们讲了函数也是对象，它有__name__等属性，但你去看经过decorator装饰之后的函数，它们的__name__已经从原来的'now'变成了'wrapper'：

	>>> now.__name__
	'wrapper'

因为返回的那个wrapper()函数名字就是'wrapper'，所以，需要把原始函数的__name__等属性复制到wrapper()函数中，否则，有些依赖函数签名的代码执行就会出错。

不需要编写wrapper.__name__ = func.__name__这样的代码，Python内置的functools.wraps就是干这个事的，所以，一个完整的decorator的写法如下：

	import functools
	
	def log(func):
	    @functools.wraps(func)
	    def wrapper(*args, **kw):
	        print 'call %s():' % func.__name__
	        return func(*args, **kw)
	    return wrapper

或者针对带参数的decorator：

	import functools
	
	def log(text):
	    def decorator(func):
	        @functools.wraps(func)
	        def wrapper(*args, **kw):
	            print '%s %s():' % (text, func.__name__)
	            return func(*args, **kw)
	        return wrapper
	    return decorator

import functools是导入functools模块。模块的概念稍候讲解。现在，只需记住在定义wrapper()的前面加上@functools.wraps(func)即可。

在面向对象（OOP）的设计模式中，decorator被称为装饰模式。OOP的装饰模式需要通过继承和组合来实现，而Python除了能支持OOP的decorator外，直接从语法层次支持decorator。Python的decorator可以用函数实现，也可以用类实现。

decorator可以增强函数的功能，定义起来虽然有点复杂，但使用起来非常灵活和方便。

请编写一个decorator，能在函数调用的前后打印出'begin call'和'end call'的日志。

再思考一下能否写出一个@log的decorator，使它既支持：

	@log
	def f():
	    pass

又支持：

	@log('execute')
	def f():
	    pass
### 偏函数 ###
Python的functools模块提供了很多有用的功能，其中一个就是偏函数（Partial function）。

简单总结functools.partial的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。

	def int2(x, base=2):
	    return int(x, base)
	
	>>> import functools
	>>> int2 = functools.partial(int, base=2)
	>>> int2('1000000')
	64

创建偏函数时，实际上可以接收函数对象、*args和**kw这3个参数，当传入：

	int2 = functools.partial(int, base=2)

实际上固定了int()函数的关键字参数base，也就是：

	int2('10010')

相当于：

	kw = { base: 2 }
	int('10010', **kw)

当传入：

	max2 = functools.partial(max, 10)

实际上会把10作为*args的一部分自动加到左边，也就是：

	max2(5, 6, 7)

相当于：

	args = (10, 5, 6, 7)
	max(*args)

结果为10。
## 模块 ##
为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，很多编程语言都采用这种组织代码的方式。在Python中，一个.py文件就称之为一个模块（Module）。

为了避免模块名冲突，Python又引入了按目录来组织模块的方法，称为包（Package）。

引入了包以后，只要顶层的包名不与别人冲突，那所有模块都不会与别人冲突。现在，abc.py模块的名字就变成了mycompany.abc，类似的，xyz.py的模块名变成了mycompany.xyz。

请注意，每一个包目录下面都会有一个__init__.py的文件，这个文件是必须存在的，否则，Python就把这个目录当成普通目录，而不是一个包。__init__.py可以是空文件，也可以有Python代码，因为__init__.py本身就是一个模块，而它的模块名就是mycompany。
### 使用模块 ###
Python本身就内置了很多非常有用的模块，只要安装完毕，这些模块就可以立刻使用。

我们以内建的sys模块为例，编写一个hello的模块：

	#!/usr/bin/env python
	# -*- coding: utf-8 -*-
	
	' a test module '
	
	__author__ = 'Michael Liao'
	
	import sys
	
	def test():
	    args = sys.argv
	    if len(args)==1:
	        print 'Hello, world!'
	    elif len(args)==2:
	        print 'Hello, %s!' % args[1]
	    else:
	        print 'Too many arguments!'
	
	if __name__=='__main__':
	    test()

第1行和第2行是标准注释，第1行注释可以让这个hello.py文件直接在Unix/Linux/Mac上运行，第2行注释表示.py文件本身使用标准UTF-8编码；

第4行是一个字符串，表示模块的文档注释，任何模块代码的第一个字符串都被视为模块的文档注释；

第6行使用__author__变量把作者写进去，这样当你公开源代码后别人就可以瞻仰你的大名；

以上就是Python模块的标准文件模板，当然也可以全部删掉不写，但是，按标准办事肯定没错。

后面开始就是真正的代码部分。

你可能注意到了，使用sys模块的第一步，就是导入该模块：

	import sys

导入sys模块后，我们就有了变量sys指向该模块，利用sys这个变量，就可以访问sys模块的所有功能。

sys模块有一个argv变量，用list存储了命令行的所有参数。argv至少有一个元素，因为第一个参数永远是该.py文件的名称，例如：

运行python hello.py获得的sys.argv就是['hello.py']；

运行python hello.py Michael获得的sys.argv就是['hello.py', 'Michael]。

最后，注意到这两行代码：

	if __name__=='__main__':
	    test()

当我们在命令行运行hello模块文件时，Python解释器把一个特殊变量__name__置为__main__，而如果在其他地方导入该hello模块时，if判断将失败，因此，**这种if测试可以让一个模块通过命令行运行时执行一些额外的代码**，最常见的就是运行测试。

我们可以用命令行运行hello.py看看效果：

	$ python hello.py
	Hello, world!
	$ python hello.py Michael
	Hello, Michael!

如果启动Python交互环境，再导入hello模块：

	$ python
	Python 2.7.5 (default, Aug 25 2013, 00:04:04) 
	[GCC 4.2.1 Compatible Apple LLVM 5.0 (clang-500.0.68)] on darwin
	Type "help", "copyright", "credits" or "license" for more information.
	>>> import hello
	>>>

导入时，没有打印Hello, word!，因为没有执行test()函数。

调用hello.test()时，才能打印出Hello, word!：

	>>> hello.test()
	Hello, world!

#### 别名 ####
导入模块时，还可以使用别名，这样，可以在运行时根据当前环境选择最合适的模块。比如Python标准库一般会提供StringIO和cStringIO两个库，这两个库的接口和功能是一样的，但是cStringIO是C写的，速度更快，所以，你会经常看到这样的写法：

	try:
	    import cStringIO as StringIO
	except ImportError: # 导入失败会捕获到ImportError
	    import StringIO
	
这样就可以优先导入cStringIO。如果有些平台不提供cStringIO，还可以降级使用StringIO。导入cStringIO时，用import ... as ...指定了别名StringIO，因此，后续代码引用StringIO即可正常工作。

还有类似simplejson这样的库，在Python 2.6之前是独立的第三方库，从2.6开始内置，所以，会有这样的写法：

	try:
	    import json # python >= 2.6
	except ImportError:
	    import simplejson as json # python <= 2.5

由于Python是动态语言，函数签名一致接口就一样，因此，无论导入哪个模块后续代码都能正常工作。
#### 作用域 ####
在一个模块中，我们可能会定义很多函数和变量，但有的函数和变量我们希望给别人使用，有的函数和变量我们希望仅仅在模块内部使用。在Python中，是通过_前缀来实现的。

正常的函数和变量名是公开的（public），可以被直接引用，比如：abc，x123，PI等；

类似__xxx__这样的变量是特殊变量，可以被直接引用，但是有特殊用途，比如上面的__author__，__name__就是特殊变量，hello模块定义的文档注释也可以用特殊变量__doc__访问，我们自己的变量一般不要用这种变量名；

类似_xxx和__xxx这样的函数或变量就是非公开的（private），不应该被直接引用，比如_abc，__abc等；

之所以我们说，private函数和变量“不应该”被直接引用，而不是“不能”被直接引用，是因为Python并没有一种方法可以完全限制访问private函数或变量，但是，从编程习惯上不应该引用private函数或变量。

private函数或变量不应该被别人引用，那它们有什么用呢？请看例子：

	def _private_1(name):
	    return 'Hello, %s' % name
	
	def _private_2(name):
	    return 'Hi, %s' % name
	
	def greeting(name):
	    if len(name) > 3:
	        return _private_1(name)
	    else:
	        return _private_2(name)

我们在模块里公开greeting()函数，而把内部逻辑用private函数隐藏起来了，这样，调用greeting()函数不用关心内部的private函数细节，这也是一种非常有用的代码封装和抽象的方法，即：

外部不需要引用的函数全部定义成private，只有外部需要引用的函数才定义为public。
### 安装第三方模块 ###
在Python中，安装第三方模块，是通过setuptools这个工具完成的。Python有两个封装了setuptools的包管理工具：easy_install和pip。目前官方推荐使用pip。

如果你正在使用Mac或Linux，安装pip本身这个步骤就可以跳过了。

如果你正在使用Windows，请参考安装Python一节的内容，确保安装时勾选了pip和Add python.exe to Path。

在命令提示符窗口下尝试运行pip，如果Windows提示未找到命令，可以重新运行安装程序添加pip。

现在，让我们来安装一个第三方库——Python Imaging Library，这是Python下非常强大的处理图像的工具库。一般来说，第三方库都会在Python官方的pypi.python.org网站注册，要安装一个第三方库，必须先知道该库的名称，可以在官网或者pypi上搜索，比如Python Imaging Library的名称叫PIL，因此，安装Python Imaging Library的命令就是：

	pip install PIL

其他常用的第三方库还有MySQL的驱动：MySQL-python，用于科学计算的NumPy库：numpy，用于生成文本的模板工具Jinja2，等等。
#### 模块搜索路径 ####
默认情况下，Python解释器会搜索当前目录、所有已安装的内置模块和第三方模块，搜索路径存放在sys模块的path变量中：

	>>> import sys
	>>> sys.path
	['', '/Library/Python/2.7/site-packages/pycrypto-2.6.1-py2.7-macosx-10.9-intel.egg', '/Library/Python/2.7/site-packages/PIL-1.1.7-py2.7-macosx-10.9-intel.egg', ...]

如果我们要添加自己的搜索目录，有两种方法：

一是直接修改sys.path，添加要搜索的目录：

	>>> import sys
	>>> sys.path.append('/Users/michael/my_py_scripts')
	
这种方法是在运行时修改，运行结束后失效。

第二种方法是设置环境变量PYTHONPATH，该环境变量的内容会被自动添加到模块搜索路径中。设置方式与设置Path环境变量类似。注意只需要添加你自己的搜索路径，Python自己本身的搜索路径不受影响。
### 使用__future__ ###
由于Python是由社区推动的开源并且免费的开发语言，不受商业公司控制，因此，Python的改进往往比较激进，不兼容的情况时有发生。Python为了确保你能顺利过渡到新版本，特别提供了__future__模块，让你在旧的版本中试验新版本的一些特性。

从Python 2.7到Python 3.x就有不兼容的一些改动，比如2.x里的字符串用'xxx'表示str，Unicode字符串用u'xxx'表示unicode，而在3.x中，所有字符串都被视为unicode，因此，写u'xxx'和'xxx'是完全一致的，而在2.x中以'xxx'表示的str就必须写成b'xxx'，以此表示“二进制字符串”。

	from __future__ import division
	
	print '10 / 3 =', 10 / 3
	print '10.0 / 3 =', 10.0 / 3
	print '10 // 3 =', 10 // 3

问题：难道就是打印个东西？真正使用时测试什么？
## 面向对象编程 ##

### 类和实例 ###

### 访问限制 ###

### 继承和多态 ###

### 获取对象信息 ###


## 资源 ##
[Python 教程](http://www.ziqiangxuetang.com/python/python-tutorial.html)
[Python3 教程](http://www.ziqiangxuetang.com/python3/python3-tutorial.html)

[The Python Standard Library](https://docs.python.org/2/library/index.html)

----------------
python(py)---pbc(so)

import sys

print sys.path

python *.py  ---  \_\_name__ = \_\_main__  vs. 交互

Charm: main未定义，缩进

python-dev，glib-dev

1/beta, ~beta
