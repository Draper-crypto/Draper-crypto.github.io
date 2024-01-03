---
layout:     post
title:     竞赛开发环境配置
subtitle:  Java8+MySQL+IDEA+Navicat16
date:       2023-6-1
author:     Draper-crypto
header-img: img/blogimg/post-bg-rwd.jpg
catalog: true
tags:
    - Java
    - 环境配置
---

> 前人栽树，后人乘凉
>
> 谨以此文记录安装过程中踩的所有坑

# 第一部分 环境信息

| 序号 |        名称        |                版本                |    备注    |
| :--: | :----------------: | :--------------------------------: | :--------: |
|  1   |        Java        |       jdk-8u341-windows-x64        |  编译环境  |
|  2   |       Python       |         python-3.9.7-amd64         |  编译环境  |
|  3   |      Windows       |  Windows 10 IoT 企业版 LTSC-21H2   |  操作系统  |
|  4   |   IntelliJ IDEA    |       IntelliJ IDEA 2022.2.3       |  编程软件  |
|  5   | Navicat Premium 16 |     navicat160_premium_cs_x64      | 数据库连接 |
|  6   |       MySQL        | mysql-installer-community-8.0.33.0 |   数据库   |

# 第二部分 起  步

## 一、安装Java 8

### 1.下载安装包

（1）首先打开ORACLE的官网

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps1.jpg) 

（2）选择Products(产品)下的Java产品

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps2.jpg) 

（3）来到这个界面，选择Download Java（下载Java）

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps3.jpg) 

（4）来到这个界面后，往下翻

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps4.jpg) 

 

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps5.jpg) 

（5）找到上图所示位置后看到下面，依照您现在使用的操作系统版本，点击后面的蓝色链接进行下载

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps6.jpg) 

（6）同意条款，点击下方按钮直接开始下载（由于作者已经提前注册号oracl的账户，此处不再赘述）

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps7.jpg) 

（7）下载成功后下图

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps8.jpg) 

 

### 2.安装Java8（JDK）

（1）双击打开安装文件，选择下一步

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps9.jpg) 

（2）保持默认，下一步。

*注意：建议安装路径保持默认，若必须要改，请保证整个Java安装路径没有中文*

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps10.jpg) 

（3）稍等片刻，弹出安装JRE的界面，依旧保持默认，下一步。

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps11.jpg) 

（4）稍等片刻，安装中

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps12.jpg) 

（5）显示该界面表示安装成功。

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps13.jpg) 

（6）检查

打开路径：`C:\Program Files\Java`

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps14.jpg) 

 

### 3.JDK环境变量配置

（1）右键此电脑，选择属性

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps15.png) 

（2）打开属性后，选择左边栏目中的“高级系统设置”

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps16.jpg) 

（3）在弹出窗口中选择“环境变量”

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps17.jpg) 

（4）即可配置“用户变量”及“系统变量”

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps18.jpg) 

（5）这里我们配置的是系统变量，选中“Path”，双击打开path的环境变量编辑

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps19.jpg)![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps20.jpg) 

（6）首先配置JAVA_HOME

- 复制Java JDK的根目录，作者这里的是`C:\Program Files\Java\jdk1.8.0_341`

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps21.jpg) 

- 创建系统变量，如下图所示

*注意：大小写保持一致，路径为刚刚复制的jdk根目录*

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps22.jpg) 

（7）双击Path进入编辑，新建环境变量‘%JAVA_HOME%\bin’

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps23.jpg) 

（8）将我们新建好的变量上移至最上面（表示当有相同的环境变量时，优先使用我们安装的环境变量）

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps24.jpg) 

（9）两次点击确定退出。

（10）打开命令提示符检查是否配置成功

输入命令：`java -version`

![img](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/wps25.jpg) 

若如上图所示，则代表配置成功,若显示“不是内部或外部命令，也不是可运行的程序或批处理文件。“则表示未成功，将已配置好的删掉，重复上述操作。




-----

## 二、安装Python

1.打开安装包，如下所示选择

![image-20230531230513296](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230531230513296.png)

2.待进度条走完

![image-20230531230533081](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230531230533081.png)

3.进度条到达100%后，显示如下，点击`Close`退出安装程序

![image-20230531230723409](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230531230723409.png)



-------

## 三、安装Navicat Premium 16

### 1.安装

（1）下载好安装包和破解软件

![image-20230601101528577](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601101528577.png)

（2）首先打开软件安装包，点击下一步

![image-20230601101701655](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601101701655.png)

（3）同意条款，下一步

![image-20230601101742980](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601101742980.png)

（4）选择安装目录，作者这里保持默认

![image-20230601101819066](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601101819066.png)

（5）是否需要桌面快捷方式，默认勾选，选择下一步

![image-20230601101903427](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601101903427.png)

（6）点击安装

![image-20230601101930202](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601101930202.png)

（7）待进度条走完

![image-20230601101959423](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601101959423.png)

（8）点击完成，退出安装程序

![image-20230601102028416](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601102028416.png)

### 2.破解

（1）将破解文件移动到安装目录下

![image-20230601102441758](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601102441758.png)

（2）双击打开破解文件，检查路径是否有误，无误点击路径后的`path`按钮

![image-20230601102555878](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601102555878.png)

（3）弹窗选择`是`

![image-20230601103120828](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601103120828.png)



（4）**`断开网络连接`**，打开安装好的`Navicat16`,弹出以下界面，点击`注册`

![image-20230601102923132](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601102923132.png)

（5）出现如下界面后在破解文件中选择`Generate !`按钮，将得到的密钥输入到刚刚的验证框中

![image-20230601103358828](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601103358828.png)



![image-20230601103445113](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601103445113.png)

![image-20230601103608771](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601103608771.png)

![image-20230601103637322](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601103637322.png)

（6）点击`激活`按钮，弹出如下界面，点击`手动激活`

![image-20230601103722243](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601103722243.png)

（7）复制请求码到破解软件中

![image-20230601103831218](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601103831218.png)

（8）如下图操作

![image-20230601104037441](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601104037441.png)

（9）将`激活码`复制回软件

![image-20230601104205722](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601104205722.png)

（10）点击`激活`，弹出弹窗，表示已激活成功

![image-20230601104245526](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601104245526.png)

（11）许可证已激活

![image-20230601104329841](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601104329841.png)



------

## 四、安装MySQL 8.0.33

### 1.安装

（1）打开下载文件，如下图

![image-20230518090847598](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518090847598.png)

（2）选择安装类型
这里我们选择`Server only`，点击`next`

> 注意：这里只适用仅使用数据库功能的同学，若需要安装其他插件的请选择Full

![image-20230518091635409](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518091635409.png)

（3）检查版本是否符合要求，并点击`Execute`，

![image-20230518091714054](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518091714054.png)

（4）等待进度数字到达100%，前方显示绿色勾则表示安装成功，点击`next`进入下一步。

![image-20230518091827160](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518091827160.png)

![image-20230518091947029](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518091947029.png)

（5）点击next进入下一步，进行基础配置

![image-20230518092459408](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518092459408.png)

### 2.配置过程

（1）选择`Development Computer`（开发计算机）,配置端口号`3306`

![微信图片_20230518093131](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20230518093131.png)

（2）按需选择，下一步

![image-20230518094057513](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518094057513.png)

（3）设置`root`的密码并创建用户

![image-20230518094255636](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518094255636.png)

（4）按需选择更改，下一步

> 注意：初学者建议默认配置

![image-20230518094548754](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518094548754.png)

（5）配置服务器文件权限，选择下一步

![image-20230518095052548](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518095052548.png)

（6）进入应用配置界面，选择`Execute`等待变成全绿后安装结束

![image-20230518095143050](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518095143050.png)

![image-20230518095327200](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518095327200.png)

（7）出现下图证明安装完成，点击finish

![image-20230518095419112](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518095419112.png)

（8）继续点击`next`

![image-20230518095539272](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518095539272.png)

（9）至此，安装过程完成

![image-20230518095627363](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230518095627363.png)

### 3.测试

1.打开刚刚安装好的Navicat Premium 16，选择`连接`，选择`MySQL`

![image-20230601105201224](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601105201224.png)

2.输入连接信息

![image-20230601105351491](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601105351491.png)

3.点击`测试连接`，显示如图所示即为配置成功

![image-20230601105721918](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601105721918.png)

4.现在就可以管理数据库了

![image-20230601105818436](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601105818436.png)


-----

## 五、安装IDEA 2022.2.3

### 1.安装

（1）下载全套安装包

![image-20230601123249714](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601123249714.png)

（2）运行安装程序

![image-20230601123450371](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601123450371.png)

（3）选择安装路径，然后点击`Next`

![image-20230601123608665](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601123608665.png)

（4）按需选择，选择`Next`

![image-20230601124105087](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601124105087.png)

（5）修改安装文件夹名称，一般保持默认，选择`Next`

![image-20230601124147862](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601124147862.png)

(6)等待进度条走完

![image-20230601140752904](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601140752904.png)

（7）选择`I want to manually reboot later`，然后点击`Finish`

![image-20230601141242958](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601141242958.png)

### 2.破解

（1）解压破解文件这里使用的方式是`方式1：自动引入补丁`

![image-20230601141433040](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601141433040.png)

（2）将破解文件`jetbra`移动到安装目录如图所示的位置

> 注意：这里的位置不是强制要求放在这里，可根据自己要求决定。

![image-20230601141644052](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601141644052.png)

（3）打开目录`\jetbra\scripts`，找到`install-all-users`文件，双击运行。弹框点击确定。

![image-20230601142138221](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601142138221.png)



（4）等待`Done`弹窗出现

> 注意：等待时间有长有短

![image-20230601142243086](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601142243086.png)

（5）打开IDEA，同意条款

![image-20230601142331415](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601142331415.png)

（6）选择是否发送用户数据
![image-20230601142401757](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601142401757.png)

（7）来到激活界面，选择`Activation code`

![image-20230601142433189](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601142433189.png)

（8）打开激活码文件，复制激活码，粘贴至此。点击`Activate`

> 激活码：
>
> 6G5NXCPJZB-eyJsaWNlbnNlSWQiOiI2RzVOWENQSlpCIiwibGljZW5zZWVOYW1lIjoic2lnbnVwIHNjb290ZXIiLCJhc3NpZ25lZU5hbWUiOiIiLCJhc3NpZ25lZUVtYWlsIjoiIiwibGljZW5zZVJlc3RyaWN0aW9uIjoiIiwiY2hlY2tDb25jdXJyZW50VXNlIjpmYWxzZSwicHJvZHVjdHMiOlt7ImNvZGUiOiJQU0kiLCJmYWxsYmFja0RhdGUiOiIyMDI1LTA4LTAxIiwicGFpZFVwVG8iOiIyMDI1LTA4LTAxIiwiZXh0ZW5kZWQiOnRydWV9LHsiY29kZSI6IlBEQiIsImZhbGxiYWNrRGF0ZSI6IjIwMjUtMDgtMDEiLCJwYWlkVXBUbyI6IjIwMjUtMDgtMDEiLCJleHRlbmRlZCI6dHJ1ZX0seyJjb2RlIjoiSUkiLCJmYWxsYmFja0RhdGUiOiIyMDI1LTA4LTAxIiwicGFpZFVwVG8iOiIyMDI1LTA4LTAxIiwiZXh0ZW5kZWQiOmZhbHNlfSx7ImNvZGUiOiJQUEMiLCJmYWxsYmFja0RhdGUiOiIyMDI1LTA4LTAxIiwicGFpZFVwVG8iOiIyMDI1LTA4LTAxIiwiZXh0ZW5kZWQiOnRydWV9LHsiY29kZSI6IlBHTyIsImZhbGxiYWNrRGF0ZSI6IjIwMjUtMDgtMDEiLCJwYWlkVXBUbyI6IjIwMjUtMDgtMDEiLCJleHRlbmRlZCI6dHJ1ZX0seyJjb2RlIjoiUFNXIiwiZmFsbGJhY2tEYXRlIjoiMjAyNS0wOC0wMSIsInBhaWRVcFRvIjoiMjAyNS0wOC0wMSIsImV4dGVuZGVkIjp0cnVlfSx7ImNvZGUiOiJQV1MiLCJmYWxsYmFja0RhdGUiOiIyMDI1LTA4LTAxIiwicGFpZFVwVG8iOiIyMDI1LTA4LTAxIiwiZXh0ZW5kZWQiOnRydWV9LHsiY29kZSI6IlBQUyIsImZhbGxiYWNrRGF0ZSI6IjIwMjUtMDgtMDEiLCJwYWlkVXBUbyI6IjIwMjUtMDgtMDEiLCJleHRlbmRlZCI6dHJ1ZX0seyJjb2RlIjoiUFJCIiwiZmFsbGJhY2tEYXRlIjoiMjAyNS0wOC0wMSIsInBhaWRVcFRvIjoiMjAyNS0wOC0wMSIsImV4dGVuZGVkIjp0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

![image-20230601142735491](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601142735491.png)

（9）如图显示为激活成功

![image-20230601142813706](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601142813706.png)

### 3.安装中文语言包

![image-20230601143206947](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601143206947.png)



-----



#  第三部分 创建spring boot项目

1.新建项目

![image-20230601143316551](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601143316551.png)

2.如图选择

![image-20230601143438981](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601143438981.png)

3.切换到`Spring Initializr`选项卡，如下设置

![image-20230601143629465](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601143629465.png)

4.如图改动

![image-20230601143842247](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601143842247.png)

5.创建完成等待依赖项全部创建好

> 注意：初次使用等待时间比较长，可以更改仓库地址解决。

![image-20230601144015874](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601144015874.png)

6.如图所示，创建成功

![image-20230601145140282](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601145140282.png)

----

# 第四部分 编写hello world程序

1.在`DemoApplication.java`同级或者下级的包下新建一个`HelloController`类，当然名字也可以自己取

![image-20230601145933987](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601145933987.png)

2.编写代码

```java
package com.example.demo;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class HelloController {
    @ResponseBody
    @RequestMapping("/hello")
    public String sayHello(){
        return "Hello, world! ";
    }
}
```

或

```java
package com.example.demo.web;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class HelloController {
        @RequestMapping("/hello")
        public String hello(){
            return "Hello, world!";
        }
}
```



![image-20230601150046594](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601150046594.png)

3.运行程序

![image-20230601150122243](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601150122243.png)

4.运行成功

![image-20230601153011594](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601153011594.png)


-----


# 第五部分 踩坑记录

## 第一坑 java: 警告: 源发行版 17 需要目标发行版 17

正常创建，编写运行报错：java: 警告: 源发行版 17 需要目标发行版 17

如图：

![image-20230601150846026](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601150846026.png)

### 解决方案

**方法一：改正如下几个地方的Java版本**

![image-20230601151045575](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601151045575.png)

![image-20230601151110857](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601151110857.png)

![image-20230601151210382](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601151210382.png)

![image-20230601151737298](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601151737298.png)

**成功解决**

![image-20230601152019325](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601152019325.png)

**方法二：改正如下图位置处的spring boot版本**

> 后在查阅相关资料后了解到由于3版本之后强制需要Java17版本，在这里改正可以规避后面的错误。

![](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601143842247.png)



## 第二坑 类文件具有错误的版本 61.0, 应为 52.0

好不容易解决了第一坑的问题，现在又出现第二个问题

如图：

![image-20230601151333456](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601151333456.png)

报错详情：

```shell
C:\Users\Administrator\IdeaProjects\demo1\src\main\java\com\example\demo\Demo1Application.java:3:32
java: 无法访问org.springframework.boot.SpringApplication
  错误的类文件: /C:/Users/Administrator/.m2/repository/org/springframework/boot/spring-boot/3.1.0/spring-boot-3.1.0.jar!/org/springframework/boot/SpringApplication.class
    类文件具有错误的版本 61.0, 应为 52.0
    请删除该文件或确保该文件位于正确的类路径子目录中。
```

### 问题原因

报错信息里所说的类文件版本指的是java class file version，java类文件版本该版本号与jdk版本号存在对应关系，61.0对应jdk17，52.0对应jdk8。如图

![image-20230601151818457](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601151818457.png)

具体参考：https://blog.csdn.net/weixin_43091089/article/details/128076622

> 在查这个报错时发现了一个网站，可用来查找依赖的版本号及依赖需要的依赖
>
> 这里附上网址：[点击转跳](https://mvnrepository.com/)

### 解决方法

> 这里我的解决过程非常玄学，正常情况因该是某个依赖出现问题，从而爆出该错误，但我的代码中未引用高版本的依赖，经过排查后发现，是maven的版本过高导致。

如图所示部分

![image-20230601152516217](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601152516217.png)

改正到2.7.0版本后重新检查依赖

![image-20230601152726336](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601152726336.png)

启动成功

![image-20230601152842275](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601152842275.png)



## 第三坑 Whitelabel Error Page

报错截图：

![image-20230601153317566](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601153317566.png)

源代码下文：

```java
package com.example.demo;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;


public class HelloController {
    @ResponseBody
    @RequestMapping("/hello")
    public String sayHello(){
        return "Hello, world! ";
    }
}
```

### 解决方案

> 查阅网上资料告诉我应当创建一个软件包，实践过后发现**问题依旧**

1.在文件下创建一个`web`软件包

![image-20230601153731572](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601153731572.png)

2.将HelloController.java移动到该目录下

![image-20230601153926970](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601153926970.png)

> 再顺着查找问题发现是少写了一个`@Controller`控制类

再次尝试，成功运行

![image-20230601154354444](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230601154354444.png)