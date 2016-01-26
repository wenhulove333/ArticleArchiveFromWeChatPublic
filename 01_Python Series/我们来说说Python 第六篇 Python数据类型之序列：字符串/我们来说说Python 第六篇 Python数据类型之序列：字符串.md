#我们来说说Python 第六篇 Python数据类型之序列：字符串#
在进入今天的主题之前，我们先了解下序列的概念和序列的通用操作。

序列可以理解成C语言中的数组，它的每一个元素可以通过指定一个偏移量的方式得到，多个元素可以通过切片操作的方式一次得到。

那么序列里面的每一个元素是怎么进行编号的呢？请参照下图


##序列的通用操作##
###标准类型操作符###
适用于所有的序列类型。
###序列类型操作符###
**成员关系操作符（in、not in）** 用来判断一个元素是否属于一个序列。

	>>> aStr = 'hjksdf'
	>>> 'k' in aStr
	True
	>>> 'k' not in aStr
	False

**连接操作符（+）**   用来连接两个序列
  
	>>> firstStr = "Hello "
	>>> secStr = "World!"
	>>> firstStr + secStr
	'Hello World!'

**重复操作符**   获得一个序列的多个拷贝

	>>> (firstStr + secStr) * 6
	'Hello World!Hello World!Hello World!Hello World!Hello World!Hello World!'

**切片操作符（[]，[:]，[::]）**   获得序列中的切片

	>>> aStr = 'hjksdf'
	>>> aStr[0]
	'h'
	>>> aStr[0:4]
	'hjks'
	>>> aStr[::-1]
	'fdskjh'

##字符串##
在Python里面，没有字符和字符串的区分，因此单引号和双引号的作用是相同的，字符串是**不可变类型**，因此是无法更改字符串里面的某一个字符的。

字符串里面简单的初始化，赋值，改变字符创，字符串连接，删除字符串索引，这里就不再说了，这些都非常简单。我们前面的例子中都会有涉及。

下面，我们介绍只适用于字符串的操作符。
###格式化操作符（%）###

**%c**    转换成字符（ASCII码值，或者长度为一的字符串）

**%r**  优先使用repr()函数进行字符串转换

**%s**    优先使用str()函数进行字符串转换

**%d/%i**   转换成有符号十进制数

**%u**   转换成无符号十进制数

**%o**  转换成无符号八进制数

**%x/%X**  转换成无符号十六进制数

**%e/%E**  转换成科学计数法

**%f/%F**   转换成浮点型

**%%**          输出%

**-**   用做左对齐

**+**    在正数面前显示加号（+） 

**空格**   在正数面前显示空格     

**#**      在八进制数前面显示零（'0'），在十六进制前面显示'0x'或者'0X'（取决于用的是'x'还是'X'）

**0**     显示的数字前面填充'0'而不是默认的空格

**%**        '%%'输出一个单一的'%'

**(var)**      映射变量（字典参数），也就是同时要格式化多个变量的时候

**m.n**    m是显示的最小总宽度，n是小数点后的位数

	>>> "%#x" % 100
	'0x64'
	>>> "%#e"  % 87.908765
	'8.790877e+01'
	>>> "%+4d" % 100
	'+100'
	>>> "%s %s" % ("Hello", "World!")
	'Hello World!'

###字符串模板###
其实，我们使用上面的格式化字符串相对来说还是很困难的，而且要记住这么多格式化规则，也是很痛苦的。而字符串模板里面就简化了这个规则，所有的都是使用$符号来表示。你只需要在在代码里面引入Template模块即可（from string import Template）。Template对象有两个方法：substitute()和safe_substitute()。substitute()在key缺少的情况下，会报KeyError异常，而后者在缺少key时，直接原封不动的吧字符串显示出来。

	>>> s = Template('My name is ${lastName} ${firstName}.')
	>>> s.substitute(lastName = 'Li', firstName = 'Gang')
	'My name is Li Gang.'
	>>> s.substitute(lastName = 'Li')
	
	Traceback (most recent call last):
	  File "<pyshell#56>", line 1, in <module>
	    s.substitute(lastName = 'Li')
	  File "D:\personal\08_scutdevrelateinstall\Python27\lib\string.py", line 172, in substitute
	    return self.pattern.sub(convert, self.template)
	  File "D:\personal\08_scutdevrelateinstall\Python27\lib\string.py", line 162, in convert
	    val = mapping[named]
	KeyError: 'firstName'
	>>> s.safe_substitute(lastName = 'Li')
	'My name is Li ${firstName}.'


###原始字符串操作###
在原始字符串里面，不存在转义字符或不能打印的字符。

除了原始字符串符号（引号前面的字母"r"）以外，原始字符串跟普通字符串有着几乎完全相同的语法。'r不区分大小写，但是必须紧挨着第一个引号。

	>>> print '\n'
	
	
	>>> print r'\n'
	\n

###三引号###
三引号让你完全不用关心所为的转移和特殊字符串如何处理，因为它里面包含的字符串是就是你看到的那样。

	>>> """
	sdfa
	  afd
	  afdfa
	dsaffa
		sdafdasf
		"""
	'\nsdfa\n  afd\n  afdfa\ndsaffa\n\tsdafdasf\n\t'

##字符串内建函数##
**cmp()**   和比较操作符行为一直

**len()**     获取字符串长度

**max()和min()**    返回最大或最小的字符

**enumerate()**    可以枚举字符串中的每个字符

	>>> aStr = 'Hello World!'
	>>> for i, t in enumerate(aStr):
		print i, t
	
		
	0 H
	1 e
	2 l
	3 l
	4 o
	5  
	6 W
	7 o
	8 r
	9 l
	10 d
	11 !

**zip()**  这个我们前面说到过，这里就直接略过了。

**raw_input()**   给定字符串提示让用户输入并且返回输入。

	>>> userInput = raw_input("Please input your name: ")
	Please input your name: Li Gang
	>>> print userInput
	Li Gang

就说这几个，其他的诸如字符串查找，拆分，转换等操作，请自行参照string里面的函数实现。

##相关模块##

**string**  字符串操作相关函数和工具

**re**          正则表达式：强大的字符串模式匹配模块

**struct**  字符串和二进制之间的转换

**c/StringIO**  字符串缓冲对象

**base64**  Base16、32和64数据编解码

**codecs**  解码器注册和基类

**crypt**  加密

**difflib**   找出序列间的不同

**hashlib**   多种不同安全哈希算法和信息摘要算法

**hma**  HMAC信息鉴权算法的Python实现

**md5**  RSA的MD5信息摘要鉴权

**rotor**  提供多平台的加解密服务

**sha**   NIAT的安全哈希算法SHA

**stringprep**   提供用于IP协议的Unicode字符串

**textwrap**   文本包装和填充

**unicodedata**   Unicode数据库

字符串就说这些了，敬请期待《我们来说说Python 第七篇 Python数据类型之序列：列表》。