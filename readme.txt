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
$ git branch XXX c\创建XXX分支

