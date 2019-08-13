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
![vscode](/assets/img/vscode/shot1)  


先暂存更改，然后提交
![vscode](/assets/img/vscode/shot2)  


提交更改时它会让你填写提交消息，再这里我填的是vscode下git推送
![vscode](/assets/img/vscode/shot3) 


这是完成后的提交消息，vscode下的git推送 
![vscode](/assets/img/vscode/shot4)  


推送
![vscode](/assets/img/vscode/shot5) 


输入git用户名和密码 
![vscode](/assets/img/vscode/shot6)  
![vscode](/assets/img/vscode/shot7) 

完成推送