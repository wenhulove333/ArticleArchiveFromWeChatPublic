#Git命令#
有了绝世宝刀、上古神器，没有足够的能力驾驭的话，是无法发挥出它的神奇力量的。小伙伴们，为了不要让Git在寂寥的角落里黯然神伤，就跟随我们的Git系列Get Git绝学去驾驭Git，走上软件之巅吧。在这一篇中，我们会把Git常用的口诀罗列出来。
##建立Git仓库##
如同上古神器需要饮血开封，Git也需要初始化Git仓库才能进行后续有效的管理。我们可以通过两种方式初始化Git仓库。
 
第一种，在需要进行管理的项目所在的目录，执行：
> D:\xxxxxx\xxxxxx\1701\GitRepositoryModel>**git init**

>Initialized empty Git repository in D:/xxxxxx/xxxxxx/1701/GitRepository
Model/.git/

第二种，从已有的项目仓库复制一份，执行：
> D:\xxxxxx\xxxxxx\1701>**git clone https://github.com/wenhulove333/CCBI2CCB.git**
>
> Cloning into 'CCBI2CCB'...
> 
> remote: Counting objects: 59, done.
> 
> remote: Compressing objects: 100% (42/42), done.
> 
>remote: Total 59 (delta 19), reused 55 (delta 15), pack-reused 0
>
>Unpacking objects: 100% (59/59), done.
>
>Checking connectivity... done.

对于第二种，这里稍微啰嗦一点，在没有指定目录的情况下，执行clone命令会在当前目录生成以Git仓库名作为目录名的目录（这里就是CCBI2CCB），如果你不想使用默认的目录名，可以通过在命令最后加入自己喜欢的目录名，像这样`git clone https://github.com/wenhulove333/CCBI2CCB.git 任性 `。 另外，对于Git Clone的时候使用的传输协议，我们后续会有相应的文章介绍，这里就不展开了。
##操作和查看文件状态##
不知道大家对我们的Git系列《我们来说说Git 第二篇 Git基础》是不是还记忆犹新，如果你是第一次学习Git或者早已狠心的忘记了当时和第二篇甜蜜的约会的话，那就重新燃烧激情，再来一次吧（通过微信订阅号里面的查看历史消息，可以看到我们之前的文章）。下面我们列出三种文件状态，是不是很熟悉的感觉：
- 已提交（committed）
- 已修改（modified）
- 已暂存（staged）
###查看文件状态###
我们想要知道当前仓库里面文件的状态，执行：
> D:\xxxxxx\xxxxxx\1701\GitRepositoryModel>**git status**
>
> On branch master
>
> Initial commit
> 
> nothing to commit (create/copy files and use "git add" to track)

上述输出信息说明，当前项目目录下面没有处于已修改或已暂存的文件，所有文件都处于已提交状态。
下面我们一点一点的去展现文件的不同状态和对应的Git命令。
###添加或修改文件###
增加一个新文件add.txt，再次查看文件状态，执行：
> D:\xxxxxx\xxxxxx\1701\GitRepositoryModel>**git status**
>
> On branch master
>
> Initial commit
>
> Untracked files:
>  (use "git add <file>..." to include in what will be committed)

>        add.txt

> nothing added to commit but untracked files present (use "git add" to track)

上述信息说明，add.txt处于未被跟踪的状态，也就是我们所说的三种状态中的第一个：已修改。

###暂存文件###
我们想要跟踪文件的添加或修改，执行：
> git add add.txt

再次查看文件状态，执行：
> D:\xxxxxx\xxxxxx\1701\GitRepositoryModel>**git status**
>
> On branch master
>
> Initial commit
>
> Changes to be committed:
>  (use "git rm --cached <file>..." to unstage)
>
>        new file:   add.txt

上述信息说明，add.txt处于跟踪的状态，也就是我们所说的三种状态中的第二个：已暂存。

这里我们继续啰唆一点，一旦文件被暂存，Git就会对其做一个快照，并且对其算出一个SHA-1哈希值。当然，这个时候你是可以修改文件状态到已修改状态的（上述输出信息中的git rm --cached <file>...）。这里我们先不说这种状态的切换，我们先一路走到Commit。

###提交文件###
对文件进行暂存之后，此时还没有真正记录到仓库。
我们想要提交暂存到仓库，执行：
> D:\xxxxxx\xxxxxx\1701\GitRepositoryModel>**git commit**

添加一些信息来说明你这次提交的目的和原因，然后提交。
> [master (root-commit) c45ccb7] Commit example
>
> 1 file changed, 1 insertion(+)
>
> create mode 100644 add.txt

再次查看文件状态，执行：
> D:\xxxxxx\xxxxxx\1701\GitRepositoryModel>**git status**
> 
> On branch master
> 
> nothing to commit, working directory clean

Bingo! 我们现在已经把所有的控制文件状态的命令都展现出来了，一切都是这么完美和谐。然并卵，让我们期待《我们来说说Git 第五篇 Git混战》