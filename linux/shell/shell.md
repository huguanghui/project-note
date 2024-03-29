[TOC]

# 链接

[shell语法](https://github.com/qinjx/30min_guides/blob/master/shell.md)

[google的shell编程风格](https://zh-google-styleguide.readthedocs.io/en/latest/google-shell-styleguide/contents/)

[Linux命令操作](http://man.linuxde.net/)

[/usr/bin/env和/usr/bin/bash的比较](https://blog.csdn.net/austin_zhou001/article/details/46591169)

[shell替换整行](https://blog.csdn.net/qq_42016265/article/details/90711264)

# Linux的常用命令使用

## 打包相关

### tar

```shell
# 显示包中的文件列表
tar tvf [包名]
```

## 网络操作

### curl

> 一个利用URL规则在命令行下工作的文件传输工具。它支持文件的上传和下载

#### 选项

```c++
-s		静默模式.不输出任何东西
-S		显示错误
-L		Follow redirects
```

#### 样例

```c++
$curl 
```

## 系统操作

### 用户管理

```shell
$ chown mysql auth.log #含义为 把 文件 auth.log 的所有者更改为 mysql
$ chgrp  -R  mysql  apache2  #含义为 ，把 目录apache2 的所在组更改为mysql
```

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
# 查看动态库的函数是否定义
$ arm-hisiv500-linux-nm -D yourLib.so |grep -w yourFunction
# 查看进程动态依赖库
$ readelf -a program | grep "Shared"
# 查看编译器
$ readelf build/mips-linux-gnu/release/t40_demo -p .comment | grep GCC
$ objdump -s --section=.comment build/mips-linux-gnu/release/t40_demo
```

## 文本处理

### sort

> 排序

|  选项   |                 功能                  |
| :-----: | :-----------------------------------: |
|   -n    |        根据字符串数值进行比较         |
|   -r    |             反向比较结果              |
| -k  val | 根据一个关键字进行排序, val为对应位置 |

### echo

> 显示

#### 选项

```shell
-n 不换行
-e 处理特殊字符
```

#### 样例

```shell
$ echo -n > $RESOLV_CONF   # >是覆盖导入 -n 不换行
$ echo -e "\033[字背景颜色；文字颜色m字符串\033[0m" 
$ echo -e "\033[44;33m hello \033[0m" 
```

#### 颜色相关

```shell
# 字颜色(30 - 37)
30m 黑色字
31m 红色字
32m 绿色字
33m 黄色字
34m 蓝色字
35m 紫色字
36m 天蓝字
37m 白色字 
# 背景颜色(40 - 47)
40 黑底
41 红底 
42 绿底
43 黄底
44 蓝底
45 紫底
46 天蓝底
47 白底
# 控制选项
\33[0m 关闭所有属性 
\33[1m 设置高亮度 
\33[4m 下划线 
\33[5m 闪烁 
\33[7m 反显 
\33[8m 消隐 
\33[30m — \33[37m 设置前景色 
\33[40m — \33[47m 设置背景色 
\33[nA 光标上移n行 
\33[nB 光标下移n行 
\33[nC 光标右移n行 
\33[nD 光标左移n行 
\33[y;xH设置光标位置 
\33[2J 清屏 
\33[K 清除从光标到行尾的内容 
\33[s 保存光标位置 
\33[u 恢复光标位置 
\33[?25l 隐藏光标 
\33[?25h 显示光标
```

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
BEGIN{ } 初始化代码块，在对每一行进行处理之前，初始化代码，主要是引用全局变量，设置FS分隔符
{ } 命令代码块，包含一条或多条命令
// 用来定义需要匹配的模式（字符串或者正则表达式），对满足匹配模式的行进行上条代码块的操作
END{ }  结尾代码块，在对每一行进行处理之后再执行的代码块，主要是进行最终计算或输出结尾摘要信息
```

```shell
$0           表示整个当前行
$1           每行第一个字段
NF          字段数量变量
NR          每行的记录号，多文件记录递增
FNR         与NR类似，不过多文件记录不递增，每个文件都从1开始
\t          制表符
\n          换行符
FS          BEGIN时定义分隔符
RS          输入的记录分隔符， 默认为换行符(即文本是按一行一行输入)
~            匹配，与==相比不是精确比较
!~           不匹配，不精确比较
==           等于，必须全部相等，精确比较
!=           不等于，精确比较
&&　         逻辑与
||              逻辑或
+              匹配时表示1个或1个以上
/[0-9][0-9]+/   两个或两个以上数字
/[0-9][0-9]*/    一个或一个以上数字
FILENAME 文件名
OFS      输出字段分隔符， 默认也是空格，可以改为制表符等
ORS        输出的记录分隔符，默认为换行符,即处理结果也是一行一行输出到屏幕
-F'[:#/]'   定义三个分隔符
```

#### 样例

```shell
# 方式1
$ awk -F" " 'command' input-file(s)
# 方式2
$ awk -f awk-script-file  input-file(s)
# $0 - 显示完全数据, $1 - 显示第一个数据, $2, $3, $4, $5
```

### sed

> sed是一个非交互性文本流编辑器
> 基本使用
> a. 显示
> b. 搜索后新增
> c. 搜索后替换

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
$ sed -e s/Last\ Changed\ Rev:\ //g //获取 SVN 上次提交的版本号
```

##### 示例01

```markdown
#define NGINX_VERSION      "1.16.1"
$ sed -e 's/^.*"\(.*\)".*/\1/') // 截取""内的参数
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

## watch - 实时监测

```shell
$ watch -d -n 1 'free'
```

## ln - 创建软连接

```shell
$ ln -s [源] [目标]
```

```shell
# 格式化分区
# ext4分区
$ mkfs.ext4 /dev/mmcblk0p11 // 海思板子
$ mount -t ext4  /dev/mmcblk0p11 /facerecodb  -o sync
# fat分区
$ mkfs.vfat /dev/mmcblk0p12
$ mount -t vfat /dev/mmcblk0p12 /facerecodb/files/
```

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

## set -x和set +x

> set -x开启执行显示
>
> set +x关闭执行显示

# 正则表达式

> 元字符,运算优先级,匹配规则

[例子](https://www.cnblogs.com/fozero/p/7868687.html)

# 判断

```shell
[ -z "$1" ]									# 判断值是否为空  空-true 非空-false
[ -n "$1" ]									# 判断值是否为空  非空-true 空-false
[ -f /usr/bin/grep ] 					    # 判断/usr/bin/grep是不是常规文件 是-true 不是-false
[ -e /var/log/syslog ] 						# 判断文件存在
[ -d /tmp/mydir ] 							# 判断目录
[ -L /usr/bin/grep ]						# 判断软连接
[ -r /var/log/syslog ] 						# 判断可读
[ -w /var/mytmp.txt ] 						# 判断可写
[ -x /usr/bin/grep ] 						# 判断可执行
```

# 函数

## 定义

```shell
fun01() {
	command
}
```

## 调用

```shell
fun01
```



## 传参

```shell
fun01 "abc"
```

## 样例

```shell
# 蓝底黄字的打印
prt_yellow() {
	echo -e "\033[44;33m $1 \033[0m" 
}

prt_yellow "${cur_path} git pull..."
```

## vim设为默认编辑器

```shell
$ echo export EDITOR=/usr/bin/vim >> ~/.bashrc 
```

## tcpdump 使用

```shell
$ tcpdump -i enp0s3 "host 192.168.1.112" -w test.pcap
```

