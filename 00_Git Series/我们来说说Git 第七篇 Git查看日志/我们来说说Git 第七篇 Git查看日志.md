#我们来说说Git 第七篇 Git查看日志#
有的是不是还是向回顾下光荣岁月，无论前面经历的是苦难还是幸福，最后回味起来留下的肯定都是幸福的味道。好了，就让我们一起来回顾下青葱岁月吧。
下面我们就从简到繁一一道来。
##git log##
默认不加任何参数的话，git log会按照提交时间列出所有的更新。

	192:02_ArticleArchiveFromWeChatPublic xxxxxxxx$ git log
	commit 937963c441ab273de7188d5c16770a7b5b76349c
	Author: xxxxxxxx <xxxxxxxx@163.com>
	Date:   Tue Jan 5 19:37:13 2016 +0800
	
		Git 第6篇
	
	commit e1f746243b1e02d541bf63ab7b56ab34f1d2403f
	Author: xxxxxxxxx <xxxxxxxxx@163.com>
	Date:   Tue Jan 5 18:48:08 2016 +0800
	
		Rename the directory of Git混战

	commit 672e53054b0ada9d73f7416d924325cb089c86dd
	Author: xxxxxxxxx <xxxxxxxxx@163.com>
	Date:   Tue Jan 5 18:45:09 2016 +0800
	
		Git  第五篇上传

	commit f2f618983c2d22eb8179aca13de7ddf3bb0c87d0
	Merge: 6a7b14c 1cda24f
	Author: xxxxxxxxx <xxxxxxxxx@163.com>
	Date:   Sun Jan 3 20:17:24 2016 +0800
	
		Merge branch 'master' of https://github.com/xxxxxxxxx/ArticleArchiveFromWeChatPublic

	commit 6a7b14c8aa94b1fed9a9c20981feb3e215cc7f5d
	Author: xxxxxxxxx <xxxxxxxxx@163.com>
	Date:   Sun Jan 3 20:12:56 2016 +0800
	
		Update Git 第四篇

	commit 1cda24fc36770b9513dd586f5378e3f97afa0601
	Author: xxxxxxxxx <xxxxxxxxx@163.com>
	Date:   Thu Dec 24 14:20:09 2015 +0800
	
		Create README.md

	commit 1133cdb3fc0e436cd4b46fafdf8f1c9c6d2503a0
	Author: xxxxxxxxx <xxxxxxxxx@163.com>
	Date:   Thu Dec 24 14:18:25 2015 +0800
	
		Initial Project

通过上面，我们可以看到，每一次更新包含SHA-1校验和、作者的名字、电子邮件和提交日期，最后缩进表示提交说明。

##git log -p -2##
－p这个选项用来现实每次提交的内容差异，关于内容差异报告怎么看，我们再上一篇给出了详细的说明；－2表示最近的两次更新。

	192:02_ArticleArchiveFromWeChatPublic xxxxxxxx$ git log -p -1
	commit 7dc49ccec3ba8c6415962acbedd27b8f88211472
	Author: Xxxxxxxx <xxxxxxxx@192.168.0.44>
	Date:   Wed Jan 6 21:44:21 2016 +0800
	
		Only for illustration

	diff --git a/README.md b/README.md
	index 72dae23..9fa465a 100644
	--- a/README.md
	+++ b/README.md
	@@ -1 +1,2 @@
	# ArticleArchiveFromWeChatPublic
	+Add additional information as example for showing log

通过上面，我们可以看到，比单独使用git log多出了内容差异报告

##git log --stat##
有的时候我们需要快速浏览其他人的更新，我们就可以使用--stat这个选项。

	192:02_ArticleArchiveFromWeChatPublic xxxxxxxx$ git log --stat -2
	commit 7dc49ccec3ba8c6415962acbedd27b8f88211472
	Author: Xxxxxxxx <xxxxxxxx@192.168.0.44>
	Date:   Wed Jan 6 21:44:21 2016 +0800
	
		Only for illustration

	README.md | 1 +
	1 file changed, 1 insertion(+)

	commit 937963c441ab273de7188d5c16770a7b5b76349c
	Author: xxxxxxxx <xxxxxxxx@163.com>
	Date:   Tue Jan 5 19:37:13 2016 +0800
	
		Git 第6篇

	...7\264\350\257\264Git \347\254\254\345\205\255\347\257\207 Git\344\271\213\346\226\207\344\273\266\346\257\224\350\276\203.md" | 127 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	1 file changed, 127 insertions(+)

通过上面，我们可以快速的知道文件的变更和变更的行数。

上面都是默认的显示格式，下面的命令可以让我们自由灵活的定义显示的东西,如果我们后续需要自动分析日志的话，都非常方便。定义好你的规则就好了。
##git log --pretty=format:""##
format的格式大家可以使用git help log去查看，这里就不详细说明了。只是简单的举个例子。

	192:02_ArticleArchiveFromWeChatPublic xxxxxxxx$ git log --pretty=format:"%h %s"
	7dc49cc Only for illustration
	937963c Git 第6篇
	e1f7462 Rename the directory of Git混战
	672e530 Git  第五篇上传
	f2f6189 Merge branch 'master' of https://github.com/xxxxxxxx/ArticleArchiveFromWeChatPublic
	6a7b14c Update Git 第四篇
	1cda24f Create README.md
	1133cdb Initial Project

我们自定义只要显示校验码和提交说明。

##git log --graph##
有的时候我们想要分支间的关系，我们可以使用--graph，它使用ASCII字符串表示的简单图形，让我们可以一目了然的看到分支之间的衍生关系。

	192:02_ArticleArchiveFromWeChatPublic xxxxxxxx$ git log --graph
	* commit 7dc49ccec3ba8c6415962acbedd27b8f88211472
	| Author: Xxxxxxxx <xxxxxxxx@192.168.0.44>
	| Date:   Wed Jan 6 21:44:21 2016 +0800
	| 
	|     Only for illustration
	|  
	* commit 937963c441ab273de7188d5c16770a7b5b76349c
	| Author: xxxxxxxx <xxxxxxxx@163.com>
	| Date:   Tue Jan 5 19:37:13 2016 +0800
	| 
	|     Git 第6篇
	|  
	* commit e1f746243b1e02d541bf63ab7b56ab34f1d2403f
	| Author: xxxxxxxx <xxxxxxxx@163.com>
	| Date:   Tue Jan 5 18:48:08 2016 +0800
	| 
	|     Rename the directory of Git混战
	|  
	* commit 672e53054b0ada9d73f7416d924325cb089c86dd
	| Author: xxxxxxxx <xxxxxxxx@163.com>
	| Date:   Tue Jan 5 18:45:09 2016 +0800
	| 
	|     Git  第五篇上传
	|    
	*   commit f2f618983c2d22eb8179aca13de7ddf3bb0c87d0
	|\  Merge: 6a7b14c 1cda24f
	| | Author: xxxxxxxx <xxxxxxxx@163.com>
	| | Date:   Sun Jan 3 20:17:24 2016 +0800
	| | 
	| |     Merge branch 'master' of https://github.com/xxxxxxxx/ArticleArchiveFromWeChatPublic
	| |   
	| * commit 1cda24fc36770b9513dd586f5378e3f97afa0601
	| | Author: xxxxxxxx <xxxxxxxx@163.com>
	| | Date:   Thu Dec 24 14:20:09 2015 +0800
	| | 
	| |     Create README.md
	| |   
	* | commit 6a7b14c8aa94b1fed9a9c20981feb3e215cc7f5d
	|/  Author: xxxxxxxx <xxxxxxxx@163.com>
	|   Date:   Sun Jan 3 20:12:56 2016 +0800
	|   
	|       Update Git 第四篇
	|  
	* commit 1133cdb3fc0e436cd4b46fafdf8f1c9c6d2503a0
	Author: xxxxxxxx <xxxxxxxx@163.com>
	Date:   Thu Dec 24 14:18:25 2015 +0800
	
		Initial Project

通过上面我们可以看到，中间出现一次分支，后续进行了分支到主线的合并操作。

下面，我们看下如何根据各种不同的条件来筛选想要的日志。

##日志筛选##
git log --since=
git log --until=
git log --author=
git log --grep=
git log --before=
git log --after=
git log --committer=
这些就不再详细说明，用法相对简单。通过上面的命令组合可以完成更复杂的筛选操作。同样举个例子。

	192:02_ArticleArchiveFromWeChatPublic xxxxxxxx$ git log --after="2016-01-02" --until="2016-01-04"
	commit f2f618983c2d22eb8179aca13de7ddf3bb0c87d0
	Merge: 6a7b14c 1cda24f
	Author: xxxxxxxx <xxxxxxxx@163.com>
	Date:   Sun Jan 3 20:17:24 2016 +0800
	
		Merge branch 'master' of https://github.com/xxxxxxxx/ArticleArchiveFromWeChatPublic

	commit 6a7b14c8aa94b1fed9a9c20981feb3e215cc7f5d
	Author: xxxxxxxx <xxxxxxxx@163.com>
	Date:   Sun Jan 3 20:12:56 2016 +0800
	
		Update Git 第四篇

到这里，Git的基本命令和一些高阶的用法已经覆盖的差不多了。下面，我们就进行到分支管理的部分。敬请期待《我们来说说Git 第八篇 Git分支》。
