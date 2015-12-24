#Git安装#
自古宝刀配英雄，红粉送佳人，Git送码农，咳咳！程序猿真的不能随便吟诗。还是来一个豪言壮语开始我们今天的主题吧：Git在手，天下我有。 是不是心中已经豪情万丈，有一种站在金子塔尖的微妙感觉。哎，哥们，醒醒，先让我们列举下我们常用的用来做开发工作的操作系统吧。Windows相信80%人的青春都倾注在它上面，Linux开源世界的神级产物（越来越多的人就这么义无反顾的喜欢上了它），MAC OS X高（jiu）大（zhe）上（yang）感觉用它写代码都自带框架。好了，让我们一一看下在这些操作系统上面怎么安装Git。
##Windows#
我们先到http://git-scm.com/download/win这个地址上面下载Git，根据你的操作系统是32位还是64位的下载不同的版本，下完之后呢，开始我们的安装过程。下面，关键点来了，关键点来了，关键点来了，重要的事情说三遍。
身为一名专业的软件攻城狮，我们知道，虽然都是换行，但是Windows和Linux背后对应的编码确是不一样的，这里我们建议在安装的时候使用下面这张图里面的设置。当然，如果你充满了对知识的无尽渴望和追求，你可以每个选项都装一遍，玩坏Git安装。
##Linux##
Linux上面安装Git是一件非常非常简单的事情。只需要进入到shell，根据你所使用的Linux系统，输入下面的命令即可。

Debian/Ubuntu
>$ apt-get install git**

Fedora/Redhat/CentOS
>$ yum install git

Gentoo
> $ emerge --ask --verbose dev-vcs/git

Arch Linux
>$ pacman -S git

openSUSE
>$ zypper install git

FreeBSD
>$ cd /usr/ports/devel/git
>$ make install

Solaris 11 Express
>$ pkg install developer/versioning/git

OpenBSD
>$ pkg_add git

是不是很简单，是不是立马喜欢上了Linux。
##MAC OS X##
我们先到http://git-scm.com/download/mac这个地址上面下载Git. MAC上面的安装同样是非常简单。双击安装，根据提示来就OK了。有的时候，高大上的东西就是这么简单粗暴，有钱就是任性。

现在我们神兵Git在手，是时候召集小伙伴一起扫码江湖了。后面我们会一一奉上闯荡江湖的各种武林绝学。敬请期待纯正干货《我们来说说Git 第四篇 Git命令》