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


###恢复文件内容
* git checkout filename 恢复文件到上传时候的内容

###分支的处理
* git branch 查看分支 
* git branch -a 查看所有的分支 包括远程分支
* git branch name 创建分支
* git checkout branch_name 切换分支的名字
* git branch -D branch_name 删除分支
* git branch -m name new_name 重命名分支

###checkout的应用
* git checkout filename 恢复到提交的版本
* git checkout filename 如果本地删除,没有添加,可以恢复出来
* 文件名字前面显示D表示删除的文件

###删除分段区域的更改
* 当执行添加操作的时候,文件将从本地存储库移动到暂存区,如果用户意外修改的文件提交到了暂存区则可以使用git checkout命令恢复其修改

* 在git中,有一个HEAD指针重视指向最新的提交.如果要从分段区域中撤销更改,则可以使用git checkout 命令, 必须提供一个附加参数, 即HEAD指针. 
附加的提交指针参数指示git checkout命令重置工作树,并删除分段更改

* __<font color=#ff0000 size=7 face="黑体">已经git add 的如果想要撤销更改,可以使用 git checkout -- filename 会撤销提交的变化,本地的也会删除</font>__

###用git复位移动头指针
* 经过少量更改后, 可以决定删除这些改动. git reset命令可以用于复位或恢复更改. 我们可以执行三种不同类型的复位操作
* --soft选项 每个分支都有一个HEAD指针,他指向最新的提交,如果用--soft选项后跟提交ID的 git reset命令,那么它将重置HEAD指针提交的ID, 
可以使用git log -1命令验证它
