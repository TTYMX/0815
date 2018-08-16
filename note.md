#git常用命令

###需要知道的单词
* repository  仓库
* track 跟踪文件
* storage 暂存
* remote 远程


###创建所需命令
* git init
* git add README.md
* git commit -m "first commit"
* git remote add origin https://github.com/TTYMX/20180815-git-test.git //更改链接远程
* git push -u origin master


###后续改动

* git add 
* git commit -m 
* git push

###查看命令

* git config user.name
* git config user.email
* vim ~/.gitconfig 查看配置文件
* git config --list 查看配置信息
* git config <key> 查看某项配置的信息

###设置命令

所有的操作
* git config --global user.name 'aaa'
* git config --global user.email 'youremail@email,com'
* git config --global push.default

* 一个特定的项目(很少用)
    > 1. git config user.name 'aaa'
    > 2. git config user.email 'email@email.com'

###基本命令

pwd 查看当前所在文件位置
1. 删除本地分支
    > git branch -d <BranchName>
2. 删除远程分支
    > git push origin --delete <BranchName>
3. 查看所有分支
    > git branch -a
4. 克隆代码
    > git clone [url] <br>
    会自动生成.git文件  <br>
    可以自定义仓库的名字 git clone [url] name
5. 查看当前文件的状态
    > git status 

###帮助命令

* git help <verb>config
* git <verb> --version  可以使用git --查看可以看那些命令

##详解命令
* git push origin master 将本地分支的更新推送到远程主机
    > 推送 远程主机 本地master分支 如果远程的master分支不存在创建之<br>
    > 本地分支被省略，表示删除远程分支
    git push origin :master等同于git push origin --delete master<br>
    > 如果本地分支和远程分支存在追踪关系,则本地分支和远程分支都可以省略
    git push origin<br>
    > 如果当前分支只有一个追踪分支，那么主机名也可以省略　git push<br>
    > 如果当前分支和多个主机存在追踪关系，可以用-u选项指定一个默认主机
    　git push -u origin master

* git add 开始跟踪一个文件
    > eg: git add README.md

* git status 查看文件状态
    > git status -s 缩减的展示

* git rm 移出跟踪的文件
    > git rm README.md<br>
    git rm --cached README.md
    
###状态
 
 * ?? 没有追踪的文件
 * A  已经追踪的文件
 * 绿M 已经追踪了没有提交过修改的文件
 * 红M 已经提交了修改的文件
 * 结果为空表示很干净了,全部提交了
 * git diff 本身只显示尚未暂存的改动，而不是自上次提交以来所做的所有改动。 所以有时候你一下子暂存了所有更新过的文件后，运行 git diff 后却什么也没有，就是这个原因。

###远程仓库
* git clone [url]
* git remote 
* git remote -v 显示需要殂谢远程仓库使用的git保存的简写和其对应的url
* git remote add name url 添加远程仓库
* git remote rename name new_name 更改远程仓库的名字 
