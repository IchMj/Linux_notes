# Linux网络配置
### centos6网卡配置
	`DEVICE=em1
	TYPE=Ethernet
	UUID=9b333747-34c5-4e80-8a02-91c5c9bd619d
	ONBOOT=*yes*
	NM_CONTROLLED=yes
	BOOTPROTO=*none*
	HWADDR=04:7D:7B:60:0D:A4
	DEFROUTE=yes
	IPV4_FAILURE_FATAL=yes
	IPV6INIT=no
	NAME="System em1"
	IPADDR=103.57.111.137
	PREFIX=29
	NETMASK=255.255.255.248
	GATEWAY=103.57.111.142
	DNS1=8.8.8.8
	DNS2=114.114.114.114
	`
### centosC段添加
`
IPADDR_START=
IPADDR_END=
CLONENUM_START=60
NETMASK=255.255.255.0
PREFIX=24
ARPCHECK=no
`
	*centos7要在主网卡添加  NM_CONTROLLED=no*

### debian网卡配置和安装教程
	`
auto eth0
iface eth0 inet static
address 10.16.3.99
netmask 255.255.255.0
network 10.16.3.0
broadcast 10.16.3.255
gateway 10.16.3.1
	`
安装教程(https://www.jb51.net/os/618680.html)

### ubuntu网卡配置和安装教程
`
auto eth0
iface eth0 inet static
address 
netmask 
gateway 
dns-nameserver 8.8.8.8 
`
安装教程(https://blog.csdn.net/baidu_36602427/article/details/86548203#2_52)  

- 安装ssh服务
`sudo apt-get update`
`sudo apt-get insatll openssh-server`

### pve网卡配置和安装教程
安装教程(http://www.myxzy.com/m/?post=144)

*有三个地方需要改 都是网卡名*