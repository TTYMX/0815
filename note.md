#git常用命令
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

###设置命令

####所有的操作
* git config --global user.name 'aaa'
* git config --global user.email 'youremail@email,com'
* git config --global push.default

####一个特定的项目
* git config user.name 'aaa'
* git config user.email 'email@email.com'

###基本命令

pwd 查看当前所在文件位置
1. 删除本地分支
> git branch -d <BranchName>
2. 删除远程分支
> git push origin --delete <BranchName>
3. 查看所有分支
> git branch -a



##详解命令
* git push origin master 将本地分支的更新推送到远程主机
<br>
>推送 远程主机 本地master分支 如果远程的master分支不存在创建之<br>
>本地分支被省略，表示删除远程分支
git push origin :master等同于git push origin --delete master<br>
>如果本地分支和远程分支存在追踪关系,则本地分支和远程分支都可以省略
git push origin<br>
>如果当前分支只有一个追踪分支，那么主机名也可以省略　git push<br>
>如果当前分支和多个主机存在追踪关系，可以用-u选项指定一个默认主机
　git push -u origin master



