---
title: Git使用
date: 2025-08-25 01:16:01
tags:

---

### 仓库初始化

``` bash
$ cd "/target_repository_file"
$ git init
$ git add .
$ git commit -m "first commit"
$ git remote add origin "远端github仓库地址"
$ git branch -M main
$ git push -u origin main
```

### 仓库更新

``` bash
$ cd "/target_repository_file"
$ git add .
$ git commit -m "更新说明"
# 拉取远程最新内容（防止冲突，非必要）
# git pull origin main
$ git push origin main
```

### 仓库ssh密码设置
作用：每次开新终端不用输用户名与密码了。
安全性高，没用明文(Personal Access Token)保存。

#### 生成密钥
``` bash
$ mkdir -p ~/.ssh
$ chmod 700 ~/.ssh
# -t 为加密方式 （ed25519 是 一种椭圆曲线加密算法）-C 为注释（可以填 邮箱、用户名 或 描述用途）
$ ssh-keygen -t ed25519 -C "forever_love233@163.com"
```

#### 输出log
``` bash
xy@xy:~$ ssh-keygen -t ed25519 -C "forever_love233@163.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/xy/.ssh/id_ed25519):         
passphrase:二次验证密钥(之后在终端push会弹出的窗口中输入的密码是这个)
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/xy/.ssh/id_ed25519
Your public key has been saved in /home/xy/.ssh/id_ed25519.pub
The key fingerprint is:XXX
```
#### 配置github
``` bash
$ cat ~/.ssh/id_ed25519.pub
# 复制内容到github->setting->SSH and GPG keys->SSH keys->New SSH Key
# 最后在仓库目录，点击code->ssh 复制网址替换到下面代码中
$ cd "/target_repository_file"
$ git remote set-url origin git@github.com:foreverxiaoyu/my_blog.git
```

#### 开个新终端测试
``` bash
$ git push origin main
# 在弹出的窗口中输入之前的passphrase
```
