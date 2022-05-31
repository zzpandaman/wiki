# git

## 1. 版本控制

- 本地版本控制

>**版本仓库**仅有一份;并且同一时间仅允许一个人对版本做读写操作。

- 集中版本控制

>**版本仓库**仅有一份，一般存放在服务器;同一时间内允许多人读取**版本仓库**中最新版本并在本地自行修改;提交更新时解决冲突。<br>
>这种解决方案，如果服务器出问题，**版本仓库**丢失，历史版本也就丢失了。<br>
>代表产品：svn

- 分布式版本控制

>**版本仓库**在本地和服务器上同时存在;在没有网络的情况下，本地可以实现版本控制；联网时可以提交到服务器，同时解决冲突。<br>
>代表产品：git

## 2. 安装

- 参考 [菜鸟教程](https://www.runoob.com/git/git-install-setup.html)

## 3. 工作原理

<!-- ![工作原理](../_static/img/git.png) -->
<img src="../_static/img/git.png" width="60%" height="60%">

## 4. 常用命令

- .gitignore 配置失效

```cmd
git rm -r --cached .
git add .
git commit -m "update .gitignore"
git push -u origin master
```

- 查看暂存区状态、查看日志

```cmd
git status -s
git log --oneline
```

- 关联远程仓库

```cmd
git remote add origin url
git remote rm origin
git remote rename old_name new_name
```

- 分支管理

```cmd
git branch
git branch new_branch_name
git branch -d branch_name
git merge
git checkout branch_name
git checkout -b new_branch_name
git push origin remote_branch_name:local_branch_name
```

- 多ssh-key配置

>在~/.ssh路径下，生成多个ssh-key

```cmd
ssh-keygen -t rsa -C '[邮箱]' -f ~/.ssh/github_id_rsa
ssh-keygen -t rsa -C '[邮箱]' -f ~/.ssh/gitlab_id_rsa
```

>在~/.ssh路径下，新建配置文件config

```txt
# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/github_id_rsa

# gitlab
Host gitlab.com
HostName gitlab.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/gitlab_id_rsa

# 如果生成多个 SSH-Key , 则按上面的格式继续往下写
```

