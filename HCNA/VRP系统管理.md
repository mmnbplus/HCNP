 https://www.bilibili.com/video/BV1Dg4y187bZ?p=27 

# VRP系统管理

### 前言

为了满足企业业务对网络的需求，网络设备中的系统文件需要不断进行升级。另外，网络设备中的配置文件也需要时常进行备份，以防止设备故障或者其他灾害给业务带来损害。在升级和备份系统文件或者配置文件时，经常会使用FTP和TFTP来传输文件。

* 随着VRP版本的更新，VRP支持的特性也越来越多，可根据需求更新VRP版本

```
<Huawei>dis ver
Huawei Versatile Routing Platform Software
VRP (R) software, Version 5.130 (AR2200 V200R003C00)
Copyright (C) 2011-2012 HUAWEI TECH CO., LTD
Huawei AR2220 Router uptime is 0 week, 0 day, 0 hour, 49 minutes
BKP 0 version information: 

```

### VRP命名规范

* 由VRP自身版本号和关联产品版本号两部分组成

* 产品版本格式包含Vxxx(产品码)，Rxxx(大版本号)，Cxx(小版本号)

* 如果VRP产品版本有补丁，VRP产品版本号中还会包括SPC部分

  | Version 5.90(AR2200V200R001C00)        | VRP版本为5.90，产品版本号为V200R001C00                       |
  | -------------------------------------- | ------------------------------------------------------------ |
  | Version 5.120(AR2200V200R003C00SPC200) | VRP版本为5.120，产品版本号为V200R003C00SPC00，此产品版本包含有补丁包 |

### 上传文件

![1595926705817](VRP系统管理.assets/1595926705817.png)

![1595926896656](VRP系统管理.assets/1595926896656.png)

```bash
<Huawei>ftp 192.168.3.6						## 连接FTP服务器
Trying 192.168.3.6 ...

Press CTRL+K to abort
Connected to 192.168.3.6.
220 Xlight FTP 3.9 就绪...
User(192.168.3.6:(none)):mm
331 需要密码 mm
Enter password:
230 登录成功

[Huawei-ftp]
[Huawei-ftp]get huaweiftp.txt				## 下载文件
200 PORT命令执行成功
150 正在打开二进制模式数据连接为 huaweiftp.txt (9 比特).
226 传送完毕 (0.035 KB/s).
FTP: 9 byte(s) received in 0.540 second(s) 16.66byte(s)/sec.

[Huawei-ftp]q								## 退出
221 再见

<Huawei>dir									## 查看文件
Directory of flash:/

  Idx  Attr     Size(Byte)  Date        Time(LMT)  FileName 
    0  drw-              -  Jul 28 2020 05:52:24   dhcp
    1  -rw-              9  Jul 28 2020 11:47:06   huaweiftp.txt
    2  -rw-        121,802  May 26 2014 09:20:58   portalpage.zip
    3  -rw-          2,263  Jul 28 2020 06:51:27   statemach.efs
    4  -rw-        828,482  May 26 2014 09:20:58   sslvpn.zip
    5  -rw-            249  Jul 28 2020 06:16:09   private-data.txt
    6  drw-              -  Jul 28 2020 05:44:29   m6m6
    7  -rw-            120  Jul 28 2020 06:46:01   vrpcfg.zip

1,090,732 KB total (784,444 KB free)
<Huawei>more huaweiftp.txt 						## 查看文件内容
helloword
<Huawei>
[Huawei-ftp]put vrpcfg.zip						## 上传文件，工具需要开启权限
200 PORT命令执行成功
150 正在打开二进制模式数据连接为 vrpcfg.zip.

 100%     
226 传送完毕 (0.622 KB/s).
FTP: 120 byte(s) sent in 0.370 second(s) 324.32byte(s)/sec.

[Huawei-ftp]
```

## 系统管理

```bash
[Huawei-ftp]get /vrpcfg/newvrpcfg.cfg			## 上传新的VRP文件
200 PORT命令执行成功
150 正在打开二进制模式数据连接为 newvrpcfg.cfg (995 比特).
226 传送完毕 (5.819 KB/s).
FTP: 995 byte(s) received in 0.440 second(s) 2.26Kbyte(s)/sec.

[Huawei-ftp]q									## 退出


```

