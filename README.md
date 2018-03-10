# Everyday-Record
<font size=4>
记录每天遇到的问题以及解决方法，学习上的东西记录(从2018-2-28开始-)，采用的是倒序，从最新的开始。

----------

# 2018年3月10日
## 1、makefile文件的规则与编写
（1）规则：
> 目标（target）: 目标文件1 目标文件2
> 
>  &emsp;&emsp;gcc -o 打算建立的执行文件 目标文件1 目标文件2
 
（2）例子：
> main : main.o haha.o sin_value.o cos_value.o<br/>
> &emsp;&emsp;    gcc -o main.o haha.o sin_value.o cos_value.o<br/>
> clean : <br/>
> &emsp;&emsp;   rm -f main main.o haha.o sin_value.o cos_value.o

(3)进一步举例：
> LIBS = -lm<br/>
> OBJS = main.o haha.o sin_value.o cos_value.o<br/>
> CFLAGS = -Wall
> main:${OBJS}<br/>
> &emsp;&emsp;  gcc -o $@ ${OBJS} ${LIBS}<br/>
> clean:<br/>
> &emsp;&emsp;  rm -f main ${OBJS}
	
其中$@代表的是目前的目标target

## 2、 树莓派与ubuntu 16.04 的交叉编译步骤
（1）在Ubuntu中下载交叉编译工具
>	git clone https://github.com/raspberrypi/tools.git

注意：虚拟机Git下载一般很不稳定，所以，建议直接用电脑下载，然后复制到虚拟机里面解压即可。

（2）切换到tools目录中
> cd tools/arm-bcm2708

（3）查看里面的内容，如下图
![](https://i.imgur.com/lkFqHRS.jpg)

树莓派对应的是红色框框中的arm-linux-gnueabihf架构

（4）复制一份到/opt目录下，以防止用户变化不能使用
> cp -r arm-bcm2708/ /opt/

（5）加入环境变量
>  export PATH=/opt/arm-bcm2708/arm-linux-gnueabihf/bin/:$PATH

（6）配置编译参数
> export CFLAGS="-O2 -pipe -mcpu=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -w"

（7）切换到/root目录，更新当前环境变量
> cd ~
> source .bashrc

（8）测试环境变量是否生效
> arm-linux-gnueabihf-gcc -v
> 
> ![](https://i.imgur.com/QQXdWru.jpg)
出现如下版本号，就代表安装完成

（9）创建目录pi_test，并测试交叉编译是否完成
> 编写hello.c和makefile文件
>
> hello.c文件
>
> ![](https://i.imgur.com/7A9pR7F.jpg)

> makfile文件
>
> ![](https://i.imgur.com/Mp4ZyyK.jpg)

（10）make一下，将生成的hello发送给树莓派运行
> ![](https://i.imgur.com/A3P1ciJ.jpg)


----------

# 2018年3月9日
## 1、Linux中gcc -L/path 和 -I/path的意思是什么？
-L/path:意思是指定要找到的lib的目录，如-L/lib,-L/lib64;<br/>
-I/path:意思是指定要找的include文件，默认值是放在/usr/include底下，如：-I/usr/include

## 2、gcc的一些用法
（1）gcc -c hello.c
> 会自动产生hello.o这个文件，但是并不会产生二进制行文件

（2）gcc -O -c hello.c
> 会自动产生hello.c这个文件，并进行优化

（3）gcc sin.c -lm -L/lib -I/usr/include
> 会产生二进制文件；-lm：指定的是libm.so 或 libm.a这个函数库文件；-L 后面接的路径是函数库的搜寻目录；-I接的路径是源码内include文件之所在目录

（4）gcc -o hello hello.c
> -o后面接的是要输出的二进制文件名

（5）gcc -o hello hello.c -Wall
> -Wall 是出现更多的编译信息
> 
 

----------

# 2018年3月8日

## 1、笔记记录
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

## 3、armhf是什么？
armel：也即softfp，用浮点运算单元（fpu）计算，但是传参数用普通寄存器传，这样中断的时候，只需要保存普通寄存器，中断负荷小，但是参数需要转换成浮点的再计算。

armhf：也即hard，用fpu计算，传参数用fpu中的浮点寄存器传，省去了转换性能最好，但是中断负荷高。

## 4、armv7l和armv7hl是什么？
h——hard-float，指浮点运算直接由CPU（APU）完成，而不用通过软件库编译成定点算法实现，对应的是soft-float。

 l——little-endian。

## 5、树莓派交叉编译的官方网址
<https://redmine.named-data.net/projects/ndn-embedded/wiki/Cross-compiling_NDN_projects_for_Raspberry_Pi>




----------

# 2018年2月28日

## 1、 树莓派中c++调用python，遇到找不到“Python.h”文件?

## 2、在apt-get install被中断，重新输入apt-get install xxx是会报错，如下图
 方法： 切换到cd /var/lib/dpkg目录下，然后删除lock文件即可，rm lock.

## 3、 Linux删除目录指令
 方法：rm -rf 目录名

## 4、gcc -Wall 的作用
方法：-Wall的作用就是显示所有的警告信息。

## 5、sudo apt-get update 和 upgrade的作用和区别？
(1)sudo apt-get update :这个命令，会访问源列表里的每个网址，并读取软件列表，然后保存在本地电脑。我们在新立得软件包管理器里看到的软件列表，都是通过update命令更新的.<br/>
(2)sudo apt-get upgrade:这个命令，会把本地已安装的软件，与刚下载的软件列表里对应软件进行对比，如果发现已安装的软件版本太低，就会提示你更新。如果你的软件都是最新版本，<br/>
**总而言之，update是更新软件列表，upgrade是更新软件。**





