# LINUX下的SCP命令

相同Linux系统中对文件复制拷贝可以用CP命令：

cp [options] source dest

cp [options] source… directory

说明：将一个档案拷贝至另一档案，或将数个档案拷贝至另一目录。

-a 尽可能将档案状态、权限等资料都照原状予以复制。

-r 若 source 中含有目录名，则将目录下之档案亦皆依序拷贝至目的地。

-f 若目的地已经有相同档名的档案存在，则在复制前先予以删除再行复制。

不同的Linux之间copy文件常用有3种方法：

第一种就是ftp，也就是其中一台Linux安装ftp Server，这样可以另外一台使用ftp的client程序来进行文件的copy。

第二种方法就是采用samba服务，类似Windows文件copy 的方式来操作，比较简洁方便。

第三种就是利用scp命令来进行文件复制。

```
scp是有Security的文件copy，基于ssh登录。操作起来比较方便，比如要把当前一个文件copy到远程另外一台主机上
1
```

**从 本地 复制到 远程（都是Linux系统时）**

命令格式：
scp -r local_file remote_username@remote_ip:remote_folder
或者
scp -r local_file remote_username@hostname:remote_folder （这里使用hostname，是因为提前配置了hosts映射）
或者
scp -r local_file remote_username@remote_ip:remote_file
或者
scp -r local_file remote_ip:remote_folder
或者
scp -r local_file remote_ip:remote_file
**注：-r 是递归的意思，相当于把文件目录包括里面的内容都递归复制到目标机器**

##### 如果没有配置ssh无密登录会在输入复制命令回车后要去输入远程机器的用户登录密码

------

**从远程机器复制到本地当前操作的机器（跟上面操作反过来）remote_ip同样可以换成hostname，条件也是提前配置了hosts映射**
如：**scp -r remote_username@remote_ip:remote_file ./**
**注：**./的意思是当前所在目录，即正在操作的当前机器目录位置，也可以写成具体路径：

##### scp -r remote_username@remote_ip:remote_file local_username@hostname:local_folder

**这里的local_username和local_folder是指正在操作的机器，可能是实体物理机，也可能是虚拟机，也可能是远程机器**（正在输入要执行命令的机器）

------

**从本机操作远程机器，将远程机器文件复制到另一台远程机器（三台机器）**
**scp -r remote_username1@remote_ip1:remote_file1 username2@remote_ip2:remote_file2**
**注：**

-   remote_file1需要复制的文件既可以是文本也可以是目录，而remote_file2是用来存放remote_file1的目录（位置）
-   remote_ip可以换做hostname,前提是远程机器上做了hosts映射，把它自己的ip映射为自己的hostname
    **如：scp -r atguigu@hadoop103:/opt/software/demo.txt atguigu@hadoop104:/opt/software**(如果没有配置ssh无秘登录，会依次要求输入主机hadoop103和主机hadoop104的用户密码的)

------

从 远程 复制到 本地，只要将 从 本地 复制到 远程 的命令 的 后2个参数 调换顺序 即可；

相比于CP命令，主要就是在source跟dest之前加上remote_username@remote_ip:,通过加的位置的不同区分出到底从远程到本地还是本地到远程

可能有用的几个参数 :

-v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接 , 认证 , 或是配置错误 .

-C 使能压缩选项 .

-P 选择端口 . 注意 -p 已经被 rcp 使用 .

-4 强行使用 IPV4 地址 .

-6 强行使用 IPV6 地址 .

注意两点：
1.如果远程服务器防火墙有特殊限制，scp便要走特殊端口，具体用什么端口视情况而定，命令格式如下：
\#scp -p 4588 [remote@www.abc.com](mailto:remote@www.abc.com):/usr/local/sin.sh /home/administrator
2.使用scp要注意所使用的用户是否具有可读取远程服务器相应文件的权限。
参考：[链接:](https://blog.csdn.net/jyf0412/article/details/36866041)