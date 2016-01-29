#我们来说说Python 第九篇 Python数据类型之映射：字典#
字典是Python语言中唯一的映射类型。映射类型对象里哈希值（键，key）和指向的对象（值，value）是一对多的关系。一个字典对象是可变的，它是一个容器类型，能存储任意个数的Python对象，其中也包含其他容器类型。字典类型和序列类型容器类的区别是存储和访问数据的方式不同。序列类型只用数字类型的键。映射类型可以使用其他对象类型做键。也是因为这个原因，映射类型的数据是无序的。但是，字典有非常出色的查询性能。那么，下面就让我们一点一点的来了解字典吧。

###创建字典###
三种方法

- 直接把字典赋值给一个变量

		dictEx = {'name': 'Li Gang', 'age': 28, 'gender': 'male'}

- 使用工厂方法dict()

		dictEx = dict((['name', 'Li Gang'], ['age', 28], ['gender', 'male']))

- 内建方法fromkeys()创建一个默认字典

		dictEx = {}.fromkeys(('name', 'age',  'gender'), 'Li Gang')

###访问字典###

- 遍历字典

		>>> for key in dictEx.keys():
			print 'key=%s, value=%s' % (key, dictEx[key])
		
			
		key=gender, value=Li Gang
		key=age, value=Li Gang
		key=name, value=Li Gang

- 判断一个元素是否存在字典中
		
		>>> 'name' in dictEx
		True
		>>> dictEx.has_key('name')
		True

- 更新字典
	
		>>> dictEx['name'] = 'Niu niu'
		>>> print dictEx
		{'gender': 'Li Gang', 'age': 'Li Gang', 'name': 'Niu niu'}
		>>> dictEx['hobby'] = 'Shuttleball'
		>>> print dictEx
		{'gender': 'Li Gang', 'age': 'Li Gang', 'name': 'Niu niu', 'hobby': 'Shuttleball'}

- 删除字典元素和字典

		>>> del dictEx['hobby']      #删除键值为hobby的元素
		>>> print dictEx
		{'gender': 'Li Gang', 'age': 'Li Gang', 'name': 'Niu niu'}
		>>> dictEx.pop('name')     #删除并返回键值为name的元素
		'Niu niu'
		>>> dictEx.clear()                 #删除字典中的所有元素
		>>> print dictEx
		{}
		>>> del dictEx                       #删除字典
		>>> print dictEx
		
		Traceback (most recent call last):
		  File "<pyshell#26>", line 1, in <module>
		    print dictEx
		NameError: name 'dictEx' is not defined

###字典比较算法###

- 第一步，比较字典长度，字典键的个数越多，字典就越大。

			len(dict1) > len(dict2) => dict1 > dict2

- 第二步，如果字典的长度相同，那么就比较字典的键：键比较的顺序和keys()方法返回键的顺序相同。依次对键值进行比对，如果dict1中第一个不同的键大于dict2的第一个不同的键，cmp()就会返回正值。

- 第三步，如果两个字典的长度相同并且键也是完全匹配的话，就会对键所对应的值进行比较，如果dict1比dict2中相同的键所对应的值打，cmp会返回正值。

- 第四步，如果两个字典长度相同、键也一样并且键对应的值也一样的话，那么这两个字典就完全匹配，返回0.

###字典的键###
字典中的值是没有任何限制的。它们可以使任意的Python对象，即从标准对象到用户自定义对象都可以，但是字典中的键是有类型限制的。

- **不允许一个键对应多个值**

	每个键只能对应一个项。注意：这个和相同的hash值下面可能有几个对象是不一样的，熟悉哈希表的小伙伴们应该可以理解这一点。

	因此，如果在Python里面如果对字典里面的元素赋值的时候，存在的会覆盖其值，不存在就会被创建和添加。

- **键必须是可以哈希的**

	我们前面说过，大多数Python对象是可以作为键的，只要他们可以被哈希。所有不可变的类型都是可哈希的，因此它们可以作为字典的键。这里我们要强调一个问题：**这个问题是针对数字的，值相同的数字表示相同的键，无论它的数字类型是什么样的。**

	但是，有一些可变对象也可以哈希，比如一个实现了__hash__()特殊方法的类，因为__hash__()方法返回一个整型，因此最终作为字典的键的值仍然是不可变的。

	在这里我们要特别来说下元组，我们知道元组是不可变的（当然这里有一些限制，就是元组里面只包含不可变参数）。

	这里我们举一个例子，就是用户登录管理系统，这里我们就可以使用用户名和密码创建一个元组作为记录登录用户信息的键。代码实现就不写，感兴趣的小伙伴们可以尝试下。

###字典内建方法###
最后，我们看下字典都提供了那些方法来供我们方便的操作。

- **dict.clear()**  删除字典中的所有元素

- **dict.copy()**   返回字典（浅复制）的一个副本

- **dict.fromkeys(seq, val=None)**  创建并返回一个字典，以seq中的元素作为该字典的键，val做该字典中所有键对应的初始值，默认为None

- **dict.get(key, default=None)**   对字典dict中的键key，返回它对应的值value，如果字典中不存在此键，则返回default的值。

- **dict.has_key(key)**  如果键在字典中存在，返回True，否则返回False。

- **dict.items()**   返回一个包含字典中键、值对元组的列表

- **dict.keys()**     返回一个包含字典中键的列表

- **dict.iteritems()、iterkeys()、itervalues（）**   这三个方法和前面的items()、keys()和values()区别就是这里返回一个迭代子

- **dict.pop(key[,default])**  和get方法相似，只是如果存在会删除对应的键值，不存在的话，会引发KeyError异常。

- **dict.setdefault(key, default=None)**  和方法set()相似，如果字典中不存在指定的键，使用默认值给其赋值。

- **dict.update(dict2)** 将字典dict2的键-值对添加到字典dict

- **dict.values()**   返回一个包含字典中所有值的列表

字典就说这么多了，敬请期待《我们来说说Python 第十篇 Python数据类型之集合：集合》。