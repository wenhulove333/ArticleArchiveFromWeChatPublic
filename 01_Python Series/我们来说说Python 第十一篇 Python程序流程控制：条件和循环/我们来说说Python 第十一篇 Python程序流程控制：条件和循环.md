#我们来说说Python 第十一篇 Python程序流程控制：条件和循环#
这一篇我们要说的内容对于一个有着编程经验的小伙伴来说是很简单的，每一种编程语言都少不了流程的控制，要么是显示的，要么是隐式的。下面我们就一一道来。

###if###
**语法**
	
	if expression:
		expr_true_suite

其中expression部分可以使用布尔操作符and、or和not实现多重条件判断或否定条件判断。

	if not handsome and (money <= 0):
		print "Warning: loser"

如果expr_true_suite是单一的语句，我们可以写在同一行上面，当然，这种方式是不推荐的。

###else###
**语法**
	
	if expression:
		expr_true_suite
	else:
		expr_false_suite

说到else的时候，我们说一个关于"dangling else"的一个问题，这个问题是由于语义导致的，在python不存在这个问题，原因就是因为python使用缩进而不是大括号标记代码块边界。这个问题在C代码里面比较常见，大家有兴趣的话可以自行百度下了解一下。

###elif###
**语法**
	
	if expression1:
		expr1_true_suite
	elif expression2:
		expr2_true_suite
			:
	elif expressionN:
		exprN_true_suite
	else:
		expr_false_suite

###条件表达式（三元操作符）###
在Python2.5之前是没有三元操作符的，在2.5之前，Python程序员使用了一种很酷的方法。

	>>> x = 10
	>>> y = 100
	>>> smaller = (x < y and [x] or [y])[0]
	>>> smaller
	10

在Python2.5和更新的版本中，你就可以使用我们眼中的条件表达式了。

	>>> x = 10
	>>> y = 100
	>>> smaller = x if x < y else y
	>>> smaller
	10

###while###
**语法**

	while expression:
		suite_to_repeat

其中expression部分和if里面的一样，你可以使用布尔操作符去实现多重判断条件或否定判断条件。

	>>> count = 0
	>>> while (count < 9):
		print 'the index is: ', count
		count += 1
	
		
	the index is:  0
	the index is:  1
	the index is:  2
	the index is:  3
	the index is:  4
	the index is:  5
	the index is:  6
	the index is:  7
	the index is:  8

###for###
python里面的for和我们常见的for还是有些差别的，它更像Java里面的foreach。

**语法**
	
	for iter_var in iterable:
		suite_to_repeat

for循环会访问一个可迭代对象（序列或迭代器）中的所有元素。

	>>> for eachLetter in 'Hello':
		print 'current letter: ', eachLetter
	
		
	current letter:  H
	current letter:  e
	current letter:  l
	current letter:  l
	current letter:  o

###break###
结束当前循环跳转到循环流程的下条语句，用在while和for循环。

	>>> count = 0
	>>> while (count < 9):
			print 'the index is: ', count
			count += 1
			if (count == 6):
				break
	
		
	the index is:  0
	the index is:  1
	the index is:  2
	the index is:  3
	the index is:  4
	the index is:  5

###continue###
终止当前循环，然后判断循环的条件是否成立（while）或判断是否还存在迭代元素（for），以此决定是否进行下一个循环处理。

	>>> count = 0
	>>> while (count < 9):
			count += 1
			if (count == 6):
				continue
			print 'the index is: ', count

	the index is:  1
	the index is:  2
	the index is:  3
	the index is:  4
	the index is:  5
	the index is:  7
	the index is:  8
	the index is:  9

###pass###
用来表示这里不做任何事情，可以用于表示这里有待后续完成。

###else###
说完了while和for，我们再来说下else用于while和for循环里面的情形。

else用于while和for循环，else后面的子句只有在循环完成的情况下才会执行，如果循环里面使用了break语句的话，将会跳过else后面的子句。
	
	>>> count = 0
	>>> while (count < 9):
			count += 1
			if (count == 6):
				continue
			print 'the index is: ', count
		else:
			print 'while is finished, the index is: ', count
	
		
	the index is:  1
	the index is:  2
	the index is:  3
	the index is:  4
	the index is:  5
	the index is:  7
	the index is:  8
	the index is:  9
	while is finished, the index is:  9

	>>> count = 0
	>>> while (count < 9):
			count += 1
			if (count == 6):
				break
			print 'the index is: ', count
		else:
			print 'while is finished, the index is: ', count
	
		
	the index is:  1
	the index is:  2
	the index is:  3
	the index is:  4
	the index is:  5

###列表解析###
这个是个高级玩意，来自函数式编程语言Haskell，是一个非常有用、简单而且灵活的工具，可以用来动态的创建列表。

**语法**

	[expr for iter_var in iterable]
	[expr for iter_var in iterable if cond_expr]

举几个例子

	>>> [(x+1, y+1) for x in range(3) for y in range(5)]
	[(1, 1), (1, 2), (1, 3), (1, 4), (1, 5), (2, 1), (2, 2), (2, 3), (2, 4), (2, 5), (3, 1), (3, 2), (3, 3), (3, 4), (3, 5)]

###生成器表达式###
它是列表解析的一个扩展。我们知道列表解析需要把所有的数据生成出来放在内存里面，这个对于大量数据处理的程序而言是不好的。而生成器表达式不是真正的去创建列表，而是返回一个生成器，每次去计算一个条目出来。

**语法**

	(expr for iter_var in iterable）
	(expr for iter_var in iterable if cond_expr)

下面举一个例子：寻找文件中最长的行。

	max(len(x.strip()) for x in open('/etc/motd'))

一句话搞定，并且对于大文件也是没有问题的，如果我们使用列表解析的话，对于大文件处理的话，就会存在一定的问题。

这一篇的内容除了列表解析和生成器表达式，其他的都很简单。敬请期待《我们来说说Python 第十二篇 Python文件处理》。