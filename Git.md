# Git Notes

#### 安装

Git 各平台安装包下载地址为：http://git-scm.com/downloads

#### 用户配置

$ git config --global user.name "rekfan"

$ git config --global user.email macos@rekfan.com

如果用了 --global 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。
如果要在某个特定的项目中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。

#### 编码问题

$ git config --global core.quotepath false          # 显示 status 编码

$ git config --global gui.encoding utf-8            # 图形界面编码

$ git config --global i18n.commit.encoding utf-8    # 提交信息编码

$ git config --global i18n.logoutputencoding utf-8  # 输出 log 编码

#### Git 工作区、暂存区和版本库

* workspace：工作区

* staging area：暂存区/缓存区

* local repository：版本库或本地仓库

* remote repository：远程仓库


![alt git图解](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)

![alt git图解](https://img-blog.csdnimg.cn/2019011421175356.png)

#### 创建仓库

$ git init  使用当前目录作为Git仓库

$ git init <dir>  指定目录作为Git仓库

$ git config --list 显示当前的 git 配置信息

$ git config -e    # 针对当前仓库编辑 git 配置文件

$ git config -e --global   # 针对系统上所有仓库

#### 常用命令
$ git add .  # 添加所有文件到缓存区

$ git add [file1] [file2] ... # 添加一个或多个文件到暂存区

$ git commit -m "message" # 暂存区的目录树写到版本库（对象库）中

$ git commit [file1] [file2] ... -m [message] # 提交暂存区的指定文件到仓库区

注： 在 Linux 系统中，commit 信息使用单引号 '，Windows 系统，commit 信息使用双引号 "

$ git commit -a  # -a 参数设置修改文件后不需要执行 git add 命令，直接来提交

$ git status [-s] # 命令用于查看项目的当前状态,-s 简短

$ git rm --cached <file> # 直接从暂存区删除文件，工作区则不做出改变

$ git checkout . # 用暂存区全部文件替换工作区的文件

$ git checkout -- <file>  # 会用暂存区指定的文件替换工作区的文件

##### reset 
$ git reset HEAD # 命令时，暂存区的目录树会被重写,工作区不受影响

$ git reset HEAD^            # 回退所有内容到上一个版本  

$ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  

$ git  reset  052e           # 回退到指定版本


$ git reset –hard HEAD~3  # 回退上上上一个版本  

$ git reset –hard bae128  # 回退到某个版本回退点之前的所有信息。
 
$ git reset --hard origin/master    # 将本地的状态回退到和远程的一样 

注：--hard 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交

##### rm
$ git rm <file>  # 将文件从暂存区和工作区中删除

$ git rm runoob.txt # 从暂存区和工作区中删除 runoob.txt 文件

$ git rm -f runoob.txt  

注：如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f

$ git rm --cached <file>  # 如果想把文件从暂存区域移除，但仍然希望保留在当前工作目录中

$ git rm –r * # 可以递归删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件

##### mv

$ git mv [file] [newfile] # git mv 命令用于移动或重命名一个文件、目录或软连接

$ git mv -f [file] [newfile]  #如果新但文件名已经存在，但还是要重命名它，可以使用 -f 参数


##### diff

* 尚未缓存的改动：git diff

* 查看已缓存的改动： git diff --cached

* 查看已缓存的与未缓存的所有改动：git diff HEAD

* 显示摘要而非整个 diff：git diff --stat

$ git diff [file]  # 显示暂存区和工作区的差异

$ git diff --cached [file] 或 $ git diff --staged [file]  # 显示暂存区和上一次提交(commit)的差异

$ git diff [first-branch]...[second-branch]  # 显示两次提交之间的差异

#### 日志log

$ git log # 列出历史提交记录

$ git log --oneline # --oneline 选项来查看历史记录的简洁的版本

$ git log --reverse --oneline  # --reverse 参数来逆向显示所有日志

$ git log --author=Linus --oneline -5 # --author查找指定用户的提交日志

$ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges  # 三周前且在四月十八日之后的所有提交 --no-merges 选项以隐藏合并提交

$ git blame README  # 如果要查看指定文件的修改记录可以使用 git blame 命令


#### 远程仓库

$ git clone <repo> # 克隆远程仓库到当前目录

$ git clone <repo> <directory> # 克隆远程仓库到指定目录

$ git remote -v # 显示所有远程仓库

$ git remote show https://github.com/rekfan/Blog  # 显示某个远程仓库的信息

$ git remote add origin git@github.com:tianqixin/runoob-git-test.git # 提交到 Github  origin为本地库 

$ git push -u origin master

$ git remote rm name  # 删除远程仓库

$ git remote rename old_name new_name  # 修改仓库名

$ git pull origin master:brantest # 将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并

$ git push origin master # 将本地的 master 分支推送到 origin 主机的 master 分支

$ git push --force origin master # 本地版本与远程版本有差异，但又要强制推送可以使用 --force 参数

$ git push origin --delete master  # 表示删除 origin 主机的 master 分支

#### 分支管理

$ git branch (branchname) # 创建分支命令

$ git checkout (branchname) # 切换分支命令:

$ git merge # 合并分支命令

$ git branch # 列出分支命令

$ git branch -d (newtest) # 删除分支

#### 标签

$ git tag -a v1.0  # 提交打上（HEAD）"v1.0"的标签

$ git tag -a v0.9 85fc7e7  # 追加标签

$ git tag # 查看标签

$ git tag -a <tagname> -m "runoob.com标签"  # 指定标签信息命令

$ git tag -s <tagname> -m "runoob.com标签"  # PGP签名标签命令

