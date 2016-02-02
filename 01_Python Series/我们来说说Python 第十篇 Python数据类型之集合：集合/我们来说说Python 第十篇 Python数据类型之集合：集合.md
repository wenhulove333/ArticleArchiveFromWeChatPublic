#我们来说说Python 第十篇 Python数据类型之集合：集合#
是的，这里的集合，就是来自数学上的集合概念。集合对象是一组无序排列的可哈希的值（这个特点使得**集合成员**可以作为字典中的键）。

在Python中，集合有两种不同的类型，可变集合（set）和不可变集合（frozenset）。这里需要注意的是：**对于可变集合，你可以添加和修改其中的元素，但是可变集合不是可哈希的，是无法用来作为字典的键或者集合中的元素的。不可变集合刚好相反**。

###创建集合类型和赋值###
我们知道列表和字典，除了使用工厂方法之外都有特别的语法格式创建或赋值。但是对于集合来说，只能使用工厂方法去创建：set()和frozenset()。

	>>> exSet = set('Hello World!')
	>>> exSet
	set(['!', ' ', 'e', 'd', 'H', 'l', 'o', 'r', 'W'])
	>>> exAnotherSet = set('Hello Newer!')
	>>> exAnotherSet
	set(['!', ' ', 'e', 'H', 'l', 'o', 'N', 'r', 'w'])
	>>> type(exSet)
	<type 'set'>
	>>> type(exAnotherSet)
	<type 'set'>

###访问集合###
可以遍历访问集合成员或者判断某项元素是否在集合中。

	>>> 'e' in exSet
	True
	>>> 'N' in exSet
	False
	>>> 'N' in exAnotherSet
	True
	>>> 'N' not in exSet
	True
	>>> for i in exSet:
		print i
	
		
	!
	 
	e
	d
	H
	l
	o
	r
	W

###更新集合###

	>>> exSet.add('s')  #添加新的元素
	>>> print exSet
	set(['!', ' ', 'e', 'd', 'H', 'l', 'o', 's', 'r', 'W'])
	>>> exSet.update('Welcome')  #使用新的元素更新集合
	>>> exSet
	set(['!', ' ', 'c', 'e', 'd', 'H', 'm', 'l', 'o', 's', 'r', 'W'])
	>>> exSet.remove('c')  #移除指定的元素
	>>> exSet
	set(['!', ' ', 'e', 'd', 'H', 'm', 'l', 'o', 's', 'r', 'W'])
	>>> exFrozenSet = frozenset('can\'t change me')
	>>> exFrozenSet
	frozenset(['a', ' ', 'c', 'e', 'g', "'", 'h', 'm', 'n', 't'])
	>>> exFrozenSet.add('s') 
	
	Traceback (most recent call last):
	  File "<pyshell#58>", line 1, in <module>
	    exFrozenSet.add('s')
	AttributeError: 'frozenset' object has no attribute 'add'
	>>> del exSet  #删除集合本身

前面我们说了，这里的集合和数学里面的集合概念是非常类似的，那么我们来看下表达集合关系的符合哪些吧？

###集合关系操作符###

- 成员关系：前面已经说过了，这里只列表操作符（in，not  in）。

- 等价、不等价：用于集合之间的比较，规则和数学里面一致。操作符（==，!=）。

- 子集、超集
	
	Set用Python的比较操作符检查某集合是否是其他集合的超集或子集。“小于”符号（<，<=）用来判断子集，"大于"符号（>，>=）用来判断超集。

	“小于”和“大于”意味着两个集合在比较时不能相等。等于号允许非严格定义的子集和超集。

	Set支持严格（<）子集和非严格（<=）子集，也支持严格（>）超集和非严格（>=）超集。只有当第一个集合是第二个集合的严格子集是，我们才称第一个集合“小于”第二个集合，同理，只有当第一个集合是第二个集合的严格超集时，我们才称第一个集合“大于”第二个集合。


		>>> set('shop') < set('cheeseshop')
		True
		>>> set('shop') <= set('cheeseshop')
		True
		>>> set('cheeseshop') <= set('cheeseshop')
		True
		>>> set('bookshop') >= set('shop')
		True

- 合集（Union）（|）

	联合（union）操作和集合的OR其实是等价的。两个集合的联合是一个新集合，新集合中的每个元素至少属于其中一个集合的成员。

		>>> oneSet = set('Hello')
		>>> secSet = set('World')
		>>> oneSet | secSet
		set(['e', 'd', 'H', 'l', 'o', 'r', 'W'])

- 交集 （Retention/Intersection）（&）

	交集操作和集合的AND其实是等价的。两个集合的交集是一个新集合，新集合中的每个元素同时是两个集合中的成员。

		>>> oneSet = set('Hello')
		>>> secSet = set('World')
		>>> oneSet & secSet
		set(['l', 'o'])

- 差补、相对补集（Difference）（-）

	两个集合的补差或相对补集是指新集合中的元素只属于该操作符前面的集合，不属于操作符后面的集合。它有一个等价的方法，那就是difference()。

		>>> oneSet = set('Hello')
		>>> secSet = set('World')
		>>> oneSet - secSet
		set(['H', 'e'])

- 对称差分（Symmetric Difference）（^）

	对称差分和集合的XOR（异或）其实是等价的。两个集合的异或是一个新集合，新集合中的每个元素只能属于两个集合中的其中一个。

		>>> oneSet = set('Hello')
		>>> secSet = set('World')
		>>> oneSet ^ secSet
		set(['e', 'd', 'H', 'r', 'W'])

- 对于可变集合来说，可以这么使用上面的操作符。

	- Union Update （|=）

	- Retention/Intersection Update （&=）

	- Difference Update （-=）

	- Symmetric Difference Update  （^=）

###集合内建方法###

这里的大多数都是上述操作符对应的集合方法。

- 适用于所有的集合

	- s.issubset(t)  如果s是t的子集，则返回True，否则返回False。

	- s.issuperset(t) 如果t是s的超集，则返回True，否则返回False。

	- s.union(t) 返回一个新集合，该集合是s和t的并集。

	- s.intersection(t) 返回一个新集合，该集合是s和t的交集。

	- s.difference(t) 返回一个新集合，该集合是s的成员，但不是t的成员。

	- s.symmetric_difference(t) 返回一个新集合，该集合是s或t的成员，但不是s和t共有的成员。

	- s.copy() 返回一个新集合，它是集合s的浅复制。

- 仅适用于可变集合

	- s.update(t)  用t中的元素修改s

	- s.intersection_update(t) s中的成员是共同属于s和t的元素

	- s.difference_update(t) s中的成员是属于s但不包含在t中的元素

	- s.symmetric_difference_update(t) s中的成员更新为那些包含在s或t中，但不是s和t共有的元素

	- s.add(obj)  在集合s中添加对象obj

	- s.remove(obj) 在集合s中删除对象obj，如果obj不是集合中的元素，会引发KeyError错误

	- s.discard(obj) 如果obj是集合s中的元素，从集合s中删除对象obj

	- s.pop() 删除集合s中的任意一个对象，并返回它

	- s.clear() 删除集合s中的所有元素

集合部分就说这么多了，到此为止，Python内置的数据类型我们就说完了。敬请期待《我们来说说Python 第十一篇 Python程序流程控制：条件和循环》。