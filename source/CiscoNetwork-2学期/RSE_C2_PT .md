第二章实战分析
en
conf terminal
!R1
hostname Central
ipv6 unicast-routing 
no ip domain-lookup 
int s0/0/0
description For Primary Lan
ip add 128.107.0.1 255.255.255.252
ipv add 2001:DB8:2:1::1/64
ipv add FE80::1 link-local
no sh
exit

int s0/0/1
description For Backup Lan
ip add 128.107.0.5 255.255.255.252
ipv add 2001:DB8:3:1::1/64
ipv add FE80::1 link-local
no sh
exit

int s0/1/1
description For Router
ip add 10.10.20.1 255.255.255.252
ipv add 2001:DB8:1:1::1/64
ipv add FE80::1 link-local
no sh
exit


enable secret cisco
line console 0
password class
login
exit

line vty 0 15
password class
login
exit
service pass
banner motd "you are fucking crazy"
ip route 10.10.2.0 255.255.255.0 s0/1/1
ip route 10.10.1.0 255.255.255.0 s0/1/1
ipv6 route 2001:DB8:1:B::/64 S0/1/1
ipv6 route 2001:DB8:1:A::/64 S0/1/1
ip route 0.0.0.0 0.0.0.0 s0/0/0
ip route 0.0.0.0 0.0.0.0 s0/0/1 2
ipv6 route ::/0 s0/0/1 2

!确认配置
sh ip route
------------------------------------------------------------
!West
hostname West


ipv6 unicast-routing
int s0/0/0
ip add 10.10.20.2 255.255.255.252
ipv add 2001:DB8:1:1::2/64
ipv add FE80::2 link-local
no sh
exit
int g0/0
ip add 10.10.1.254 255.255.255.0
ipv add 2001:DB8:1:A::1/64
ipv add FE80::2 link-local
no sh
exit
int g0/1
ip add 10.10.2.254 255.255.255.0
ipv add 2001:DB8:1:B::1/64
ipv add FE80::2 link-local
no sh
exit

ip route 0.0.0.0 0.0.0.0 s0/0/0
ipv6 route ::/0 s0/0/0

会看到
West#sh ipv6 route 
IPv6 Routing Table - 8 entries
Codes: C - Connected, L - Local, S - Static, R - RIP, B - BGP
       U - Per-user Static route, M - MIPv6
       I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea, IS - ISIS summary
       O - OSPF intra, OI - OSPF inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2
       D - EIGRP, EX - EIGRP external
S   ::/0 [1/0]
     via Serial0/0/0, directly connected
C   2001:DB8:1:1::/64 [0/0]
     via Serial0/0/0, directly connected
L   2001:DB8:1:1::2/128 [0/0]
     via Serial0/0/0, receive
C   2001:DB8:1:A::/64 [0/0]
     via GigabitEthernet0/0, directly connected
L   2001:DB8:1:A::1/128 [0/0]
     via GigabitEthernet0/0, receive
C   2001:DB8:1:B::/64 [0/0]
     via GigabitEthernet0/1, directly connected
L   2001:DB8:1:B::1/128 [0/0]
     via GigabitEthernet0/1, receive
L   FF00::/8 [0/0]
     via Null0, receive
-------------------------------------------------------------------

![1574498707719](RSE_C2_PT%20-%20%E5%89%AF%E6%9C%AC.assets/1574498707719.png)



[具体视频教程链接](https://www.youtube.com/watch?v=fmvC_LPpJTA)

