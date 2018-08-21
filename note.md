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

* __<font color=#ff0000 size=7 face="黑体">
已经git add 的如果想要撤销更改,
可以使用 git checkout head -- filename 会撤销提交的变化,本地的也会删除</font>__

### 用git复位移动头指针  git reset
* 经过少量更改后, 可以决定删除这些改动. git reset命令可以用于复位或恢复更改. 我们可以执行三种不同类型的复位操作
* --soft选项 每个分支都有一个HEAD指针,他指向最新的提交,如果用--soft选项后跟提交ID的 git reset命令,那么它将重置HEAD指针提交的ID的git reset命令,
那么他将重置HEAD指针而不会破坏任何东西 
* .git/refs/heads/master 文件存储HEAD指针的提交ID, 可以使用git log -1命令验证它
###倒退命令
* cat .git/refes/heads/master 查看提交版本
* git log -graph --oneline 查看提交日志
* git reset --hard HEAD^    git reset可以将master引用指向任意一个村子的提交id(-hard参数会破坏工作区未提交的改动)
    >注意: 重置命令很危险,因为重置让提交历史也改变了,通过浏览历史不能恢复
    
* git提供了一个挽救机制
    > 显示文件的内容<br>
        git reflog show master | head -5 将最新的改变放到最前面显示<br>
        输出中表达式<refname>@{<n>}的含义:引用<refname>之前第<n>次改变时的SHA1哈希值
   <br>
        重置master为两次改变之前值:<br>
        git reset --hard master@{2}
        
        


###git 命令
git 有很多优势, 其中之一便是远程操作非常简便. 

* git clone <版本库网址> 
    >将存储库克隆到新建的目录中, 
    为克隆的存储库中的每个分支创建远程跟踪分支,
    并从克隆检出的存储库作为当前活动分支的初始分支
    <br><br>
    git clone 支持多种协议, https ssh git 本地文件协议等等
    <br><br>
    
    
    
* git remote 
    >命令管理一组跟踪的存储库
    <br>
    <br>git remote [-v | --verbose]
    <br>git remote add [-t <branch>] [-m <master>] [-f] [--[no-]tags] [--mirror=<fetch|push>] <name> <url>
    <br>git remote rename <old> <new>
    <br>git remote remove <name>
    <br>git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
    <br>git remote set-branches [--add] <name> <branch>…​
    <br>git remote get-url [--push] [--all] <name>
    <br>git remote set-url [--push] <name> <newurl> [<oldurl>]
    <br>git remote set-url --add [--push] <name> <newurl>
    <br>git remote set-url --delete [--push] <name> <url>
    <br>git remote [-v | --verbose] show [-n] <name>…​
    <br>git remote prune [-n | --dry-run] <name>…​
    <br>git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)…​]

* git fetch 
    >命令用于从另一个存储库下载对象和引用
     <br>git fetch [<options>] [<repository> [<refspec>…]]
     <br>git fetch [<options>] <group>
     <br>git fetch --multiple [<options>] [(<repository> | <group>)…]
     <br>git fetch --all [<options>]
     <br>
     从一个或多个其他存储库中获取分支和/或标签(统称为引用)以及完成其历史所必须的对象<br>
     远程跟踪分支已更新(commit),需要将这些更新取回到本地,这时就要用到git fetche命令

* git pull
    >命令用于从另一存储库或本地分支获取并集成(整合)<br>
    git pull 命令的作用是: 取回远程主句某个分支的更新,再与本地的指定分支合并,它的完整格式稍稍有点复杂
    <br>
    git pull [options] [<repository> [<refspec>…]]
    <br>
    将远程存储库中的更改合并到当前分支中,在默认模式下,git pull是git fetch后跟gitmerge FETCH_HEAD的缩写
    <br>
    梗准确地说,git pull是用给定的参数运行git fetch, 并调用git merge将检索到的分支头合并到当前分支中
    <br><br>
    实例
    <br>$ git pull <远程主机名> <远程分支名>:<本地分支名>
    <br>比如，要取回origin主机的next分支，与本地的master分支合并，需要写成下面这样
    <br>$ git pull origin next:master
    <br>如果远程分支(next)要与当前分支合并，则冒号后面的部分可以省略。上面命令可以简写为：
    <br>$ git pull origin next
    <br>上面命令表示，取回origin/next分支，再与当前分支合并。实质上，这等同于先做git fetch，再执行git merge。
    <br>$ git fetch origin
    <br>$ git merge origin/next
    <br><br>
    Git也允许手动建立追踪关系。
    <br>上面命令指定master分支追踪origin/next分支。
    <br>$ git branch --set-upstream master origin/next
    <br>如果当前分支与远程分支存在追踪关系，git pull就可以省略远程分支名。
    <br>$ git pull origin
    <br><br>
    git fetch和git pull的区别
    >>git fetch：相当于是从远程获取最新版本到本地，不会自动合并。
    <br>在实际使用中，git fetch更安全一些，因为在merge前，我们可以查看更新情况，然后再决定是否合并。
    
* git push
    >命令用于将本地分支的更新推送到远程的主机,他的格式和git pull 相似
    <br>
    $ git push <远程主机名> <本地分支名>:<远程分支名>
    <br>git push [--all | --mirror | --tags] [--follow-tags] [--atomic] [-n | --dry-run] [--receive-pack=<git-receive-pack>]
    <br>[--repo=<repository>] [-f | --force] [-d | --delete] [--prune] [-v | --verbose]
    <br>[-u | --set-upstream] [--push-option=<string>]
    <br>[--[no-]signed|--sign=(true|false|if-asked)]
    <br>[--force-with-lease[=<refname>[:<expect>]]]
    <br>[--no-verify] [<repository> [<refspec>…]]
    <br><br>
    __示例__
    <br>git push origin master 将本地分支推送到master上,没有则创建master分支
    <br>git push origin :master 删除远程master分支 等同于 git push origin --delete master
    <br>git push origin 当前分支和远程分支存在追踪关系 则本地和远程分支都可以省略
    <br>git push 将当前分支推动到origin主机的对应分支,如果当前分支只有一个追踪分支,那么主机名也可以省略
    <br>git push -u origin master 将本地分支推送到origin主机,同时制定origin为默认主机,后面就可以git push了