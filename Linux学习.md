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

   符号连接相当于创建了一个独立的文件，这个文件会让数据读取指向它连接的那个文件的文件名。软连接的特点：


- 可以连接到目录
- 可以跨文件系统
- 删除源文件后，软连接文件也就打不开了
- 符号连接文件通过->来指示具体的连接文件
- 符号连接要使用绝对路径，否则连接错误（采用拷贝软连接时会出错）

1. 硬连接

   通过文件系统的 inode 连接产生新文件名，而不是产生新文件

   inode：记录文件属性，一个文件一个inode。inode 相当于文件ID，查找文件的时候要先找到inode，然后才能读出文件的内容。

   查看硬连接信息指令：ll -i hello*

   硬连接是多个文件都指向同一个inode。具有以下特点：

- 具有相同inode的多个文件互为硬连接文件，创建硬连接相当于文件实体多了入口。
- 对于硬连接文件，只有删除了源文件以及对应的所有硬连接文件，文件实体才会被删除。
- 根据硬连接文件的特点，我们可以通过给文件创建硬连接的方式来防止文件误删除。
- 不论修改源文件还是连接文件，另一个文件的数据都会被改变。
- 硬连接不能跨文件系统。
- 硬连接不能连接到目录。

3. In 命令

   用于创建连接文件：ln[选项] 源文件 目标文件

   选项：-s 创建符号连接 

   ​            -f 强制创建连接文件，如果目标存在，那么先删除目标文件，然后再建立连接文件

     ### vim 编辑器

1.  vim 编辑器的三种工作模式

   一般模式（指令模式）：默认模式，用 vi 打开一个软件后自动进入到此模式

   编辑模式：一般模式中无法编辑文件，要编辑文件就要进入编辑模式，按下i, I, a, A, o, O, s, r等进入到编辑模式，按下ESC退出编辑模式。

   命令行模式（底行模式）：先进入到一般模式，然后输入 :、/、? 这三个中的任意一个就可以进入到命令行模式，/xxx，表示在文件中查找xxx。

2. 保存退出

   :wq 保存退出，:q 退出，:q! 不保存退出，:w 保存

3. 其他操作方式

   一般模式下，dd/ndd（删除光标所在行/删除光标所在行后的n行）、u（撤销，恢复上一步）、.（重复前一个操作）、yy（复制光标所在行）、p/P（p为复制到光标的下一行，P复制到光标的上一行）

4. 使用方式

   新建一个文件  vim hello.c

   查看文件内容  cat hello.c

### Linux C 编程

1. 编写 C 程序（编辑器）

​	使用 vim 编写程序，也可以使用VScode

2. 编译 C 程序

   使用 gcc 编译器（预处理->汇编->编译->链接）编译 C 程序。针对ARM架构代码采用的是交叉编译器

### make 工具和 Makefile 的引入

1. make 工具和 Makefile 文件的引入

   当源文件比较多的时候就不适合通过直接输入 gcc 命令来编译，这时需要一个自动化的编译工具。

   make：一般说 GNU Make，是一个软件，用于将源代码文件编译为可执行的二进制文件，make工具主要用于完成自动化编译。make 工具编译的时候需要MakeFile文件提供编译文件。

   MakeFile：make 工具所使用的文件，MakeFile 指明了编译规则。


### Makefile 基本语法

1. Makefile 规则格式

   目标：依赖文件集合...(如果依赖文件中的任何一个有更新，那么目标也会更新)

   ​	命令1（必须以Tab键开始，不能使用空格）

   ​	命令2

   e.g. main: main.o input.o calcu.o

​       		gcc -o main main.o input.o calcu.o

​		main.o: main.c

​			gcc -c main.c

​		input.o: input.c

​			gcc -c input.c

​		calcu.o: calcu.c

​			gcc -c calcu.c

​		clean: 

​			rm  *.c

​			rm main

**变量支持：** 

objects = main.o input.o calcu.o

main: $(objects)

​	gcc -o main $(objects)

**模式规则：** 添加通配符

%.o: %.c

​	gcc -c $<

**自动化变量** 

| 自动化变量 |                             描述                             |
| :--------: | :----------------------------------------------------------: |
|     $@     | 规则中的目标集合，在模式规则中有多个目标时表示匹配模式中定义的目标集合 |
|     $<     | 依赖文件集合中的第一个文件，如果依赖文件以模式定义的，符合模式的一系列文件集合 |
|     $^     | 所有依赖文件的集合，如果依赖文件中有多个重复的文件，去除重复的依赖文件，值保留一份 |

**伪目标：** 

一般目标名都是要生成的文件，而伪目标不代表真正的目标名，在执行 make 命令的时候通过指定这个伪目标来执行其所在规则的定义的命令。

使用伪目标主要是为了避免 Makefile 中定义的只执行命令的目标和工作目录下的实际文件出现名字冲突

.PHONY: clean

clean: 

​	rm  *.c

​	rm main

2. make 执行过程
   1) make 命令会在当前目录下查找以 Makefile 命名的文件
   2) 按照 Makefile 文件中定义的规则去编译生成最终的目标文件
   3) 当发现目标文件不存在或者目标所依赖的文件比目标文件新的话就会执行后面的命令来更新目标。

3. Makefile 好处

   自动化编译，通过make 命令即可完成整个工程的编译，极大地提高了开发效率。

### shell 脚本

1. 定义

   shell 脚本类似 windows 的批处理文件，shell脚本就是将连续执行的命令写成一个文件。shell 脚本提供数组、循环、条件判断等功能。

2. 写法

   shell 脚本是个纯文本文件，命令从上到下，一行一行开始执行。shell 脚本扩展名为.sh。shell 脚本第一行一定要为：

   ```python
   #!/bin/bash         //表示使用bash
   echo "hello world!" //在屏幕上显示字符串
   ```

3. 运行

   ls my.sh -l                // 查看脚本的权限

   chmod 777 my.sh  // 添加可执行权限

   ./my.sh                    // 运行脚本

4. shell 脚本语法

   1）交互式 shell 脚本

   输出-echo 输入-read 

​	2）shell 脚本的数值计算

​	shell 仅支持整形，数值计算使用$((表达式))

​	3）test 命令

​	test 命令用于查看文件是否存在、权限等信息，可以进行数值、字符、文件三方面的测试

​	&& 和 || 命令

​	cmd1 && cmd2 当 cmd1 执行完并正确，那么cmd2开始执行，如果cmd1执行完毕错误，那么cmd2不执行

​	cmd1 || cmd2 当cmd1执行完毕并正确，那么cmd2不执行，反之cmd2执行

​	4）中括号[ ]判断符

​	[ "$firststr " == "$secondstr" ] && echo "firststr == secondstr" || echo "firststr != secondstr"

​	5）默认变量

​	$0 - $n，表示 shell 脚本的参数，包括 shell 脚本命令本身，shell 脚本命令本身为$0

​	$#，#表示最后一个参数的标号

​	$@，表示$1、$2、$3......（整个参数内容）

### shell 脚本条件判断、函数和循环

1. shell 脚本条件判断

   ```python
   if 条件判断 ；then 
   // 判断成立要做的事情
   	echo "your input is Y"
       exit 0
   fi
   
   if 条件判断 ；then
   // 条件判断成立要做的事情
   else
   // 条件判断不成立要做的事情
   fi
   
   if 条件判断 ；then
   // 条件判断成立要做的事情
   elif 条件判断；then
   // 条件判断成立要做的事情
   else
   // 条件判断不成立要做的事情
   fi
   
   case $变量 in
   "第1个变量内容")
   	程序段
       ;; //表示该程序块结束！！！
   "第2个变量内容")
   	程序段
       ;;
   "第n个变量内容")
   	程序段
       ;;
   esac
   ```

2. shell 脚本函数

   ```python
   function fname(){
       //函数代码段
   }
   ```

3. shell 循环

   ```python
   // 当条件成立的时候一直循环，直到条件不成立
   while[ 条件 ]
   do   //循环开始
   	//循环代码段
   done
   
   // 条件不成立的时候循环。条件成立以后就不循环了
   until[ 条件 ]
   do
   // 循环代码段
   done
   
   //for循环，使用for循环可以知道循环次数
   for var（变量） in con1 con2 con3......（变量的值）
   do 
   	//循环代码段
   done
   
   //for循环数值处理
   for((初始值；限制值；执行步长))
   do 
   	//循环代码段
   done
   ```

   

​	
