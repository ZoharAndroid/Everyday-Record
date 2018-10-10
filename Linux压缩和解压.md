# Linux压缩和解压

#压缩后缀
![](https://i.imgur.com/SvQOoAl.png)

# gzip

 压缩
	
	gzip -v 文件名：将文件进行压缩，且这个源文件文件会被删除

 解压
	
	gzip -d 文件名：解压，压缩的文件也将被删除


----------

# bzip2

压缩
	
	bzip2 -v 文件名：压缩，源文件删除

解压

	bzip2 -d 文件名：解压，源压缩文件删除



# xz

压缩

	xz -v 文件名：压缩，源文件删除

解压

	xz -d 文件名：解压，源压缩文件删除



----------

 **以上都是针对文件进行压缩的，如果要对包含多个文件的一个文件夹进行打包，那就得用到tar打包命令，然后在使用压缩命令来进行压缩了。**

----------

## tar
![](https://i.imgur.com/wMxyUpn.png)

 

> 可以简单记忆下面简单的命令
> 
- **压 缩：tar -jcv -f filename.tar.bz2 要被压缩的文件或目录名称**
> 
>
>- **查 询：tar -jtv -f filename.tar.bz2**
> 
>
>- **解压缩：tar -jxv -f filename.tar.bz2 -C 欲解压缩的目录**
>- **备份：tar -zpcv -f filename.tar.gz 要被备份的文件或者目录** 



  **tar不会自动产生后缀名，所以需要自己在文件的后面添加，比如.tar.gz / .tar.bz2 / .tar.xz**


