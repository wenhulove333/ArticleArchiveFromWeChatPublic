#我们来说说Python 第七篇 Python数据类型之序列：列表#
列表类型也是序列式的数据类型，可以通过下标或切片对象去访问某一个或某一块连续的元素。我们通过上篇了解到，字符串是不能改变它的某个下标对应的字符的，但是在列表里面，你可以任意的增加、减少和改变元素。

	>>> aList = [123, 'Hello World!', 9.8, 9 + 8j]
	>>> aList.append([123, 'check']
		     )
	>>> print aList
	[123, 'Hello World!', 9.8, (9+8j), [123, 'check']]
	>>> id(aList)
	47769352L
	>>> aList.append([9+7j, 90])
	>>> id(aList)
	47769352L

由于列表和字符串一样属于序列类型，因此创建列表、访问列表、更新列表和字符串是一样的，请参照上一篇。同样，用于字符串的操作符切片、成员关系、连接和重复操作符同样适用于列表。同样，他们的内置函数也是如此。这里，我们来说一些特殊的东西，这些特殊的东西都是基于列表的特点（随便放什么元素都可以；它是一个序列）。

那就是
##用列表来构建其他的数据结构##
用过C语言基础的肯定可以想的到，那就是构建堆栈和队列。

###堆栈###
我们来想下堆栈的特点，堆栈是一个后进先出（LIFO）的数据结构，可以把这个结构想象成一落盘子，放在最上面的肯定是要被先取走的。那我们直接看实现吧。

- 我们要有一个列表来存放堆栈。

		stack = []

- 我们要有一个往堆栈里面扔数据的操作。

		def pushToStack():
			stack.append(raw_input(' Enter the info that you want to push: ').strip())

- 我们要有一个从堆栈里面取数据的操作。

		def popFromStack():
			if len (stack) == 0:
				print 'stack is empty.'
			else:
				print 'Remove [', `stack.pop()`, ']'

- 当然，我们还要有一个查看当前堆栈的操作。

		def viewstack():
			print stack

下面，我们就可以操作这个堆栈了。

	>>> pushIntoStack()
	Enter the info that you want to push: First
	>>> viewstack()
	['First']
	>>> pushIntoStack()
	Enter the info that you want to push: second
	>>> viewstack()
	['First', 'second']
	>>> popFromStack()
	Remove [ 'second' ]
	>>> viewstack()
	['First']

###队列###
同样，我们来想下队列的特点，队列是一种先进先出（FIFO）的数据类型，大家想下排队的场景。

- 我们要有一个列表来存放队列。

		queue = []

- 我们要有一个往队列里面扔数据的操作。

		def enQ():
			queue.append(raw_input(' Enter the info that you want to put into queue: ').strip())

- 我们要有一个从队列里面取数据的操作。

		def deQ():
			if len (queue) == 0:
				print 'queue is empty.'
			else:
				print 'Remove [', `queue.pop(0)`, ']'

- 当然，我们还要有一个查看当前队列的操作。

		def viewQ():
			print queue

下面，我们就可以操作这个队列了。

	>>> enQ()
	 Enter the info that you want to put into queue: First
	>>> enQ()
	 Enter the info that you want to put into queue: Second
	>>> viewQ()
	['First', 'Second']
	>>> deQ()
	Remove [ 'First' ]
	>>> viewQ()
	['Second']

列表就说这么多了，有了字符串的基础，这里是很简单的。敬请期待《我们来说说Python 第八篇 Python数据类型之序列：元组》。
