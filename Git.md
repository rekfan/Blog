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

$ git clone <repo> 克隆远程仓库到当前目录
$ git clone <repo> <directory> 克隆远程仓库到指定目录

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

* 尚未缓存的改动：git diff
* 查看已缓存的改动： git diff --cached
* 查看已缓存的与未缓存的所有改动：git diff HEAD
* 显示摘要而非整个 diff：git diff --stat

$ git status [-s] # 命令用于查看项目的当前状态,-s 简短
$ git reset HEAD # 命令时，暂存区的目录树会被重写,工作区不受影响
$ git rm --cached <file> # 直接从暂存区删除文件，工作区则不做出改变
$ git checkout . # 用暂存区全部文件替换工作区的文件
$ git checkout -- <file>  # 会用暂存区指定的文件替换工作区的文件

