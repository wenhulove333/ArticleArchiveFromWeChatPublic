#我们来说说Python 第二篇 Python环境搭建#
俗话说”工欲善其事必先利其器“，想要进入Python的世界，Python的解释执行环境是首要的事情。这一篇，我们来说下不同的平台上Python环境的搭建。

我们就从https://www.python.org/downloads/这里开始。

进入到这个页面，大家会发现有两个版本的Python，看过第一篇的小伙伴们应该知道，这两个是分别对应Python2.0和Python3.0的，而我们这个系列是基于Python2.0，后续的话，我们会根据情况来看是否推出Python3.0的系列。

##Windows平台##
这里我们下载最新的Python2.0的Python软件（Python2.7.11）。安装完成后，你开始菜单里面你会看到Python相关的快捷方式，通过这些快捷方式你可以打开Python IDE，命令行模式以及相关帮助文档。

这里有图片

另外，如果你想再windows的命令行模式下，直接执行命令：python --version。这个时候，你需要添加python的安装目录到你的系统路径下面。请参照下面方式。

我们以windows7为例，打开"我的电脑"（computer），在上方你可以看到”系统属性“（System properties），点击打开它，在左侧，你可以看到”高级系统设置“（Advanced system settings），点击打开它，在下方你可以看到”环境变量“（Environment Variables）,点击打开它，你可以看到标签”系统变量“（System variables），在里面找到变量名（Variables Name）为Path的那一项，双击打开它，你可以看到"变量值"（Variable Value），在它的尾部加入你的python安装路径，注意在python路径的前面加上分号（;），用来和之前设置的值分割。大家可以参照下下面图片中的设置，注意红圈里面的分号（;），不要把它漏掉了。

这里有图片。

现在你可以使用python gui或者直接进入命令行执行python命令打开python了。python的交互式的命令执行可以让你快速的调试小段代码。

##Linux平台##
在linux平台上面安装是很容易的一件事情。
在Redhat和CentOS上面，你可以使用yum install python2 和 yum install python2-dev来安装Python运行环境和开发环境。
在Ubuntu上面，你可以使用apt-get install python2.x 和 apt-get install python2.x-dev。
大家经常用的linux系统应该不大会超出这个范畴。

安装完成后，同样运行python进入到交互式命令执行的环境。

这里有图片。

##MAC OS X平台##
MAC上面更加简单，和普通安装程序是一样的，和windows上面一样可以使用GUI和命令行两种模式。

运行环境安装完成后，另外一个关心的就是代码编辑环境了，这里列举几个，大家可以根据喜好去进行选择。
Sublime Text; Eclipse; Notepad++; Vim;emacs

环境就说这么多，具体的用法我们在后面说Python语言的时候会涉猎到。敬请期待《我们来说说Python 第三篇 Python数据类型》。