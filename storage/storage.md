存储技术

DAS：直接附加存储

存储本身没有控制器

可通过SCSI线，SAS线，FC线连接

NAS：网络附加存储

SAN：存储区域网络



NFS

服务端

```
/dev/sda														OS
/dev/sdb1								1T		EXT4	/project1
/dev/datavg/project2		20T		XFS		/project2

rpm -q nfs-utils

vim /etc/exports
/project1			172.16.100.0/24(rw,sync,no_root_squash)
/project2			172.16.200.10(rw,sync,no_root_squash)

exportfs -r
exportfs -v
```

客户端

```
shomount -e storage_IP

vim /etc/fstab
storage_IP:/project1		/var/www/html		nfs		default 	0 0
mount -a

automount
```



iSCSI

```
yum -y install targetcli

vim /etc/tgt/targets.conf


```

实验

linux系统iSCSI

Openfiler

Windows



FC SAN

```shell
lspci |grep fibre

dmesg |grep -i fib

cat /sys/class/fc_host/host3/port_name
```



Udev:dynamic device management

用途

1、为设备设置自定义设备名

​	连接到主机主板总线上的设备（存储设备，网络设备）

​	通过网络连接的SAN设备

2、可以解决多个节点发现的存储设备名不一致问题

3、没有多路径功能

4、可以用于IP/FC SAN中

功能：

1、动态管理

2、自定义命名规则

3、设定设备的权限和所有者

```shell
CentOS6/RHEL 6
udevadm info -a -p /block/sdb  # 查看信息

vim /etc/udev/rules.d/100-san.rules
SUBSYSTEM=="block",ATTR{size}=="43881772",ATTRS{vendor}=="dell",MODE="0777",OWNER="test",SYMLINK+="san1"

start_udev
```



Mulitpath多路径

```
yum install device-mapper-multipath

cp /usr/share/doc/device-mapper-multipath*.*.*/multipath.conf /etc/.
```



