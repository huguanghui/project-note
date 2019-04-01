[TOC]

# 链接

[google的shell编程风格](https://zh-google-styleguide.readthedocs.io/en/latest/google-shell-styleguide/contents/)

[Linux命令操作](http://man.linuxde.net/)

# Linux的常用命令使用

## 系统操作

### mount

> 挂载

```shell
$ mount -a    # 自动挂载/etc/fstab里面的东西
```

### mknod

>生成设备节点/文件

**用法:**

​	mknod *DEVNAME* {b | c}  *MAJOR*  *MINOR*

样例:

```shell
$ mkdir -p  /dev/cobing
$ mknod /dev/cobing/mydev1 c 128 512
```

### make

> 执行Makefile

#### 选项

```shell
-f：指定“makefile”文件；
-i：忽略命令执行返回的出错信息；
-s：沉默模式，在执行之前不输出相应的命令行信息；
-r：禁止使用build-in规则；
-n：非执行模式，输出所有执行命令，但并不执行；
-t：更新目标文件；
-q：make操作将根据目标文件是否已经更新返回"0"或非"0"的状态信息；
-p：输出所有宏定义和目标文件描述；
-d：Debug模式，输出有关文件和检测时间的详细信息。
```

#### 样例

```shell

```

### nm

> 显示二进制文件的符号表

#### 选项

```shell
-A：每个符号前显示文件名；
-D：显示动态符号；
-g：仅显示外部符号；
-r：反序显示符号表。
```



#### 样例

```shell
# 查看当前路径下所有静态库的中具有HY_PkgStream_DataPopCreate符号的库
$ arm-hisiv500-linux-nm -A *.a | grep HY_PkgStream_DataPopCreate
```



## 文本处理

### grep

> 查找文本

#### 选项

```shell
-a 不要忽略二进制数据。
-A<显示列数> 除了显示符合范本样式的那一行之外，并显示该行之后的内容。
-b 在显示符合范本样式的那一行之外，并显示该行之前的内容。
-c 计算符合范本样式的列数。
-C<显示列数>或-<显示列数>  除了显示符合范本样式的那一列之外，并显示该列之前后的内容。
-d<进行动作> 当指定要查找的是目录而非文件时，必须使用这项参数，否则grep命令将回报信息并停止动作。
-e<范本样式> 指定字符串作为查找文件内容的范本样式。
-E 将范本样式为延伸的普通表示法来使用，意味着使用能使用扩展正则表达式。
-f<范本文件> 指定范本文件，其内容有一个或多个范本样式，让grep查找符合范本条件的文件内容，格式为每一列的范本样式。
-F 将范本样式视为固定字符串的列表。
-G 将范本样式视为普通的表示法来使用。
-h 在显示符合范本样式的那一列之前，不标示该列所属的文件名称。
-H 在显示符合范本样式的那一列之前，标示该列的文件名称。
-i 忽略字符大小写的差别。
-l 列出文件内容符合指定的范本样式的文件名称。
-L 列出文件内容不符合指定的范本样式的文件名称。
-n 在显示符合范本样式的那一列之前，标示出该列的编号。
-q 不显示任何信息。
-R/-r 此参数的效果和指定“-d recurse”参数相同。
-s 不显示错误信息。
-v 反转查找。
-w 只显示全字符合的列。
-x 只显示全列符合的列。
-y 此参数效果跟“-i”相同。
-o 只输出文件中匹配到的部分。
```

#### 样例

```shell
# grep "match_pattern" file_name
$ grep "text" . -r -n  // 递归查找当前目录下的所有文件
```

### awk

> awk是一种编程语言

#### 选项

```shell
-F fs   fs指定输入分隔符，fs可以是字符串或正则表达式，如-F:
-v var=value   赋值一个用户定义变量，将外部变量传递给awk
-f scripfile  从脚本文件中读取awk命令
-m[fr] val   对val值设置内在限制，-mf选项限制分配给val的最大块数目；-mr选项限制记录的最大数目。这两个功能是Bell实验室版awk的扩展功能，在标准awk中不适用。
```

#### 样例

```shell

```

### sed

> sed是一个流编辑器

#### 选项

```shell
-e<script>或--expression=<script>：以选项中的指定的script来处理输入的文本文件；
-f<script文件>或--file=<script文件>：以选项中指定的script文件来处理输入的文本文件；
-h或--help：显示帮助；
-n或--quiet或——silent：仅显示script处理后的结果；
-V或--version：显示版本信息。
```

####   样例

```shell
$ sed -e s/Last\ Changed\ Rev:\ //g
```

### cut

> 显示行中指定部分

#### 选项

```shell
-b：仅显示行中指定直接范围的内容；
-c：仅显示行中指定范围的字符；
-d：指定字段的分隔符，默认的字段分隔符为“TAB”；
-f：显示指定字段的内容；
-n：与“-b”选项连用，不分割多字节字符；
--complement：补足被选择的字节、字符或字段；
--out-delimiter=<字段分隔符>：指定输出内容是的字段分割符；
--help：显示指令的帮助信息；
--version：显示指令的版本信息。
```

#### 样例

```shell
$ cut -d+ -f1
```

### wc

> 计算命令

#### 选项

```shell
-c或--bytes或——chars：只显示Bytes数；
-l或——lines：只显示列数；
-w或——words：只显示字数。
```

#### 样例

```shell
$ echo $SVN | wc -c
```



# 常用系统相关命令

```shell
系统
　　# uname -a # 查看内核/操作系统/CPU信息
　　# head -n 1 /etc/issue # 查看操作系统版本
　　# cat /proc/cpuinfo # 查看CPU信息
　　# hostname # 查看计算机名
　　# lspci -tv # 列出所有PCI设备
　　# lsusb -tv # 列出所有USB设备
　　# lsmod # 列出加载的内核模块
　　# env # 查看环境变量
资源
　　# free -m # 查看内存使用量和交换区使用量
　　# df -h # 查看各分区使用情况
　　# du -sh <目录名> # 查看指定目录的大小
　　# grep MemTotal /proc/meminfo # 查看内存总量
　　# grep MemFree /proc/meminfo # 查看空闲内存量
　　# uptime # 查看系统运行时间、用户数、负载
　　# cat /proc/loadavg # 查看系统负载
磁盘和分区
　　# mount | column -t # 查看挂接的分区状态
　　# fdisk -l # 查看所有分区
　　# swapon -s # 查看所有交换分区
　　# hdparm -i /dev/hda # 查看磁盘参数(仅适用于IDE设备)
　　# dmesg | grep IDE # 查看启动时IDE设备检测状况
网络
　　# ifconfig # 查看所有网络接口的属性
　　# iptables -L # 查看防火墙设置
　　# route -n # 查看路由表
　　# netstat -lntp # 查看所有监听端口
　　# netstat -antp # 查看所有已经建立的连接
　　# netstat -s # 查看网络统计信息
进程
　　# ps -ef # 查看所有进程
　　# top # 实时显示进程状态
用户
　　# w # 查看活动用户
　　# id <用户名> # 查看指定用户信息
　　# last # 查看用户登录日志
　　# cut -d: -f1 /etc/passwd # 查看系统所有用户
　　# cut -d: -f1 /etc/group # 查看系统所有组
　　# crontab -l # 查看当前用户的计划任务
服务
　　# chkconfig --list # 列出所有系统服务
　　# chkconfig --list | grep on # 列出所有启动的系统服务
程序
　　# rpm -qa # 查看所有安装的软件包
其他常用命令整理如下：
　　查看主板的序列号：dmidecode | grep -i 'serial number'
　　用硬件检测程序kuduz探测新硬件：service kudzu start ( or restart)
　　查看CPU信息：cat /proc/cpuinfo [dmesg | grep -i 'cpu'][dmidecode -t processor]
　　查看内存信息：cat /proc/meminfo [free -m][vmstat]
　　查看板卡信息：cat /proc/pci
　　查看显卡/声卡信息：lspci |grep -i 'VGA'[dmesg | grep -i 'VGA']
　　查看网卡信息：dmesg | grep -i 'eth'[cat /etc/sysconfig/hwconf | grep -i eth][lspci | grep -i 'eth']
　　查看PCI信息：lspci (相比cat /proc/pci更直观)
　　查看USB设备：cat /proc/bus/usb/devices
　　查看键盘和鼠标：cat /proc/bus/input/devices
　　查看系统硬盘信息和使用情况：fdisk & disk – l & df
　　查看各设备的中断请求(IRQ)：cat /proc/interrupts
　　查看系统体系结构：uname -a
　　查看及启动系统的32位或64位内核模式：isalist –v [isainfo –v][isainfo –b]
　　查看硬件信息，包括bios、cpu、内存等信息：dmidecode
　　测定当前的显示器刷新频率：/usr/sbin/ffbconfig –rev ?
　　查看系统配置：/usr/platform/sun4u/sbin/prtdiag –v
　　查看当前系统中已经应用的补丁：showrev –p
　　显示当前的运行级别：who –rH
　　查看当前的bind版本信息：nslookup –class=chaos –q=txt version.bind
　　查看硬件信息：dmesg | more
　　显示外设信息， 如usb，网卡等信息：lspci
　　查看已加载的驱动：
　　lsnod
　　lshw
　　查看当前处理器的类型和速度(主频)：psrinfo -v
　　打印当前的OBP版本号：prtconf -v
　　查看硬盘物理信息(vendor， RPM， Capacity)：iostat –E
　　查看磁盘的几何参数和分区信息：prtvtoc /dev/rdsk/c0t0d0s
　　显示已经使用和未使用的i-node数目：
　　df –F ufs –o i
　　isalist –v
　　对于“/proc”中文件可使用文件查看命令浏览其内容，文件中包含系统特定信息：
　　主机CPU信息：Cpuinfo
　　主机DMA通道信息：Dma
　　文件系统信息：Filesystems
　　主机中断信息：Interrupts
　　主机I/O端口号信息：Ioprots
　　主机内存信息：Meninfo
　　Linux内存版本信息：Version
备注： proc – process information pseudo-filesystem 进程信息伪装文件系统
```



# 脚本使用技巧

## 遍历

```shell
for initscript in /etc/init.d/S[0-9][0-9]*
do
        if [ -x $initscript ] ;
        then
                echo "[RCS]: $initscript"
                $initscript start
        fi
done
```

## set -e的使用

```shell
// 当命令以非0状态退出时,退出shell
```

