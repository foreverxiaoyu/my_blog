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
$ # 拉取远程最新内容（防止冲突，非必要）
$ # git pull origin main
$ git push origin main
```

### 仓库ssh密码设置

``` bash
$ mkdir -p ~/.ssh
$ chmod 700 ~/.ssh
$ # -t 为加密方式 -C 为注释（可以填 邮箱、用户名 或 描述用途）
$ ssh-keygen -t ed25519 -C "forever_love233@163.com"

xy@xy:~$ ssh-keygen -t ed25519 -C "forever_love233@163.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/xy/.ssh/id_ed25519):         
# passphrase:二次验证密钥
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/xy/.ssh/id_ed25519
Your public key has been saved in /home/xy/.ssh/id_ed25519.pub
The key fingerprint is:XXX

$ 
$ 
$ 
```
