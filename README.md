# Everyday-Record
<font size =5>
记录每天遇到的问题以及解决方法，学习上的东西记录

#2018年2月28日

## 1、 树莓派中c++调用python，遇到找不到“Python.h”文件?

## 2、在apt-get install被中断，重新输入apt-get install xxx是会报错，如下图
 方法： 切换到cd /var/lib/dpkg目录下，然后删除lock文件即可，rm lock.

## 3、 Linux删除目录指令
 方法：rm -rf 目录名

## 4、gcc -Wall 的作用
方法：-Wall的作用就是显示所有的警告信息。

##5、sudo apt-get update 和 upgrade的作用和区别？
(1)sudo apt-get update :这个命令，会访问源列表里的每个网址，并读取软件列表，然后保存在本地电脑。我们在新立得软件包管理器里看到的软件列表，都是通过update命令更新的.<br/>
(2)sudo apt-get upgrade:这个命令，会把本地已安装的软件，与刚下载的软件列表里对应软件进行对比，如果发现已安装的软件版本太低，就会提示你更新。如果你的软件都是最新版本，<br/>
**总而言之，update是更新软件列表，upgrade是更新软件。**


#2018年3月8日15:44:47

----------

##1、笔记记录<br/>
The major components of this kit are:

	
  * PyNDN: a Python implementation of NDN
  * nfd: the NDN Forwarding Daemon, which manages connections (faces)
  * nrd: the NDN Routing Daemon, which routes interests and data


There are other libraries included for further exploration of NDN:

   * repo-ng: a data repository server
   * ndn-cpp: C++ implementation of NDN
   * ndn-cxx: C++ implementation of NDN with eXperimental eXtensions


## 2、查看Linux系统架构类型

（1）uname -a：直接显示 Linux 系统架构的命令，安几乎可以工作在所有 Linux/Unix 系统当中。

（2）dpkg --print-architecture：dpkg 的命令可用于查看 Debian/ Ubuntu 操作系统是 32 位还是 64 位，此命令只适用于基于 Debian 和 Ubuntu 的 Linux 发行版。
    
 （3）getconf LONG_BIT ：getconf 命令主要用于显示系统变量配置
        
（4）arch: 命令主要用于显示操作系统架构类型，与 uname -a 命令非常类似。如果输出 x86_64 则表示为 64 位系统，如果输出 i686 或 i386 则表示为 32 位系统。           
    
（5）file /lib/systemd/systemd: 特殊参数来查看系统架构类型
（6）查看cpu信息：cat /proc/cpuinfo

##3、armhf是什么？
armel：也即softfp，用浮点运算单元（fpu）计算，但是传参数用普通寄存器传，这样中断的时候，只需要保存普通寄存器，中断负荷小，但是参数需要转换成浮点的再计算。

armhf：也即hard，用fpu计算，传参数用fpu中的浮点寄存器传，省去了转换性能最好，但是中断负荷高。

## 4、armv7l和armv7hl是什么？
h——hard-float，指浮点运算直接由CPU（APU）完成，而不用通过软件库编译成定点算法实现，对应的是soft-float。

 l——little-endian。

## 5、树莓派交叉编译的官方网址</br>
<font size = 5><https://redmine.named-data.net/projects/ndn-embedded/wiki/Cross-compiling_NDN_projects_for_Raspberry_Pi>


# 2018年3月9日
