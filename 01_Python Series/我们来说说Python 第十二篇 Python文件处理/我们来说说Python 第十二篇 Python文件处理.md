#我们来说说Python 第十二篇 Python文件处理#
存储是非常重要的一个概念，在实际的场景中，我们有各种各样的数据类型需要存储，简单到字符串，复杂到对象。这一篇我们就来说下存储中一个很重要的概念---文件对象。

文件对象不仅仅限于普通的磁盘文件，它可以包含其他抽象层面的“文件”。比如说一个URL，一个TCP客户端等，我们都可以抽象成为文件。**一个重要的概念，文件是连续的字节序列。**

下面我们就一一的来看文件操作的内建函数、内建方法以及内建属性。

###打开文件###
**open()**内建函数成功打开文件后会返回一个文件对象，否则会引发一个错误。关于异常错误，我们后续会说到，这个就不展开了。

**语法**

	file_object = open(file_name, access_mode='r', buffering=-1)

**参数**

	file_name：打开的文件名字的字符串，可以是相对路径或者绝对路径。
	access_mode：r（以读方式打开，打开的文件必须存在）；rU（以读方式打开，同时提供通用换行符支持，打开的文件必须存在）；a（以追加方式打开，文件不存在将会创建文件）；r+/w+/a+（以读写方式打开，文件不存在将会创建文件）；b（以二进制模式打开，要结合读写方式标识，注意：在unix系统里面把所有的文件都当做二进制文件，这个标志位可有可无，为了程序可以移植到非Unix系统上面，最好是加上）
	bufferring：访问文件所采用的缓冲方式。0表示不缓冲，1表示只缓冲一行数据，大于1表示缓冲区大小，不提供或负值表示采用系统默认缓冲机制（即对任何类电报机（tty）设备使用行缓冲，其他设备使用正常缓冲）。

**file()**是工厂方法，和open()具有相同的功能。

前面我们说到了**通用换行符**，为什么会引入这个概念呢？原因就是不同平台上面表示行结束的符号不一致。开启了通用换行符后，在读取文件的时候，换行符会被替换为统一的换行符NEWLINE(\n)。注意：这个特性只用于读取文件。

###读取数据###
**read()**方法用来直接读取字节到字符串中，最多读取给定数目个字节。如果没有给定size参数（默认值为-1）或者size值为负，将会读取整个文件。

**readline()**读取文件的一行（包含行结束符）。它也有一个size参数，默认值为-1，读到行结束符，如果size超过了一行的大小，以行结束符为结束条件，否则以size为结束条件。

**readlines()**读取所有剩余的行，返回字符串列表。

**for eachline in file**在引入迭代器和文件迭代的功能后，这个看起来就很厉害了。

###写入数据###
**write()** 和read()相反，就是写入数据。

**writelines**和readlines()相反，就是写入数据列表

需要注意的是，写方法都不会自动加入行结束符，需要自己控制。

###文件内当前位置移动###
**seek()**移动文件指针到不同的位置，它有两个参数，第一个表示偏移，第二个表示从哪里开始偏移（0-SEEK_SET，1-SEEK_CUR，2-SEEK_END）。

这里再说一下tell()函数，它是获取当前文件指针的位置。

###关闭文件###
**close()** 用来关闭文件

###其他方法###
**fileno()** 获取文件的描述符。

**flush()** 把内部缓冲区中的数据立刻写入文件。

**isatty()** 判断文件是否是一个类tty设备。

**truncate()**将文件截取到当前文件指针位置，或者给定size。

###不同操作系统差异性处理###
我们应该经常遇到这种情况，在不同的操作系统上面使用的一些符号是不一样的，比如：换行符、路径分隔符。在python的os模块里面，这种情形被考虑了进去，使得我们可以完美的写跨平台的python程序。

那os模块是怎么解决的呢？它增加了一些属性，在导入os模块的时候，这些属性的值会自动适配。

	linesep：行分隔符
	sep：    文件路径名分隔符，比如a\b\c这个路径中的\。
	pathsep：文件路径分隔符，比如a\b\c;k\h\l中的;。
	curdir： 当前工作目录的字符串名称（.）
	pardir： 当前工作目录的父目录的字符串名称（..）

###文件系统###
既然我们要处理文件，我们就需要知道文件的位置，作不同目录的切换，也就是文件管理。

这里大概可以分成下面几类：

- 文件处理

- 目录处理

- 访问权限

- 文件操作

- 设备号

具体的细节，请需要的小伙伴们自行百度或谷歌。

###永久存储###
我们在这一篇的开头就说到了。这一篇是就不详细说明了，后续会有对应的文章展开说明。

这一篇就到这里了，敬请期待《我们来说说Python 第十三篇 Python错误异常处理》。