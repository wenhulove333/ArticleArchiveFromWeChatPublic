#我们来说说Python 第四篇 Python数据类型相关操作以及内建函数#
前一篇我们说了Python里面支持的数据类型，通过上一篇我们知道所有的数据类型都可以看成一个对象，这一篇我们来说一下针对对象操作的一些操作符和内建函数。

##对象值的比较##
比较运算符是用来判断同类型对象是否相等，所有的内建类型都支持比较函数，比较运算返回布尔值True 或 False。

下面我们列出Python用于比较的操作符。

- expr1 < expr2

- expr1 > expr2

- expr1 <= expr2

- expr1 >= expr2

- expr1 == expr2

- expr1 != expr2

具体进行比较的时候，是根据对象的类型来决定如何进行比较。比如数字和字符串的比较规则肯定是不一样的。

另外，Python里面有一个特别的是，多个比较操作可以在同一行上进行，求值顺序从左到右。

	>>> 4 < 3 < 5 != 2 < 7  #相当于(4 < 3) and (3 < 5) and (5 != 2) and (2 < 7)
	False

##对象身份的比较##
对象身份的比较是什么意思呢？我们可以把对象看做是内存中的一块区域，对象的属性和方法都存储在里面，而所有要去索引这个对象的人都会拿到一个id或者地址，对象的属性里面会有一个计数器来记录有多少人引用了自己。

对象身份的比较就是来比较引用的是否是同一个对象，或者也可以理解成是否是同一个地址。

在说对象身份的比较操作符之前，我们先说一个内建函数id()，它的参数就是表示对象的变量。

比如，我们有一个对象a，我们可以通过id(a)来获取对象的id。

我们来判断两个对象身份的时候，可以通过这个内建函数来实现，像这样id(a) == id(b)。Python提供了is 和 is not操作符来实现相同的功能。上面的那个关系表达式等价于 a is b。同样的，id(a) != id(b)等价于a is not b。

##标准类型内置函数##
###type()###
这个函数接收一个对象作为参数，返回它的类型。

	>>> a = 1
	>>> type(a)
	<type 'int'>
###cmp()###
这个函数用于比较两个对象obj1和obj2。如果obj1小于obj2，则返回一个负整数，如果obj1大于obj2，则返回一个正整数，如果obj1等于obj2，则返回0. 如果是用户自定义对象，cmp()会调用该类的特殊方法__cmp__()。

	>>> a, b = 'a', 'b'
	>>> cmp(a, b)
	-1
	>>> cmp(b, a)
	1

###str(), repr()以及``###
这里的两个函数和另外一个操作符都可以方便的以字符串的方式获取对象的内容、类型、数值属性等信息。那它们的区别在哪里呢？str()的目的就是生成一个对象的可读性好的字符串说明，但是它的返回结果只能用来显示，无法用于eval()求值。而另外两个就可以。所以对于repr()函数，我们有的情况下是可以使用obj = eval(repr(obj))，这样是没有问题的。

那一句话就是，repr()的输出是给程序用的；str()的输出是给用户看的。

	>>> a = "wenhu"
	>>> eval(str(a))
	
	Traceback (most recent call last):
	  File "<pyshell#272>", line 1, in <module>
	    eval(str(a))
	  File "<string>", line 1, in <module>
	NameError: name 'wenhu' is not defined
	>>> eval(repr(a))
	'wenhu'

###isinstance()###
这个函数用于判断一个对象是否属于指定的某个或某些个类型。

	>>> def displayNumType(num):
		print num, 'is',
		if isinstance(num, (int, long, float, complex)):
			print 'a number of type:', type(num).__name__
		else:
			print 'not a number at all!!'
	
			
	>>> displayNumType(9)
	9 is a number of type: int
	>>> displayNumType(9L)
	9 is a number of type: long
	>>> displayNumType(9.0)
	9.0 is a number of type: float
	>>> displayNumType(9 + 1j)
	(9+1j) is a number of type: complex
	>>> displayNumType('sdfa')
	sdfa is not a number at all!!

##类型工厂函数##
当你调用类型工厂函数的时候，它们会生成该类型的一个实例。

函数列表如下：

- int(), long(), float(), complex()

- str(), unicode(), basestring()

- list(), tuple()

- type()

- dict()

- set(), frozenset()

- object()

- classmethod()

- staticmethod()

- super()

- property()

- file()

		>>> a = str("hello world!")
		>>> print a
		hello world!


关于对象和对象值的一些操作符还有内建函数就说这么多了，后续我们会一一的对Python里面支持的数据类型展开说明。敬请期待《我们来说说Python 第五篇 Python数据类型之数字》。

