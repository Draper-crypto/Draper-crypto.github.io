---
layout:     post
title:     在windows server 2008 中安装SQL server 2008
subtitle:  安装教程
date:       2023-2-6
author:     Draper-crypto
header-img: img/blogimg/post-windows-server-2008.jpg
catalog: true
tags:
    - windows server 2008
    - SQL server
    - 安装教程
---

# 一、安装环境

| 设备名称、型号                    |  版本    |
| :-------------------------------: | :--: |
| windows server 2008 R2 Enterprise |   企业版   |
| SQL server 2008                   |    软件  |

# 二、安装过程

1．打开SQLServer安装中心，在右边选择“全新安装或向现有安装添加功能”
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps21.jpg)

2．SQL Server开始安装准备
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps22.jpg) 

3．安装密钥：
**GYF3T-H2V88-GRPPH-HWRJP-QRTYB\**
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps23.jpg)

4．在“许可条款”中选择“我接受许可条款”，然后“下一步”
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps24.jpg) 

5．安装程序支持文件。在下面的界面中点击“安装”来安装程序的支持文件。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps25.jpg)

6．安装程序支持规则进行检查，对于没有通过的项进行修改，以符合支持规则。全部通过后点击“下一步”。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps26.jpg)

7．进行功能选择。根据需要酌情选择功能，然后点击“下一步”。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps27.jpg) 

8．安装程序开始进行安装规则检查。通过后点击“下一步”。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps28.jpg) 

9．在“实例配置”中指定实例的名称和实例安装的位置。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps29.jpg) 

10．安装程序开始检查磁盘空间是否满足要求。满足要求后，点击“下一步”。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps30.jpg) 

11．服务器配置，点击“下一步”。（红框区域根据实际情况选择，一般情况我们使用system账户）
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps31.jpg) 

12．在“数据库引擎配置”中，选择“混合模式”，并为“SQLServer系统管理员账户（sa）”指定密码，这里使用的密码是123.com。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps32.jpg) 

13．在“错误报告”界面，点击“下一步”。
![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps33.jpg)

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps34.jpg) 






























**14．*****\*核对一下需要安装的内容有无缺失，实例ID有无错误，安装位置是否正确，若没有问题则点击“安装”\****

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps35.jpg) 

**15．*****\*开始程序的安装。\****

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps36.jpg) 

**16．*****\*等待至进度条走完，安装完成\****

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps37.jpg) 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

***\*验证安装：\****

***\*1.\*******\*登录SQL Server数据库实例\****

***\*选择开始菜单－所有程序－Microsoft SQL Server 2008 R2－SQL Server Management Studio。\****![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps38.jpg)

***\*2.在打开的“连接到服务器”对话框中，服务器类型选择“数据库引擎”。\****

***\*“服务器名称”一栏输入"<计算机名>\<实例名>"\****

***\*身份验证选择“SQLServer身份验证”。选择“SQLServer身份验证”还需要在下面的登录名中填入“sa”，然后在登录密码中输入创建此实例时输入的密码，点“连接”\****

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps39.jpg) 

 

 

 

 

 

***\*3.连接成功\****

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps40.jpg) 

***\*至此安装过程全部结束\****
