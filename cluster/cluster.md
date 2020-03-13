大型网站并发架构



##### LoadBalance 负载均衡集群：提高并发能力

硬件：F5 BIG-IP ，Netscaler

软件：LVS（4层），Nginx/Tengine（7层），Haproxy（7层）



##### High Availability：以在线时间为根本

99%，99.9%，99.99%

Keepalived，RHCS，Pacemaker，rose（windows），PowerHA（AIX）



##### High-Performance Computing：解决大任务计算问题

MapReduce，Hadoop



LVS：四层LB

NAT

DR

TUN

FULL-NAT



NAT实验：

1、准备工作，集群中所有主机

IP，hostname,hosts,iptables,firewalld,SELinux,ssh trust,ntp

2、RS配置

所有网关指向DIP

3、Director配置

添加DIP

开启内核转发

定义LVS的分发策略

