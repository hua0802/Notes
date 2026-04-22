# Linux学习

## 【第一期】Ubuntu入门篇

###  Ubuntu 终端操作与Shell命令

|       命令        |                   用途                   |
| :---------------: | :--------------------------------------: |
|        ls         |               目录查看命令               |
|       ls -a       | 显示目录下所有文件及文件夹，包括隐藏文件 |
|       ls -l       |      显示所有文件及文件夹的详细信息      |
|        cd         |                 切换目录                 |
|        pwd        |               显示当前路径               |
|       uname       |               系统信息查看               |
|     uname -a      |             查看全部系统信息             |
|       clear       |                 清理屏幕                 |
|        cat        |               查看文件内容               |
|       sudo        |            切换用户身份为root            |
|      sudo su      |          切换用户名称（不建议）          |
|       touch       |                 创建文件                 |
|        cp         |                   拷贝                   |
|      rm  -rf      |                   删除                   |
|       mkdir       |                创建文件夹                |
|       rmdir       |                 目录删除                 |
|        mv         |            移动文件（重命名）            |
|     ifconfig      |             显示网络配置信息             |
|      reboot       |                 重启系统                 |
|     poweroff      |                 关闭系统                 |
|        man        |      系统帮助信息（某个函数的意思）      |
|       sync        |      （缓冲区）数据同步写入磁盘命令      |
| find -name 文件名 |                 查找文件                 |
|       grep        |                 查找内容                 |
|        du         |               查看文件大小               |
|        df         |                 磁盘检查                 |
|  gedit + 文件名   |        打开某个文件，可以进行编辑        |
|        ps         |           当前系统进程查看命令           |
|        top        |           进程实时运行状态查看           |
|       file        |           查看文件类型详细信息           |

### Ubuntu 软件安装

1）APP Store安装（Ubuntu软件）

2）sudo apt-get install git

3）sudo dpkg -i xxxx.deb（deb软件包安装）

4）自己下载程序源码编译安装 make（编译） make install（安装）

### Ubuntu 的文件系统结构

1）/bin 存放二进制可执行文件，这些命令在单用户模式下也能够使用，可以被root和一般账号使用。

2）/boot Ubuntu内核和启动文件（vmlinuz-xxx，grub引导装载程序）

3）/dev 设备驱动文件

4）/etc 存放系统配置文件，比如用户账号和密码文件，各种服务的起始地址

5）/home 系统默认的用户主文件夹，一般创建用户的时候，默认的用户主文件夹都会放在此目录下

6）/lib 存放库文件

7）/media 存放可插拔设备，比如SD卡或者U盘

8）/mnt 用户可使用的挂载点，如果要挂载一些额外的设备，那就可以挂载到此处

9）/opt 可选的文件和程序存放目录，给第三方软件放置的目录

10）/root root用户目录，系统管理员目录

11）/sbin 和/bin类似都是存放一些二进制可执行文件，sbin下面一般是系统开机过程中所需要的命令

12）/srv 服务相关目录，比如网络服务

13）/sys 记录内核信息，虚拟文件系统

14）/tmp 临时目录

15）/var 存放一些变化的文件，比如日志文件

16）/usr UNIX Software Resource 的缩写，存放与系统用户有关的文件，会占用很大的存储空间

17）/proc 虚拟文件系统，数据放置到内存中，存放系统运行信息

- **绝对路径：** 从根目录/算起的路径


- **相对路径：** 相当于目前路径的文件名写法 ./home/kun

### Ubuntu下的磁盘管理

1）/dev/sd\*文件是磁盘设备文件，并不能直接访问磁盘，必须要将磁盘挂载到某一个目录下才可以访问

/dev/sdb表示U盘，/dev/sdb1表示U盘的第一个分区

2）df 列出文件系统的整体磁盘使用量，主要查看整个文件系统的使用量

​     du 评估文件系统的磁盘使用量，主要查看单个文件的大小。

3）磁盘的挂载和卸载

mount和umount命令

mount /dev/sdb1 /media/kun/udisk（挂载点）

4）磁盘分区

fdisk命令： fdisk -l（查看当前分区情况）

5）磁盘格式化

磁盘分区创建好之后就可以格式化磁盘（给每个分区按上文件系统），mkfs -t vfat /dev/sdx

### Ubuntu下的压缩与解压缩

1. Linux下常用的压缩扩展名：.tar、.tar.bz2、.tar.gz

2. gzip压缩工具（压缩和解压缩.gz格式的压缩包）

   gzip xxx  //压缩

   gzip -d xxx.gz   //解压缩

   gzip -r xxx   //对文件夹内的文件进行压缩

   gzip -rd xxx.gz //对文件夹内的文件进行解压缩

   gzip虽然可以对文件夹进行压缩，但是并不能提供打包的服务，只是对文件夹中所有文件进行了单独压缩

3. bzip2压缩工具

   和gzip类似，只是bzip2工具负责压缩和解压缩.bz2格式的压缩包

   bzip2 -z xxx  //压缩

   bzip2 -d xxx.gz  //解压缩

4. **tar打包工具** 

   tar工具提供打包服务，就是将多个文件打包

   -f 使用归档文件或ARCHIVE设备

   -c 创建新归档，创建压缩文件

   -x 从归档中解出文件，解压缩

   -j 使用bzip2压缩格式

   -z 使用gzip压缩格式

   -v 打印出命令执行过程

   tar -vcf test test.tar   //将test打包成test.tar

   tar -vxf test.tar  //解包

   **1）对.tar.bz2进行压缩和解包** 

   tar -vcjf xxx.tar.bz2 xxx   //压缩

   tar -vxjf xxx.tar.bz2          //解压缩

   **2）对.tar.gz进行压缩和解压缩** 

   tar -vczf xxx.tar.gz   xxx   //压缩

   tar -vxzf xxx.tar.gz           //解压缩

5. 其他压缩格式

   1）.rar格式

   sudo apt-get install rar

   rar x xxx.rar    //解压缩

   rar a xxx.rar xxx //压缩

   2）.zip格式

   zip -rv xxx.zip xxx   //压缩

   unzip -v xxx.zip      //解压缩

### Ubuntu用户与用户组

#### Linux用户

linux是多用户操作系统，不同的用户拥有不同的权限。可以查看和操作不同的文件。Ubuntu有三种用户：

1）初次创建的用户

2）root 用户

3）普通用户

- 初次创建的用户权限比普通用户多，但是没有root用户多。
- Linux用户记录在/etc/passwd这个文件内
- Linux用户密码记录在/etc/shadow这个文件内
- 每个用户都有个ID，叫做UID

####  Linux用户组

为了方便管理，将用户进行分组。这样做就可以设置非本组人员不能访问某些文件，每个用户可以属于多个不同的组。因此，用户和用户组的存在就是为了控制文件的访问权限。

每个用户组都有一个ID，叫做GID

用户组的信息存储在/etc/group文件中

####  创建用户和用户组

1. 通过图形化界面创建

   sudo apt-get install gnome-system-tools

2. 命令创建用户

​       1）添加用户：adduser命令

​	2）用户查询：finger命令

​	3）修改用户密码：passwd +用户名

​	4）删除用户：deluser命令

​	5）创建用户组：addgroup

​	6）显示组内用户：groups

​	7）删除用户组：delgroup

### 文件权限管理

1. 文件的三种状态

   读-r（4-100），写-w（2-010），执行-x（1-001）

e.g. a.c文件信息：查看指令：ls a.c -l

设备类型（b-块设备，c-字符设备）rw- (所属用户权限) rw- (用户组成员权限) r-- (其他用户)

编译.c文件：gcc hello.c -o hello(可执行文件)

执行.c文件：./hello

2. 修改文件权限

   chmod命令  chmod 777 hello

3. 修改文件所属用户

    chown 命令  

    sudo chown root hello 更改所属用户为root

​        sudo chown .root hello 更改用户组为root

​	sudo chown root.root hello 同时更改用户和用户组为root

### Linux 连接文件

1. 符号连接（软连接）

   类似 Windows 下的快捷方式

2. 硬连接

   通过文件系统的 inode 连接产生新文件名，而不是产生新文件

   inode：记录文件属性，一个文件一个inode。inode 相当于文件ID，查找文件的时候要先找到inode，然后才能读出文件的内容。

   硬连接是多个文件都指向同一个inode。具有以下特点：

- 具有相同inode的多个文件互为硬连接

3. In 命令

   用于创建连接文件：ln[选项] 源文件 目标文件

   选项：-s 创建符号连接 

   ​            -f 强制创建连接文件，如果目标存在，那么先删除目标文件，然后再建立连接文件

​            

