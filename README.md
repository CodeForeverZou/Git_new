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

若push时出现如下问题：Please tell me who you are
则先查看用户、邮箱，然后再配置相同的用户、邮箱即可！

![](https://github.com/CodeForeverZou/Git_new/blob/master/img/git%20problem.png)

git config --global user.email "你的邮箱"

git config --global user.name "你的名字"

---
1）、不小心init仓库：git取消文件夹 版本控制：**执行命令：find . -name ".git" | xargs rm -Rf** 或者：rm -rf .git

2）、验证公钥可用：**在git bash终端输入ssh -T git@github.com验证与github是否连接成功.**

3）、**push没权限** git@github.com: Permission denied (publickey). fatal: 无法读取远程仓库。请确认您有正确的访问权限并且仓库存在。

ssh git@github.com 验证私钥是不是添加成功。

git remote add origin git@github.com:CodeForeverZou/Git2.git<br>
git push origin master

---
## ubuntu虚拟机遇到的问题

首先：新建git用户邮箱，添加shh-key，这里你的key随便怎么生成（以下都行，添加后都能用，与name、email无关）
* ssh-keygen
* ssh-keygen -t rsa -C "username" (注：username为你git上的用户名)，✖ 这是随意的
* ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

### 网络错误

其次：git push时，*ssh: Could not resolve hostname github.com: Temporary failure in Aname resolution fatal: Could not read from remote repository.*
* 原因是网络问题，发现虚拟机网页也上不了网，可虚拟底下显示网络连接正常！！！尝试更改net、桥接。。等模式，，
* 后来才发现，Ubuntu是需要自己手动开启网络的，在右上角！！！看到wifi标志

### 版本不一致

最后：*ssh: Could not resolve hostname github.com: Temporary failure in Aname resolution fatal: Could not read from remote repository.*

*! [rejected] master -> master (fetch first)* 
* 因为两个仓库提交历史不一致，无法pull拉取远程信息，所以需要在GIT命令中添加一句代码：–allow-unrelated-histories允许不相关历史进行提交
* 最好是，git pull 把网上的版本拉下来，然后再 push； （这里git pull origin master指定清楚的好）
* git提供了一种强制上传的方式：git push -f ，它会忽略版本不一致等问题，强制将本地库上传的远程库，但是一定要谨慎使用，因为-f会用本地库覆盖掉远程库

---
git 查看分支：git branch -a（或者git branch -vv）

Ubuntu查看git安装目录： which git.

QT结合git，工具→选项→版本控制→Git→首路径填写git路径，重启在工具向→Git→添加仓库即可

---
保留代码git信息

先git clone

再git push 推送到自己仓库，会保留git信息

---
Git推送大文件

git lfs track "*.pack"

git lfs track "*.so"

echo "*.zip" >> .gitignore

查看

 git lfs track
 
 git lfs ls-files
 
移除git

rm -rf .git

---
```
关联已有目录或仓库
以下命令行需要您在 Git客户端 执行， 不知如何安装Git客户端？
下载Windows下的Git命令行客户端
下载Windows下的Git小乌龟客户端
下载MacOS下的Git客户端

克隆/推送仓库之前还需最后一步：添加SSH密钥，不知如何添加SSH密钥？
配置Git全局用户名和用户邮箱
git config --global user.name "your username"
git config --global user.email "your Email"

在本地克隆仓库并推送新建的README文件
git clone ssh://git@xxx.git
cd Security-Console-scc
echo "# Security-Console-scc" > README.md
git add README.md
git commit -m "add README"
git push -u origin master

关联已有代码目录到仓库
cd <Your directory path>
mv README.md README-backup.md
git init
git remote add origin ssh://git@xxx.git
git pull origin master
git add --all
git commit -m "Initial commit"
git push -u origin master

关联已有代码目录到仓库
cd <Your directory path>
git init
git remote add origin ssh://git@xxx.git
git add --all
git commit -m "Initial commit"
git push -u origin master

关联已有的Git仓库
cd <Your Git repository path>
git remote remove origin > /dev/null 2>&1
git remote add origin ssh://git@xxx.git
git push -u origin --all -f
git push -u origin --tags -f
到这里您应该已经推送内容到本仓库了，去试下其他功能吧！
![image](https://xxx.png)
```
