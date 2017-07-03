man 获取命令的帮助信息

```
man mkdir
```

info 获取命令的详细使用方法

```
info mkdir
```

clear 清屏

cd 切换目录

pwd 输出当前目录

ls 输出目录内容

```
ls -l 输出目录详细信息 -rw-r--r-- 1 morrisware morrisware  7214980 6月  29 16:08 ffmpeg_2.8.11.orig.tar.xz
ls -a 输出全部目录内容，包括隐藏文件
ls -d 仅输出目录
```

cp 拷贝文件

mv 移动文件或修改文件名

cat 输出文件内容

chmod 修改文件和目录权限

```
u is for user
g is for group
o is for others
a is for all
r is for read permission
w is for write permission
x is for execute permission
chmod u+rwx,g+x,o+x file _rwx__x__x file
chmod -R 755 dir 递归地改变目录内所有文件的权限
chmod 755 * 修改当前目录下所有目录的权限
```

mkdir 创建目录

```
mkdir -p dir1/dir2/dir3/dir4/dir5 创建一个路径上所有不存在的目录
```

rm 删除文件或目录

grep 在文件中查找字符串（不区分大小写）

```
grep -i “the” file
```

find 查找指定文件名的文件

```
find -name "file" 在当前目录和子目录查找名为file的文件
find -iname "file" 在当前目录和子目录查找名为file的文件，不区分大小写
find /dir -name “file” 从指定目录dir下开始查找名位file的文件
find -maxdepth n -name “file” 从指定目录dir下开始查找名位file的文件，层级位n（当前目录为1）
find /dir -empty 从指定目录dir下开始查找大小为0的空文件
```

tar

```

```

ps 显示正在运行中的进程信息

ifconfig 查看和配置LInux系统的网络接口

```
ifconfig -a
ifconfig eth0 up
ifconfig eth0 down
```

ping 连接远程主机，发送数据包测试连接

date 设置系统日期

```
date -s "02/07/2017 10:44:12"
hwclock -systohc 同步硬件时间
hwclock --systhohc -utc 同步系统时间
```



