在运行系统时发现自带的无线网卡驱动的下载速度很慢，就觉得可能是无线网卡驱动不太匹配导致的，所以就去网站找了个匹配的网卡驱动，现在把找到的驱动的安装过程进行记录，方便以后重装系统使用。

本机的无线网卡驱动为Broadcom BCM4313，在[https://wiki.debian.org/wl](https://wiki.debian.org/wl)上找到了教程。

1.Add a "non-free" component to **/etc/apt/sources.lis**t for your Debian version, for example:

```
# Debian 8 "Jessie"
deb http://httpredir.debian.org/debian/ jessie main contrib non-free
```

2.Update the list of available packages. Install the relevant/latest linux-image, linux-headers and [broadcom-sta-dkms](https://packages.debian.org/broadcom-sta-dkms) packages:

```
# apt-get update
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 导入证书
# apt-get install linux-image-$(uname -r|sed 's,[^-]*-[^-]*-,,') 
linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') broadcom-sta-dkms
```

3.Unload conflicting modules:

```
# modprobe -r b44 b43 b43legacy ssb brcmsmac bcma
```

4.Load the wl module:

```
# modprobe wl
```



