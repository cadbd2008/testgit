$ git	查看是否安装git
$ sudo apt-get install git	Linux 安装git
$ git config --global user.name "Your Name"	配置用户名
$ git config --global user.email "email@example.com"	配置用户邮箱
$ mkdir	XXX	创建文件夹
$ cd XXX	打开文件夹
$ git init	初始化一个空的仓库
$ ls -ah	查看当前路径文件列表（含隐藏文件/夹）
$ git add XXX	把工作区的文件添加到缓存区
$ git commit -m "本次提交内容的描述信息"	把缓存区的文件全部提交
$ git status	查看当前工作区状态（是否有未提交的内容，或新增内容）
$ git diff XXX	查看工作区某文件做了什么修改，来判断是否提交到仓库
$ git log	查看提交版本的历史
$ git log --pretty=oneline 查看提交版本的历史（单行显示）
$ git reset --hard HEAD^	退回到上个版本
$ git reset --hard XXXX		退回到指定版本，XXX为commit id
$ git reflog	查看每一次执行的命令（可用于版本退回后，查看退回前新版本的commit id,恢复新版本）
$ cat XXX	查看工作区某文件的内容
$ git checkout -- XXX	
	撤销XX文件的修改
	1.add 后checkout 为撤销到刚添加到缓存区的版本
	2.未add时checkout 为撤销到当前版本库的内容
$ git checkout	XXX	切换到XXX分支
$ git reset HEAD XXX	把暂存区的修改撤销掉（unstage），重新放回工作区
$ git rm XXX	从版本库中删除XXX文件
$ rm XXX	删除XX文件，版本库中依旧存在
$ ssh-keygen -t rsa -C "youremail@example.com"	创建SSH Key(.ssh目录，里面有id_rsa和id_rsa.pub两个文件)
$ git remote add origin git@github.com/cadbd2008/testgit.git	
	将本地版本库关联到自己账号的远程库中（远程库的名字就是origin，这是Git默认的叫法，也可以改成别的）
$ git push -u origin master 	
	把当前分支master推送到远程,第一次推送master分支时，加上了-u参数，
	Git不但会把本地的master分支内容推送的远程新的master分支，
	还会把本地的master分支和远程的master分支关联起来
$ git push origin master 发送到远程GitHub库
$ git clone git@github.com:cadbd2008/testcopygit.git	
	通过git://使用ssh（也可以使用https等其他协议）从远程克隆库
$ git checkout -b dev	创建dev分支，切换到dev分支
$ git branch	查看当前所有分支
$ git branch XXX 创建XXX分支
$ git branch -d dev	删除dev分支
$ git merge dev 
	把dev分支内容合并到master分支中
	当遭遇冲突时，$ git status ，Git会用<<<<<<<，=======，>>>>>>>标记出不同分支的内容
$ git log --graph --pretty=oneline --abbrev-commit
	带参数的git log,可以看到分支的合并情况
$ git log --graph	可以看到分支合并图
$ git merge --no-ff -m "merge with no-ff" dev
	合并dev分支，请注意--no-ff参数，表示禁用Fast forward：用于管理分支历史
$ git stash 把当前工作现场隐藏起来
$ git stash list 查看被隐藏的工作现场
$ git stash pop 恢复的同时把stash内容也删了
$ git stash apply stash@{0} 恢复{0}的工作现场
$ git stash drop 删除stash内容(删除第一个)
$ git branch -D XXX	强行删除XXX分支（分支内容未合并时强行删除）
$ git remote	查看远程库的信息
$ git remote -v	查看远程库详细的信息
$ git pull	最新的提交从origin/dev抓下来
$ git pull --set-upstream dev origin/dev
	指定本地dev分支与远程origin/dev分支的链接
$ git tag v1.0	给当前分支打上版本标签（默认标签是打在最新提交的commit上）
$ git tag v0.9 commit id	给特定版本的commit打上标签
$ git tag	查看标签
$ git show v1.0	查看标签v1.0的信息
$ git tag -a v1.4 -m 'my version 1.4' 添加自定义注释的标签
$ git tag -s v1.5 -m 'my signed  1.5' GPG 来签署的标签(如果有私钥)
$ git tag -v v1.4.2.1	此命令会调用 GPG 来验证签名需要有签署者的公钥，存放在 keyring 中
$ git push origin v1.5	分享标签到远端仓库
$ git push origin --tags	一次性推送全部尚未推送到远程的本地标签
$ git tag -d v0.1	删除v0.1标签
$ git tag -d v0.9;$ git push origin :refs/tags/v0.9
	标签已经推送到远程,先从本地删除标签,然后，从远程删除
https://github.com/github/gitignore
	.gitignore文件,配置需要忽略的文件（此网站有现成的，需要组合下就能使用）
$ git check-ignore -v App.class
	检查忽略文件匹配的规则（用于快速查找匹配错误的规则）
配置别名：
$ git config --global alias.st status	git st =git status
$ git config --global alias.co checkout	git co =git checkout
$ git config --global alias.ci commit	git ci =git commit
$ git config --global alias.br branch	git br =git branch
$ git config --global alias.unstage 'reset HEAD	git unstage XXX =git reset HEAD XXX
$ git config --global alias.last 'log -1'  git last=git log -1 显示最后一次提交信息
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"	日志输出的颜色配置
	--global参数是全局参数，也就是这些命令在这台电脑的所有Git仓库下都有用。
	如果不加，那只针对当前的仓库起作用。
	每个仓库的Git配置文件都放在.git/config文件中
	当前用户的Git配置文件放在用户主目录下的一个隐藏文件.gitconfig中
