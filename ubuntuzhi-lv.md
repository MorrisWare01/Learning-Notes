> https://www.zhihu.com/question/46525639?sort=created

UTC即Universal Time Coordinated，协调世界时（世界统一时间）

GMT 即Greenwich Mean Time，格林尼治平时

Windows 与 Mac/Linux 看待系统硬件时间的方式是不一样的：

Windows把计算机硬件时间当作本地时间\(local time\)，所以在Windows系统中显示的时间跟BIOS中显示的时间是一样的。

Linux/Unix/Mac把计算机硬件时间当作 UTC， 所以在Linux/Unix/Mac系统启动后在该时间的基础上，加上电脑设置的时区数（ 比如我们在中国，它就加上“8” ），因此，Linux/Unix/Mac系统中显示的时间总是比Windows系统中显示的时间快8个小时。

```
timedatectl set-local-rtc 1 --adjust-system-clock 
```











