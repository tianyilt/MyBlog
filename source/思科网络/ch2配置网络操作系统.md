# 配网

## 思科IOS

操作系统

- 思科ios

网络技术人员

- CLI(command line interface)命令行+用户界面gui

所有思科网络设备默认一个ios

- RJ45 console控制台接口

可对ios版本或者功能集升级

## 访问

方法

- 控制台
- 辅助
- 虚拟终端 telnet ssh

终端工具

- putty



# PT

cli 特权模式

<img src="ch2%E9%85%8D%E7%BD%AE%E7%BD%91%E7%BB%9C%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.assets/1569046336636.png" alt="1569046336636" style="zoom:150%;" />

配密码->配置ip->存盘

全局配置

Router#conf terminal 
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#

改名

![1569046555290](ch2%E9%85%8D%E7%BD%AE%E7%BD%91%E7%BB%9C%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.assets/1569046555290.png)



存盘

![1569046742231](ch2%E9%85%8D%E7%BD%AE%E7%BD%91%E7%BB%9C%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.assets/1569046742231.png)

# 设备配置

## 主机名

SW-Floor-1

字母开头

没空格



## 安全操作

密码位置

- 接口(密码配置位置)
  - console 

  

  - aux
  - vty虚拟接口  默认不配vty密码来让任何人无法远程链接  别配默认密码cisco 或者 huawei

- enable时