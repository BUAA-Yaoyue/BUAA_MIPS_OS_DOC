The Thinking
============
小明的烦恼
-------------
##思考1
  深夜，小明在做操作系统实验。困意一阵阵袭来，小明睡倒在了键盘上
  。等到小明早上醒来的时候，他惊恐地发现，他把一个重要的代码文件printf.c删除掉了。苦恼的小明向你求助，你觉得怎样能帮他把代码文件恢复呢？<br>
###解决方法
    首先，他是更改了工作区的文件，并且没有上传，所以可以直接重新利用
    git checkout print.c
    来恢复print.c文件，因为print.c文件是在OSLAB库里面有存储，所以可以直接得到
##思考2
正在小明苦恼的时候，小红主动请缨帮小明解决问题。小红很爽快地在键盘
上敲下了
git rm printf.c
，这下事情更复杂了，现在你又该如何处理才能弥补
小红的过错呢？
###解决方法
  这次是把暂存区的print.c也给删掉了，这是可以先用
  git reset HEAD print.c
  方法把print.c文件找回到暂存区中，再利用git checkout指令找回
##思考3
处理完代码文件，你正打算去找小明说他的文件已经恢复了，但突然发现小
明的仓库里有一个叫
Tucao.txt
，你好奇地打开一看，发现是吐槽操作系统
实验的，且该文件已经被添加到暂存区了，面对这样的情况，你该如何设置
才能使
Tucao.txt
在不从工作区删除的情况下不会被
git commit
指令提交到
版本库？
###解决方法
  利用git clean Tucao.txt清除了他就可以了

有关克隆问题的思考
-------------------------
##思考1
克隆时所有分支均被克隆，但只有 HEAD 指向的分支被检出。
  正确，克隆时是克隆所以远程仓库中的内容。根据官方文档`Clones a repository into a newly created directory, creates remote-tracking branches for each branch in the cloned repository (visible using git branch -r), and creates and checks out an initial branch that is forked from the cloned repository’s currently active branch.`这句话中第一句就可以得知克隆时克隆所以仓库中的内容
##思考2
  克隆出的工作区中执行 git log、git status、git checkout、git commit 等操作 不会去访问远程版本库。
  正确，在实验中我们不难发现，在我们提交作业时，`git add`和`git commit`操作执行后并没有直接的得到实验结果，而是提示我们有文件进行了更改，
  之后执行`git push`操作后得出结果，可以得知此时远程版本库被更改。
##思考3
  克隆时只有远程版本库 HEAD 指向的分支被克隆。
  错误，正确的应该是所有分支被克隆，但只有HEAD分支被检出。理由在第一题中有所叙述。
##思考4
  克隆后工作区的默认分支处于 master 分支。
  正确。在我们进行试验时，工作区默认确实在master分支中，同时官方文档中也给出了类似的描述` creates and checks out an initial branch that is forked from the cloned repository’s currently active branch.`这句话中的`initial branch`默认应该为master分支

