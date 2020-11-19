## Git study notes
[廖雪峰的教程](https://www.liaoxuefeng.com/wiki/896043488029600)    
[learn git branch](https://learngitbranching.js.org/?locale=zh_CN)    
[指令速查表](https://www.cnblogs.com/kenshinobiy/p/4543976.html)    
[github官方文档](https://docs.github.com/cn/free-pro-team@latest/github/using-git/managing-remote-repositories)
## Basic command lists


### 一些操作
```
git clone git@github.com:LearningGit.git
git checkout -b dev
vi text.txt
git status
git add text.txt
git status
git commit -m "add text file"
git push origin dev (dev下执行,名字要对应)
git checkout master 
git diff master dev
git diff master origin/dev
git merge dev (git merge origin/dev)
git diff master dev
git branch 
git branch -r 
git branch -a
git checkout -d dev
git push origin --delete dev
git branch -a 
```

### 0.两种远程URL
> https  

> ssh 

[ssh](https://docs.github.com/cn/free-pro-team@latest/github/using-git/which-remote-url-should-i-use)要求必须在计算机上生成 SSH 密钥对，并将公钥添加到的 GitHub 帐户


### 1.创建版本库
> `git clone git@github.com:GitZzw/LearningGit.git`  克隆远程版本库(master分支)

##### 克隆版本库指定分支：
方法1：
`git branch -a` 列出远程和本地所有分支
`git checkout -b dev origin/dev`  
checkout远程的dev分支，在本地起名为dev分支，并切换到本地的dev分支

方法2：
> git clone -b branchname https://github.com/GitZzw/LearningGit.git   

> 
```
mkdir DirName
cd DirName
git init
```                                     
初始化本地版本库

### 2.修改和提交
> `git status`     查看状态 

> `git diff`       查看变更内容  


![1090617-20181008211557402-232838726.png](https://i.loli.net/2020/11/05/KVDNvpd6TfaJhEi.png)


```
git diff：比较工作区与暂存区

git diff --cached 或 git diff --staged：比较暂存区和本地分支的最近一次commit(本地版本库)

git diff HEAD：显示工作目录(已track但未add文件)和暂存区(已add但未commit文件)与最后一次commit之间的的所有不相同文件的增删改。

git diff HEAD~X或git diff HEAD^^^…(后面有X个^符号，X为正整数):可以查看最近一次提交的版本与往过去时间线前数X个的版本之间的所有同(3)中定义文件之间的增删改。

git diff <分支名1> <分支名2> ：比较两个分支上最后 commit 的内容的差别

git diff branch1 branch2 --stat    显示出所有有差异的文件(不详细,没有对比内容)

git diff branch1 branch2              显示出所有有差异的文件的详细差异(更详细)

git diff origin/master master
```

> `git add .`      跟踪所有改动过的文件 

> `git add file`   跟踪指定的文件 

> `git mv old new` 文件改名 

> `git rm file`    删除文件或者用本地命令行的操作再更新 

> `git rm --cached file`  停止跟踪文件但不删除 

> `git commit -m "commit message"` 提交所有更新过的文件 


### 3.查看提交历史
> `git log`        查看所有提交历史 

> `git log -p file`  查看指定文件提交历史 

> `git blame file`   以列表方式查看指定文件提交历史 

### 4.撤销
> `git reset --hard HEAD` 撤销工作目录中所有未提交文件的修改内容 

> `git checkout HEAD file` 撤销指定未提交文件的修改内容 

> `git revert <commit>`   撤销指定的提交 


### 5.分支与标签
> `git branch`  显示所有本地分支 

> `git checkout <branch/tag>`  切换到指定分支或标签 

> `git checkout -b newbranch`    创建新分支 

> `git branch -d branchname`  删除分支 

> `git tag`     列出所有本地标签 

> `git tag tagname` 基于最新提交创建标签 

> `git tag -d tagname` 删除标签 

### 6.合并与衍合
> `git merge branchname` 合并指定分支到当前分支 

> `git rebase branchname` 衍合指定分支到当前分支 

 

### 7.远程操作
> `git remote -v`   查看远程版本库信息 

> `git remote show <remotename>`   查看指定远程库信息 

> `git remote add <remote> <url>`  添加远程版本库 

> `git fetch <remote>`    从远程库获取代码 

> `git pull <remote> <branch>`   下载代码以及快速合并

> `git pull origin branch` pull指定origin的dev分支到当前目录

> `git push origin dev`  push当前分支到origin的dev分支下

> `git push <remote> <branch>`   上传代码以及快速合并 


删除本地分支：git branch -d 分支名称

强制删除本地分支：git branch -D 分支名称

删除远程分支：git push origin --delete 分支名称


## git常用命令速查
```
git branch 查看本地所有分支
git status 查看当前状态
git commit 提交
git branch -a 查看所有的分支
git branch -r 查看远程所有分支
git commit -am "init" 提交并且加注释
git remote add origin git@192.168.1.119:ndshow
git push origin master 将文件给推到服务器上
git remote show origin 显示远程库origin里的资源
git push origin master:develop
git push origin master:hb-dev 将本地库与服务器上的库进行关联
git checkout --track origin/dev 切换到远程dev分支
git branch -D master develop 删除本地库develop
git checkout -b dev 建立一个新的本地分支dev
git merge origin/dev 将分支dev与当前分支进行合并
git checkout dev 切换到本地dev分支
git remote show 查看远程库
git add .
git rm 文件名(包括路径) 从git中删除指定文件
git clone git://github.com/schacon/grit.git 从服务器上将代码给拉下来
git config --list 看所有用户
git ls-files 看已经被提交的
git rm [file name] 删除一个文件
git commit -a 提交当前repos的所有的改变
git add [file name] 添加一个文件到git index
git commit -v 当你用－v参数的时候可以看commit的差异
git commit -m "This is the message describing the commit" 添加commit信息
git commit -a -a是代表add，把所有的change加到git index里然后再commit
git commit -a -v 一般提交命令
git log 看你commit的日志
git diff 查看尚未暂存的更新
git rm a.a 移除文件(从暂存区和工作区中删除)
git rm --cached a.a 移除文件(只从暂存区中删除)
git commit -m "remove" 移除文件(从Git中删除)
git rm -f a.a 强行移除修改后文件(从暂存区和工作区中删除)
git diff --cached 或 $ git diff --staged 查看尚未提交的更新
git stash push 将文件给push到一个临时空间中
git stash pop 将文件从临时空间pop下来
---------------------------------------------------------
git remote add origin git@github.com:username/Hello-World.git
git push origin master 将本地项目给提交到服务器中
-----------------------------------------------------------
git pull 本地与服务器端同步
-----------------------------------------------------------------
git push (远程仓库名) (分支名) 将本地分支推送到服务器上去。
git push origin serverfix:awesomebranch
------------------------------------------------------------------
git fetch 相当于是从远程获取最新版本到本地，不会自动merge
git commit -a -m "log_message" (-a是提交所有改动，-m是加入log信息) 本地修改同步至服务器端 ：
git branch branch_0.1 master 从主分支master创建branch_0.1分支
git branch -m branch_0.1 branch_1.0 将branch_0.1重命名为branch_1.0
git checkout branch_1.0/master 切换到branch_1.0/master分支
du -hs

git branch 
删除远程branch：git push origin :branch_remote_name
git branch -r -d branch_remote_name
-----------------------------------------------------------

初始化版本库，并提交到远程服务器端
mkdir WebApp
cd WebApp
git init 本地初始化
touch README
git add README 添加文件
git commit -m 'first commit'
git remote add origin git@github.com:daixu/WebApp.git
git remote rm origin  取消绑定
```


