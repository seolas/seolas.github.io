---
title: Linux 笔记
date: 2024-08-03 09:38:48
tags:
- Linux
---

## 命令

### man 查看手册

查看命令手册
`man 命令名`

> 空格翻页, Enter 下一行, q 退出

### pwd 显示当前目录

`pwd`

### cd 切换目录

`cd /home`

> `./` 当前目录
> `../` 上一层目录

### touch 创建文件

`touch a.txt`

> 文件存在时, 会改变文件的修改时间

### ls 列出当前目录下的文件

列出当前目录下的所有文件
`ls -alF`
* -a 显示隐藏文件
* -l 以长列表格式显示
* -F 区分文件还是目录
* -i 显示 inode 编号

过滤输出列表, 只显示指定文件, 可以使用通配符
`ls -l test`

> Bash 中的通配符只有 3 个:
> `?` 匹配任意单个字符
> `*` 匹配 0 个或多个字符
> `[]` 匹配指定范围内的单个字符, 可以使用 ! 排除指定范围 [!a]

查看目录的相关信息
`ls -dl 目录名`

### cp 复制文件

复制文件, 可以使用通配符
`cp -i 源文件 目标文件`

* -i 询问是否覆盖已有文件

复制文件到指定目录
`cp 源文件 指定目录/`

> 注意: 一定要在目录后加上 /
> 复制到当前目录, 使用 `.`

复制目录到新目录
`cp -R 原目录 新目录`

* -R 递归地复制

> 注意: 新目录并不存在

### ln 创建链接

创建硬链接, inode 相同
`ln 原文件 链接名`

创建软链接, inode 不同
`ln -s 原文件 链接名`

### mv 移动文件

移动文件
`mv 源文件 目标文件`

移动文件到目录
`mv 源文件 目标目标/`

移动目录
`mv 原目录 目标目录`

### rm 删除文件

`rm -i 文件`

* -i 询问是否删除
* -f 强制删除

递归删除目录
`rm -ir 目录`

### mkdir 创建目录

`mkdir -p 目录`

* -p 同时创建中间缺失的父目录

### rmdir 删除空目录

`rmdir 目录/`

> 删除非空目录用 rm 指令

### file 查看文件类型

`file 文件`

### cat 查看文本内容

`cat -n a.txt`

* -n 显示行号

### more 分页查看文本内容

`more a.txt`

### less 分页查看文本内容

`less a.txt`

* `?字符串` 向上搜索
* N 向前搜索
* `/字符串` 向下搜索
* n 向后搜索

### tail 显示最后几行内容

实时显示最后 15 行
`tail -nf 15 a.txt`

* -f 实时监测

> 如果不带 -n, 默认是 10 行

### head 显示前几行

`more -n 15 a.txt`

### ps 当前用户进程

查看当前用户所有进程
`ps -ef`

* -e 所有进程
* -f 完成格式的输出
* --forest 以树形格式显示

### top 查看实时进程信息

`top`

### kill 使用 PID 杀死属主进程

`kill -s PID列表`

* -s 强制杀死

### pkill 使用程序名杀死进程

支持通配符
`pkill http*`

### mount 显示已挂载的设备

`mount`

指定文件系统类型输出
`mount -t ext4`

手动挂载设备
`mount -t 文件系统类型 设备位置 挂载点目录`

> 需要 root 身份才能挂载

### umount 移除可移动设备

`umount 设备位置或挂载点`

> 如果有进程在使用设备, 不能卸载, 使用 lsof 命令

### df 查看磁盘的使用情况

`df -ht ext4`

* -h 以易读形式显示
* -t 指定文件系统类型

### du 查看当前目录的磁盘使用情况

`du -h`

* -h 以易读形式显示

### sort 将文件的内容排序显示

`sort -n a.txt`

* -n 将字符串类型的数字按值排序

### grep 正则表达式搜索文本

`grep -n 匹配内容 a.txt`

* -n 显示行号

### gzip 压缩文件为 .gz

`gzip 文件名`

> 支持通配符

### tar 压解缩文件

创建 a.tar 文件, 包含目录1和目录2的内容
`tar -cvf  a.tar 目录1/ 目录2/`

* -c 创建 tar 文件
* -v 在处理时显示文件名
* -f file 将结果输出到文件

列出 tar 文件的内容
`tar -tf a.tar`

提取 tar 文件的内容
`tar -xvf a.tar`

* -x 从 tar 中提取文件

提取 .tgz 文件
`tar -zxvf a.tgz`

提取 .tar.xz 文件
`tar -Jxvf a.tar.xz`

### which 找到命令的位置

`which 命令名`

### alias 为命令创建别名

`alias li='ls -i'`

### unalias 取消别名

`unalias 别名`

### env 查看全局变量

`env`

### printenv 查看个别环境变量

`printenv HOME`

### echo 显示变量的值

`echo $HOME`

### set 显示所有环境变量

`set`

### 设置自定义局部变量

`小写变量名=值`

> 注意事项:
> * 如果值有空格, 必须用单引号或双引号包起来
> * =左右不能有空格

### export  设置自定义全局变量

`export 小写变量名=值 `

### unset 删除环境变量

`unset 变量名`

### 设置 PATH 环境变量

`PATH=$PATH:执行文件目录`

> 系统重启后就没了
> 系统会从  个文件读取命令: /etc/profile, $HOME/.bash_profile, $HOME/.bashrc, $HOME/.bash_login, $HOME/.profile

### 数组变量

设置数组变量
`变量名=(值1 值2)`

单独取数组的每个值
`echo ${变量名[索引]}`

### 添加用户

`useradd -m test`

* -m 创建 $HOME 目录

### 删除用户

`userdel -r test`

* -r 删除用户目录

### passwd 修改用户密码

`passwd test`

### chpasswd 批量修改密码

从标准输入读入以冒号分隔的登录名和密码对, 进行修改
`chpasswd < users.txt`

### groupadd  创建组

`groupadd gpd`

### usermod  向组中添加用户

`usermod -G gpd test`

* -G 将用户加入组, 不会影响 /etc/passwd 的主要组

### groupmod 修改组

修改组名
`groupmod -n gpd2 gpd`

### chmod 修改权限

以八进制模式设置
`chmod 760 a.txt`

以符号模式设置
`chmod  u-x a.txt`

### chown 修改文件属主

`chown test a.txt`

同时修改属主和属组
`chown test.grp a.txt`

### chgrp 修改文件属组

`chgp grp a.txt`

### fdisk 创建分区

进入交互命令
`fdisk /dev/sda`

* p 显示当前分区表
* n 添加一个新分区
* w 将分区表写入磁盘并退出
* q 退出, 不保存更改

### gdisk GPT 分区

进入交互命令, 命令和 fdisk 差不多
`gdisk /dev/sda`

### apt 软件包管理工具

输出已安装的软件包
`apt --installed list`

显示软件包详细信息
`apt show 软件名`

查找软件包
`apt search 软件名`

安装软件包
`apt install 软件名`

升级软件
`apt upgrade`

删除软件包, 保留配置
`apt remove zsh`

删除软件包, 不保留配置
`apt purge zsh`

删除不再被依赖的软件包
`apt autoremove`

仓库位置在 /etc/apt/source.list

### 安装源码包

1. 检查编译器和库依赖
    `./configure`
2. 构建二进制文件
    `make`
3. 安装到常用位置
    `make install`

> 需要已安装 gcc 和 make 软件包

### vim 编辑器

`/` 进入搜索模式
`i` 进入编辑模式
`:` 进入命令模式
* q 不保存退出
* q! 强制不保存退出
* wq 保存退出

