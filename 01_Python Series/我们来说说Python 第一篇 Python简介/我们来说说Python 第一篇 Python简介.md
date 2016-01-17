#我们来说说Python 第一篇 Python简介#
在我们工作的时候学习一门语言，对于大多数人来说都是工作的需要。但是呢，对于充满探索欲望的IT从业者来说，有时也不仅仅工作的需要，而是想把它作为工作的加速剂。比如：想要快速的验证自己的设计、想要对自己编写的模块快速的进行黑盒测试等，总之，你想要快速的干一件事情的话，python会是一个不错的选择。那为什么这么说呢？下面一一道来。

##Python发展历史##
说到 Python的历史，我们就不得不说到Python的作者，Guido von Rossum，这家伙是荷兰人。

**1982年**，Guido从阿姆斯特大学（University of Amsterdam）获得了数学和计算机硕士学位。这个家伙尽管获得了数学的硕士学位，但是呢他总趋向于做计算机相关的工作，并热衷于任何和编程相关的事情。

在那个时候，Guido接触并使用过诸如Pascal、C、Fortran等语言。在80年代的时候，语言设计的基本原则就是让机器能更快运行程序，这主要是因为当时的主机的CPU主频和RAM都很小，比如早期的Macintosh，只有8MHZ的CPU主频和128KB的RAM。当时，有人甚至认为C语言的指针都是在浪费内存，像现在的动态类型，内存自动管理、面向对象，想都不要想了。

然而，这种思考方式让Guido感到很苦恼。因为他知道用C语言去实现一个功能会消耗大量的时间，即使在已经知道如何实现的情况下亦是如此。当时，有一个选择是shell，shell就像胶水一样，把unix的很多功能连接在一起。但是shell本质就是调用已有的命令，和编程语言还是差很多的。

Guido当时就想，如果有一种语言，即能像C语言那样，全面调用计算机的功能接口，又可以像shell那样，可以轻松的编程。当时，有个ABC语言，这个语言让Guido看到了希望。ABC是由荷兰的CWI（Centrum Wiskunde & Informatica, 数学和计算机研究所）开发的。Guido在CWI工作，并参与ABC的开发，当时ABC是以教学为目的的。ABC语言希望让语言变的容易阅读，容易使用，容易记忆，容易学习，来激发人们学习编程的兴趣。

ABC语言最终没有流行起来，一个原因是ABC语言编译器需要高配置的电脑才能远行；另外一个原因就是ABC语言的设置存在一些致命的缺陷：可扩展性差（不是模块化语言）、不能直接进行IO、过度革新（不符合程序员的思维方式）、传播困难。

**1989年**，Guido开始写Python语言的编译/解释器。Python来自Guido所挚爱的电视剧Monty Python's Flying Circus（BBC1960-1970年代播放的室内情景幽默剧，以当时的英国生活为素材）。他希望通过这个可以实现他的理念（**一种C和shell之间，功能全面，易学易用，可扩展的语言**）。

**1991年**，第一个Python编译器（同时也是解释器）诞生。它是用C语言实现，并能调用C库（.so文件）。从一出生，Python就已经具有了：类（class，函数(function)，异常处理（exception），包括表（list）和词典（dictionary）在内的核心数据类型，以及模块（module）为基础的扩展系统。

Python语法很多来自C，但又受到ABC语言的强烈影响。来自ABC语言的一些规定直到今天还富有争议，比如强制缩进。当然，Python聪明的选择一些C语言的惯例，对于学习者来说是个好事情。

Python从一开始就特别在意可扩展性（extensibility）。Python可以在多个层次上进行扩展，高层使用py，底层使用C库。

不得不说，此时的Python的运气确实比ABC语言要好很多，因为这个时候计算机性能有了很大程度的提高，软件世界的思维角度也随之发生了很大的变化，C++和Java的流行就是一个很好的例证。除此之外，就是Internet的悄然升起，促使了新的软件开发模式：开源的流行。Linux就是一个很好的例证。

有了天时地利人和，很多人就转向了Python。当时Guido维护了一个maillist，Python用户通过邮件进行交流。Ptyon的用户来自许多领域，有着不同的背景，对Python有着不同的需求。由于Python相当的开放，用户很容易对其进行扩展。最终，用户会把改动发给Guido，由他决定是否加入到Python或者标准库中。

Python被称为“Battery Included”，意思就是它以及其标准库的强大。Python的开发者来自不同领域，他们将不同领域的有点带给Python。比如Python标准库中的正则表达式（regular expression）是参考perl，而lambda, map, filter, reduce函数参考lisp。当然，Python大部分的标准来自于社区。Python的社区不断壮大，进而拥有了自己的newsgroup，网站（python.org），以及基金（Python Software Foundation）。从Python2.0开始Python的开发模式转为完全的开源方式，python获得了更加快速的发展。

**到现在**，Python的框架已经基本确立。Python语言以对象为核心组织代码（Everything is object），支持多种编程范式（multi-paradigm），采用动态类型（dynamic typing），自动进行内存回收（garbage collection）。Python支持解释运行（interpret），并能调用C库进行扩展。Python有强大的标准库（Battery Included）。由于标准库的体系已经稳定，所以Python的生态系统开始扩展到第三方包。

**今天**，Python已经进入了3.0的时代，由于Python3.0向后不兼容，所以从Python2.0过渡到Python3.0是一件不容易的事情。不管怎么说，Python依然是一个在发展中的语言，魅力无穷。

看到Python的发展历程，如果你也有当时Guido的困惑，我想你可以考虑用Python为你排忧解难。敬请期待《我们来说说Python 第二篇 Python环境搭建》
