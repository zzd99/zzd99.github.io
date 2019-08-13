---
date: 2019-8-13
title: vscode下git推送
layout: post
tag: git
cover: https://www.technotification.com/wp-content/uploads/2018/04/git-commands.jpg
---

**git小白个人操作**

# 首先得确保电脑装有GIT
> debian系安装命令：sudo apt install git  
> arch系安装命令：sudo pacman -S git  

# 运行下面两个命令（git全局设置）
>git config --global user.name "用户名"   
>git config --global user.email "用户邮箱"

# vscode操作
+ 确保操作文件为git仓库(手动创建或者git clone拉取的均为git仓库)
+ vscode打开仓库文件夹
+ 对文件进行操作（增删改查）后进行如下操作  

![vscode1](/assets/img/vscode-git-1.png)  

### 先暂存更改，然后提交
![vscode2](/assets/img/vscode-git-2.png)  

### 提交更改时它会让你填写提交消息，再这里我填的是vscode下git的使用   
![vscode3](/assets/img/vscode-git-3.png) 

### 这是完成后的提交消息，vscode下的git的使用  
![vscode4](/assets/img/vscode-git-4.png)  

### 推送
![vscode5](/assets/img/vscode-git-5.png) 

### 输入git用户名和密码  
![vscode6](/assets/img/vscode-git-6.png)  
![vscode7](/assets/img/vscode-git-7.png)  

### 完成推送
 