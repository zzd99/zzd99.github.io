---
date: 2019-05-05
title: archlinux安装手记
layout: post
tag: Linux
cover: https://i.loli.net/2018/09/15/5b9c4e0ba1e62.png
---

archlinux安装
===
### 镜像准备
1个大于8GB的U盘、archlinux镜像
* 写入方法
    + Windows下可用rufus写入
    + linux下可使用dd命令写入

校验镜像：因为我是使用linux所以只介绍linux下的方法 
>进终端 md5sum +镜像名 \| grep + 校验码  

dd命令使用
>先取消U盘挂载 sudo umount /dev/sdx sdx为目标U盘
>镜像写入 sudo if = archlinux镜像 of = U盘路径

### 确认引导方式
>ls /sys/firmware/efi/efivars  
>没有输出就是efi引导，不然则为bios
>因为我是efi引导，所以我只写efi的安装方式

### 联网
***注意：archlinux不能离线安装***
* 联网方式
    + 有线  使用dhcpcd连接
    + 无线  使用wifi-menu连接WiFi
    + 是在不行可以选择手机USB共享网络

检测网络连接
>ping Baidu.com  
>ctrl + c结束

###更新系统时间
>timedatectl set-ntp ture

### 改源
>vim /etc/pacman.d/mirrorlist  
>vim可以改用别的编辑器  
>将源改为国内源
>pacman -Syy更新一下源

### 分区

1. 分区方案  一个/，一个/boot/，一个/home
2. 使用lsblk或者fdisk -l命令来确认目标磁盘
3. 用mkfs对目标分区进行格式化  
    mkfs.磁盘格式 /dev/sdx    ***sdx为目标分区 ***
    mkfs.fat-F32 /dev/sdx     **efi分区格式**  
    mkfs.ext4 /dev/sdx     **/和/home分区格式** 
4. 挂载
    mount /dev/sdxx **根分区** /mnt
    mkdir -p /mnt/boot/efi
    mount /dev/sdxx  **home分区** /mnt/home
    mount /dev/sdxx  **efi分区** /mnt/boot/efi

### 安装基础包
>pacstrap -i /mnt base base-devel

### 配置Fstab
>genfstab -U / mnt >> / mnt / etc / fstab
>检查文件 cat /mnt/etc/fstab

### chroot环境
>arch-chroot /mnt

### 安装一下工具
>vim标配工具不解释  
>dialog、wpa_supplicant、ntfs-3gnet、workmanager这好像都是网络管理工具具体不清楚我也是看别人的

### 设置时区
>ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/locatime  

### 设置locale
>vim /etc/locale.gen  
>找到en_US.UTF-8 UTF-8和zh_CN.UTF-8 UTF-8并取消注释  
>设置默认locale
>
>>echo LANG=en_US.UTF-8 > /etc/local.conf

### 设置主机名
>echo xxxx > /etc/hostname  ** xxxx为主机名 ** 

 **** 安装引导
>pacman -S grub efibootmgr  
>grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=archlinux

### 生成配置文件
>grub-mkconfig -o /boot/grub/grub.cfg  
>多系统可安装os-prober  生成配置文件时先运行一下os-prober，再运行上面的命令

### 设置root命令
>passwd

### IntelCPU可安装Intel-ucode

### 退出
>exit  
>umount -R /mnt

### 重启
>reboot

#####  好了archlinux的基础安装已经完成
#####  欢迎加入arch邪教
![archlinux](/assets/img/Archlinux.png)

###### 参考链接
[https://www.viseator.com/2017/05/17/arch_install/](https://www.viseator.com/2017/05/17/arch_install/)


[https://bbs.archlinuxcn.org/viewtopic.php?id=1037](https://bbs.archlinuxcn.org/viewtopic.php?id=1037)
