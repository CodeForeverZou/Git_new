# git is a version control tool


git config --global user.name '..'

git config --global user.mail 

ssh-keygen

cd ~/.ssh

cat id_ssh.pub

git remote add origin git@github.com:CodeForeverZou/Git2.git

---

工作区

git init

暂存区

git add <>

版本库

git commit -m '...'

---

git log

git diff readme

git status

---

git reset HEAD~~

git reflog

git reset Hard ead543f

git checkout -- readme

git reset HEAD readme

---

 git push -u origin master

echo "# Git2" >> README.md<br>
git init<br>
git add README.md<br>
git commit -m "first commit"<br>
git remote add origin git@github.com:CodeForeverZou/Git2.git<br>
git push -u origin master

-----------------------------------------------

GitLAb操作（若只有ssh能clone，注意不需要添加端口号）

git status

git add -A #提交所有操作

git commit -m '更改内容'

git push

---

 git pull

 git branch dev
 
 git checkout master
 
 git branch -d dev

---

 两个用户、两个github帐号，同一台主机，一个git终端
 
 这就需要两个ssh的密钥，但要区别出主机，并且密钥不能互相覆盖

 1、生成一个新的SSH KEY
 
 ssh-keygen -t rsa -f "~/.ssh/id_rsa2" -C "Mail"
 
 然后把生成的key（id_ras2.pub的内容）添加到github中，完成github配置

 2、在~/.ssh目录下，创建一个confg文件，区别主机
 
 vi config<br>
 输入如下内容：
 
 Host git<br>
 HostName github.com<br>
 User git<br>
 IdentityFile ~/.ssh/id_rsa

 Host git2<br>
 HostName github.com<br>
 User git<br>
 IdentityFile ~/.ssh/id_rsa2

 3、将地址中的git@github.com替换成新建的Host别名
 
 原来的项目的ssh地址为： 
 
 $ git@github.com:A/Demo.git 
 
 那么替换后的地址为： 
 
 $ github-bcount:A/BestoneGitHub.git 
 
 或者： 
 
 $ git@github-bcount:A/Demo.git 

 然后可以使用$ ssh -T github-bcount命令看看是否修改成功 <br>
 用ssh -T git@github.com 看看是不是原来用户的名字，（即实现两个用户分别连接）

 用$ git remote -v判断一下现在连的是不是Demo这个地址的远程仓库，如果是的，修改host名称：

 $ git remote set-url origin github- bcount:A/Demo.git

 4、执行push、pull等同步命令即可
 
 git push -u origin master

---

查看用户：git config user.name

查看邮箱：git config user.email

![](https://github.com/CodeForeverZou/Git_new/blob/master/img/git%20problem.png)

git config --global user.email "你的邮箱"

git config --global user.name "你的名字"
