### Linux基本命令
##### 文件权限属组和属主
- chgrp命令: chgrp 属组 文件名

			- 可以改变文件或文件夹属组  -r 可以使文件夹下所有文件全部改变属组
- chown命令: chown 属主 文件名

			- 可以改变文件或文件夹属主
- chmod命令: chmod 权限值rwx 文件或目录

			- 可以改变文件的读写执行(rwx)
			- 还可以通过 +-=来赋值  格式：chmod u=rwx,g+w,o-r 文件名
- ls命令

			- 参数：
				1. -l 长数据列出，包含文件本身属性和权限
				2. -a 全部的文件包括隐藏文件
				3. -d 仅列出目录，而不是目录内的文件属性
- cd命令
- pwd命令

			- 参数: -P显示确实路径，而非link路径
- mkdir命令

			- 参数：
				1. -m 配置文件夹的权限
				2. -p 递归创建目录
- rmdir命令

			1. -p 删除文件下面的空目录
- cp命令

			1. -a 相当于 -pdr的集合 (常用)
			2. -d 来源为连接档，则复制链接档属性而不是文件本身
			3. -f 强制复制，若目标文件已存在，则移除后再复制
			4. -i 若目标档(destination)已经存在时，在覆盖时会先询问动作的进行(常用)
			5. -l 进行硬式连结(hard link)的连结档创建，而非复制文件本身；
			6. -p：连同文件的属性一起复制过去，而非使用默认属性(备份常用)；
			7. -r：递归持续复制，用於目录的复制行为；(常用)
			8. -s：复制成为符号连结档 (symbolic link)，亦即『捷径』文件；
			9. -u：若 destination 比 source 旧才升级 destination ！
- rm命令

			1. -r 递归删除
			2. -f 强制删除
			3. -i 互动模式，询问是非删除
- mv命令

			1. -f ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖
			2. -i ：若目标文件 (destination) 已经存在时，就会询问是否覆盖！
			3. -u ：若目标文件已经存在，且 source 比较新，才会升级 (update)
	### grep命令 搜索命令
		-i 忽略大小写
		-n 输出行号
		-v 反向查找
		--auto=auto 显示颜色
	#### 文件内容查看命令
		- cat 从第一行文本开始查看
			1. -A ：相当於 -vET 的整合选项，可列出一些特殊字符而不是空白而已；
			2. -b ：列出行号，仅针对非空白行做行号显示，空白行不标行号！
			3. -E ：将结尾的断行字节 $ 显示出来；
			4. -n ：列印出行号，连同空白行也会有行号，与 -b 的选项不同；
			5. -T ：将 [tab] 按键以 ^I 显示出来；
			6. -v ：列出一些看不出来的特殊字符
		- tac 从最后一行开始往看前看
		- nl 输出的时候显示行号
			1. -b ：指定行号指定的方式，主要有两种：
			2. -b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)；
			3. -b t ：如果有空行，空的那一行不要列出行号(默认值)；
			4. -n ：列出行号表示的方法，主要有三种：
			5. -n ln ：行号在荧幕的最左方显示；
			6. -n rn ：行号在自己栏位的最右方显示，且不加 0 ；
			7. -n rz ：行号在自己栏位的最右方显示，且加 0 ；
			8. -w ：行号栏位的占用的位数。
		- more 一页一页显示
			1. 空白键 (space)：代表向下翻一页；
			2. Enter         ：代表向下翻『一行』；
			3. /字串         ：代表在这个显示的内容当中，向下搜寻『字串』这个关键字；
			4. :f            ：立刻显示出档名以及目前显示的行数；
			5. q             ：代表立刻离开 more ，不再显示该文件内容。
			6. b 或 [ctrl]-b ：代表往回翻页，不过这动作只对文件有用，对管线无用。
		- less 一页显示可以往前翻页
			- 空白键    ：向下翻动一页；
			- [pagedown]：向下翻动一页；
			- [pageup]  ：向上翻动一页；
			- /字串     ：向下搜寻『字串』的功能；
			- ?字串     ：向上搜寻『字串』的功能；
			- n         ：重复前一个搜寻 (与 / 或 ? 有关！)
			- N         ：反向的重复前一个搜寻 (与 / 或 ? 有关！)
			- q         ：离开 less 这个程序
		- head 只看前几行
			-n ：后面接数字，代表显示几行的意思
		- tail 只看后几行
			-n ：后面接数字，代表显示几行的意思
			-f ：表示持续侦测后面所接的档名，要等到按下[ctrl]-c才会结束tail的侦测
	###### 添加用户和用户组
		- useradd
			 参数: useradd 选项 用户名
			 	-c comment 指定一段注释性描述。
				-d 目录 指定用户主目录，如果此目录不存在，则同时使用-m选项，可以创建主目录。
				-g 用户组 指定用户所属的用户组。
				-G 用户组，用户组 指定用户所属的附加组。
				-s Shell文件 指定用户的登录Shell。
				-u 用户号 指定用户的用户号，如果同时有-o选项，则可以重复使用其他用户的标识号

				# useradd -s /bin/sh -g group –G adm,root gem
				此命令新建了一个用户gem，该用户的登录Shell是 /bin/sh，它属于group用户组，同时又属于adm和root用户组，其中group用户组是其主组。
				这里可能新建组：#groupadd group及groupadd adm
				增加用户账号就是在/etc/passwd文件中为新用户增加一条记录，同时更新其他系统文件如/etc/shadow, /etc/group等。
				Linux提供了集成的系统管理工具userconf，它可以用来对用户账号进行统一管理。
		- userdel
			 参数: userdel 选项 用户名
			 	-r，它的作用是把用户的主目录一起删除。
		- usermod 
			 参数：usermod 选项 用户名
			 	-l 新用户名
			 	其他参数和useradd命令相同
				# usermod -s /bin/ksh -d /home/z –g developer sam
				此命令将用户sam的登录Shell修改为ksh，主目录改为/home/z，用户组改为developer。
		1.修改用户组groupmod
			-groupmod -g GID: 修改组ID
			-n 新组名 		  修改组名
		2.删除 groupdel
		3.添加 groupadd 
			-groupadd -g 添加组ID
		4.gpasswd
			-gpasswd -a 把用户加入组 附加组
			-gpasswd -d 把用户从组中删除

### 用户口令管理
			- passwd 选项 用户名
				-l 锁定口令，即禁用账号。
				-u 口令解锁。
				-d 使账号无口令。
				-f 强迫用户下次登录时修改口令。
			- chage
				-l 查看用户的详细密码状态
				-d 日期 设置为0 登录就修改没密码
				-m 天数
				-M 密码有效期
				-W 密码过期前的警告天数
				-I 密码过期后的宽限天数
				-E 日期 账号失效的时间
			vi /etc/passwd
			vi /etc/shadow
			vi /etc/group
			vi /etc/gshadow
			rm /home/
1.shadow文件

			 - 第一个字段是用户名 
			 第二个字段是密码 第三个字段是修改密码的时间 第四个字段是两次密码修改的间隔时间 第五个字段是密码有效期  第六个字段密码失效前的提示 第七个字段是密码到期之后的宽限时间 第八个字段是账号失效的时间 用时间戳表示
			 第九个字段是保留
2.用户模板目录

			/etc/skel/  新建用户后会把这里面的文件复制到用户目录下
2.1用户默认值文件

				/etc/default/useradd
				密码配置文件
				/etc/login.defs
3.su命令

			su - 用户名 切换用户
			su -root -c "useradd name" 不切换用户执行命令
## vim命令
	-  a A  a在字符后插入  A在字符所在行行尾插入
	-  i I  i在字符前插入  I在字符所在行行首插入
	-  o O	o在光标下插入新行 O在光标上插入新行
	- set number 设置行号
	- set nonumber 取消行号
	- gg 到第一行
	- G 到最后一号
	- nG 到哪一行
	- :n 指定哪一行
	- x 删除光标所在处字符
	- nx 删除光标后指定范围字符
	- dd 删除当前行
	- ndd 删除指定范围行
## 网络命令
	1.last 可以看登录日志
	2.traceroute 显示数据包到主机之间的路径
	3.netstat -t TCP协议 -u UDP协议 -l 监听 -r 路由 -n 显示IP地址和端口
	- yum install net-tools 安装netstat
	4.nmtui centos7才可以使用图形配置网络
## 软件包
1.软件包分类

		- 源码包
			脚本安装包
			优点：
			开源 可以修改源代码
			软件是编译安装 更加适合自己的系统 更加稳定效率也更高
			卸载方便
			缺点：
			安装过程多，环境搭建容易出错
			编译过程时间教程
		- 二进制包(rpm包)
		缺点：
			依赖性
			不能看到源代码
			功能选择不灵活
		优点：
			安装速度快
2.rpm命令

		-rpm 安装 rpm -ivh
			-i (instal)安装
			-v 显示详细信息
			-h (hash)显示进度
3.yum命令

			``如果出现PYCURL ERROR 6 - "Couldn't resolve host 'mirrorlist.centos.org'"
			Error: Cannot find a valid baseurl for repo: extras
			可能是DNS没有配置好``
		- yum list 查询所有可以用软件包列表
		- yum search 查询软件包关键字
		- yum -y install 自动回答yes
		- yum -y update 包名 升级
		- yum -y remove 包名 卸载
		- yum grouplist  组安装
		- yum groupinstall 软件包组
		- yum groupremover 卸载
3.1 光盘挂载yum源

			- 挂载光盘
				mount /dev/cdrom /mnt/cdrom
			- 对yum源文件改名
			- 修改光盘yum源文件
			- enabled 改为1  光盘挂载点
4.源码包

		安装在指定位置
		不能通过系统服务管理命令启动
		默认路径在 /usr/local/下面
### ACL权限
1.查询文件分区详细分区 磁盘详细信息

		- dumpe2fs -h url 
1.1 临时开启分区ACL权限

		mount -o remount,acl /
1.2永久开启ACL分区

		vi /etc/fstab  defaults默认打开acl
			UUID=..../ ext4 defaults.acl
		mount -o remount,/  重新挂载分区
2.查看ACL命令

		getfacle 文件名
2.1设定ACL权限命令

		setfacl 选项 文件名
		-m 设定权限
		-x 删除指定权限
		-b 删除所有权限
### chattr 命令
-lsattr 查看权限命令

	- +i -i 对文件使用 那么不允许对文件进行改名，删除，修改，对文件夹使用 只允许对文件下的数据只能修改不能建立或者删除
	- +a -a对文件设置a属性，只能在文件中增加数据，不能删除和修改，对目录使用，只允许建立和修改文件数据 
-sudo权限 操作对象是系统命令

### 文件系统命令
1.df -h 查看分区  考虑文件和命令、程序的占用空间

2.du -h 目录名 -s统计总大小  只考虑文件
#### 挂载命令
	- mount [-t 文件系统] [-L 卷标名] \[-o 特殊选项]
	设备文件名 挂载点 
	-t iso9660 ext3、ext4 文件系统
	-o remount 重新挂载已经挂载的文件系统 一般用于特殊权限
	exec 执行/不执行 设定是否允许在文件系统中支持可执行文件 noexec 不执行
	- ntfs 挂载需要下载插件
#### fidsk分区
	fdisk /dev/sdb
## shell
1

	- dos2unix 把Windows转换Linux格式
2.历史命令

	- history [选项] []
		-c 清空历史命令
		-w 把缓存中的命令保存
		/~/.bash_history
	可以在环境变量中设置保存条数
	/etc/profile.d
	!n 可以重复执行第n条命令
	!! 重复执行上一条命令
3.系统命令别名

		临时生效
		- alias 别名="命令"
		- alias 查看别名
		永久生效
		- vi /root/.bashrc
4.输出重定向

		命令 > 文件 覆盖
		命令 >> 文件 追加
		把文件输出结果不管正确还是错误都追加到文件里
		命令 &>> 文件 追加
		把正确的文件保存到文件1 错误的保存到文件2
		命令 >> 文件1 2>> 文件2
5.输入重定向

		wc [选项][文件名]
		-c 统计字节数
		-w 统计单词数
		-l 统计行数
#### 通配符
	? 匹配一个任意字符
	* 所有
	[] 匹配中括号中任意一个字符
	[-] [a-z] 匹配任意一个小写字母
	[^] 取反 [^1-9]匹配不是1-9的数字
## 变量
1.局部变量

		- name=123 //赋值
		- set //查看
		- unset $name 删除变量
2.全局变量

		- export name 定义全局变量
		- env 查询变量
		- unset name 删除
3.预定义变量

		- $$ 当前程序的PID
		- &? 上一条运行的PID号
		- $! 最后一次命令执行的状态 正确为0
4.接受键盘输入

		read [选项] [变量名]
		-p 提示信息
		-t 等待时间
		-n 字符数 接受指定的字符数就会执行
		-s 隐藏输入的数据
5.数字加减

		declare 声明变量类型
		-: 给变量设定类型属性
		+: 取消变量
		-i: 将变量设定为整数型
		-x: 将变量声明为环境变量
		-p: 显示声明变量的类型
		expr或let 数字运算工具
		$((运算式))
		- 变量测试与替换
			x=${y-新值} 变量替换
### 环境变量配置文件
	source 配置文件 或 . 配置文件
	/etc/profile 对所有用户生效
	/etc/profile.d/*sh
	~/.bash_profile 对当前用户生效
	~/.bashrc
	/etc/bashrc
2.shell登录信息

		/etc/issue
### shell
1.字符串截取

- cut [选项] 文件名 -f 列名 -d 分隔符

- printf '输出类型输出格式' 输出内容 格式化输出命令

			输出类型:
				%ns: 输出字符串 n代表输出几个
				%ni 输出整数
				%m.nf 输出浮点型
			输出格式：
				\a 警告声音
				\n 换行
				\r 回车
				\t tab键
- awk 命令

			awk '条件1{动作1} 条件2{动作2}' 文件名
			{FS=":"}指定分隔符
			加上BEEGIN 在命令开始前执行
			END 在命令执行完后执行
- sed 命令

			sed[选项]'[动作]' 文件名
			-n 只会把经过sed命令处理的行输出到屏幕
			-e 允许对输入数据应用多条sed命令编辑
			-i 用sed的修改结果直接修改读取数据文件
			动作
				a \: 追加
				c \: 替换
				i \: 插入
				d: 删除
				p: 打印
				s: 替换 sed 's/旧数据/新数据/g'
2.排序命令sort

			- sort [选项] 文件名
				-f 忽略大小写
				-r 倒序
				-t 指定分隔符
				-n 以数字开始排序
3.统计命令wc

			- wc [选项] 文件名
				-l 只统计行数
				-w 只统计单词数
				-m 只统计字符数
4.条件判断

			-d 判断文件是否存在 是否为目录(是目录为真)
			-e 判断是文件是否为存在
			-f 判断文件是否存在 是否为文件(是文件为真)
			按照文件权限进行判断
			-r	读
			-w	写
			-x	执行
			文件1 -nt 文件2 修改时间是否比文件2新(如果新 为真)
			-ot (如果旧为真)
			-df 通过node号判断是否是同一个文件
5.if语句

			if [条件判断式] 
				then
					程序
				elif
					then
				else

				fi
6.case语句

			case $变量名 in 
				"值1")

					;;
				"值2")
					;;
			esac
7.for循环

			for 变量 in 值1 值2..
				do
					程序
				done
			for((i=1;i<20;i=i+1))
8.while循环

			while [ 条件判断式 ] 条件成立
				do

				done
			until 条件不成立
				do

				done
## Linux服务管理
   1.rpm包管理
    ![rpm_image](E:/linux/images/rpm.png)













