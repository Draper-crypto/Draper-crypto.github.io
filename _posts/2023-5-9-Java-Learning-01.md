---
layout:     post
title:      Java学习笔记-01
subtitle:  学习笔记
date:       2023-5-9
author:     Draper-crypto
header-img: img/blogimg/post-Java-alibaba.jpg
catalog: true
tags:
    - Java
    - 学习笔记
---

#  Java01 语言介绍

##  1.认识Java

###  （1）Java 的具体内容

![java](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101055668.jpeg)

Java 是现在最流行的编程的语言之一，并且自身拥有庞大且完善的生态系统，可以实现你的任何需求（但不可能一门语言，实现的功能过多，所以，有些时候 Java 不擅长的部分会被其他的语言所顶替）。也就是说  在当前情况中 java 是整个编程的主力军，但是同一个正常来讲 它有它擅长和不擅长的地方，不擅长的地方， 就是慢慢发展之后  会寻求其他替代品。擅长的地方正在不断的应用，在国内而言，之所以 Java 使用广泛，更多的主要原因在于，**有许多的大户都在使用 Java 实现其各自的核心业务**。

大家所熟悉的一些大型网络公司，电商公司，基本上能看见的东西都是在后台通过Java 看见的，不过，近几年 Java 的发展也在不断地受到一些挑战，包括一些版权的争执等等。但和使用者是没有关系，有些系统是不可能轻易换掉的。

###  （2）Java 编程语言介绍
 Java 是由 SUN 公司开发的一套编程语言，其前身并不是 Java。

在 1991 年的时候，当时有一个 GREEN 项目，这个项目的核心功能在于使用 EMail控制家电产品的运行（智能家居这个项目就是当初GREEN项目想达到的目的）。在80 年代 Email 流行的时候，当时可以发送 Email 是一件很牛的事情。

但是遗憾的是，现在，基本不发邮件了，邮箱里停留的更多是一些广告和垃圾信息，可能永远都不会打开，但是前几年，邮箱里出现一个 Email，我们会觉得是个特别幸福的事。好莱坞有部电影叫《电子情书》有时间可以看一看，一个很文艺的片子，就是现实中是两个年轻男女，在网络中聊得特别好，互相发下信，一见面就认识了。所以说，这就是当年 Email 很火的原因。

最初 SUN 公司打算竞争此项目，但是后来考虑到了 C++ 的复杂性。所以利用C++ 开发出了一套 OAK（橡树）平台，并且利用此平台进行项目的竞标，不过遗憾的是，这个平台的竞标结果失败了，一个项目竞标失败，可想产品也就没什么利润了。但是这个时候，世界上有个最早的软件公司诞生了，创造了第一个技术最短上市的神话，就是网景。（第一家依靠技术上市的公司）受到了当时最好的浏览器的启发，推出了一个 Hotjava 的浏览器，那么后来在 1995 年 5 月 23 日的时候正式推出了 Java 编程语言，同时推出了 JDK1.0 的开发包，（1996 年的时候才开始可以提供陆续下载使用，到 1997 年传到中国）。1996 年 到 1997 的时候，才是 java 出现在报纸上比较高的频率。当时我们的信息都是通过电脑报获取的。最早还有很多杂志。

后来之所以不再用 OAK  用 Java 的主要原因在于 OAK 不能在申请版权，而我们Java 是可以的。

### （3）SUN 公司的由来
Java 是由 SUN 公司开发的一套编程语言，那么 SUN 公司是一家从事硬件开发的技术性公司，SUN 最 早的代表性产品：小型机（被广泛的应用在了 amazon 上）。亚马逊现在也是非常火的，最初在国外是个电商，它除了提供电子商务产品之外，还出了很多技术性的图书，亚马逊在最初的时候，技术非常牛，也准备了很多经典图书。再往后，亚马逊又开始涉及到了云服务上，云服务在国外是以亚马逊为主。但是国内基本上很少见到亚马逊服务。能见到更多的情况下也只是个阿里云，京东云等。

最初的 SUN 公司 全称（Stanford University NetWork）90 年代末的时候有一本电子商务书将 SUN 公司翻译成太阳公司。为什么叫太阳公司，是因为翻译图书有问题。说道电子商务，最初电子商务是由 IBM 提出来的，第一代电商已经见不到了，比如，京东，卓越。当当。卓越现在已经变成了亚马逊。在后来才有了今天的淘宝。后来，由于网络经济的发展问题，（任何的经济模式都会出现瓶颈）但是对于 90年代末-2000 年初的互联网低潮而言，这就是一个严重的伤害。当时整个互联网的开发，待遇是非常高的。虽然当时是个低潮，但是也创造出了很多神话，比如汤姆网，汤姆网是当时李嘉诚最早干的一个网站，但是由于涉及的业务过多，没有集中力量，慢慢的就颓废了。在国内，最著名的问题是，新浪和搜狐，赞美上市失败。就因为新浪和搜狐的失败很多人认为互联网并不是一个所谓的金蛋。它可能来讲是需要我们重新认识的一个过程。而同时也正赶上 8848 衰落的时候，8848 是当时最早的中国互联网的第一颗金蛋。而 SUN 公司经历了这么一段发展之后并没有恢复往日的经济实力。终于在后来被 oracle 公司所收购，但是 Oracle 公司收购前最希望收购 SUN 的实际上是 IBM，

IBM 当年软件产品线上的技术基础就是 Java 语言（SUN 并没有通过 JAVA 赚多少钱，但真正使用 Java 赚到钱的只有 IBM，后来还有依靠版权欺诈的 Oracle）所以从发展历史来讲，Java也是挺坎坷的。但是不管这些公司如何得折腾，有一点已经达成了共识，Java 依然是一个稳定的、可靠的编程语言，可以承担大型服务器的程序开发任务。而从我们的最初年代到现在 Java 语言也出现了一些技术的不同发展。

###  （4）Java 的开发形式

- Java标准开发（J2SE、JAVA SE）:提供的是底层的支持，实现了桌面程序的开发，主要就是单机程序，但是这个单机程序现在为止，实际上市场的份额并不高
- Java嵌入式开发（J2ME、JAVA ME）SUN 公司最早的时候就是想做嵌入式开发，但是这个嵌入式的发展被当年的 Nokia 给折腾够了，后来基本上就被 Android所替代了，但是再后来由于 Oracle 和 Google 的矛盾，导致 Android 的发展也出现了一个瓶颈，后来 Google 推出了自己的专属的编程语言来进行 Android 的开发（Kotlin）
- Java 企业开发（J2EE、JAVA EE）主要是进行企业平台的搭建，现在已经主要的开发是互联网平台。那么互联网平台对于JAVA的要求是越来越高，因为更多的情况下要考虑大用户访问的处理能力，所以今天为止我们再见到 Java 的这个过程基本上已经可以确定一点就是它已经不像最初我们开发那样只是个单机版程序。

##   2.Java语言特点

Java之所以可以得到持续的发展力以及良好的生态系统，这完全取决于Java的技术特征。

###  （1）Java的开发技术

Java的开发技术是一个行业内通用的技术实现标准；

Java本身也算是一个半开源的产品，所以很多的厂商得以解除Java的底层，这样使得Java 开发的更加透明；并且Java是一门面向对象的编程语言：这样使得Java语言语法结构更加方便开发者接受，这些面向对象的设计思想还在不断进行着扩充（不同的JDK版本）；

###  （2）Java同行业内的优势

Java提供有方便的内存回收处理机制：像一些编程语言里面需要明确的手工进行对象的回收与释放，否则程序将无法正常提供支持，但是Java可以提供自动内存回收操作，这样处理会更加方便一些（这里面牵扯到一些优化方面的问题）；同时避免了复杂的指针问题，而是用更加简单的引用来代替指针：指针虽然是一种高效的内存处理模式，但是其需要较强的逻辑分析，而Java在设计的时候充分考虑到了这一点，所以开发者直接利用引用就可以简化指针的处理，而引用也是在所有处理过程之中，最为麻烦最难理解的部分。

###  （3）Java支持多线编程

Java是为数不多支持多线程编程的开发语言，这样就可以使得单位时间内，处理的性能得到提升（性能的提升并不是绝对的），多线程也是Java开发之中最难以理解的部分，而正确的多线程处理，才是处理问题的核心所在；其次Java提供有高效的网络处理能力，可以基于NIO实现更加高效的数据传输处理，Java具有良好的可移植性，这样就可以提升一个程序的适用范围，而且Java语言足够简单。

##   3.Java的可移植性

###  （1）Java的可移植性

Java语言之中最大的特点在于其可移植性的支持，所谓的可移植性指的是同一个程序可以在不同的操作系统之间任意的进行部署，这样就减少了开发的难度在Java里面如果想要实现可移植性的控制，那么主要是依靠的是JVM（Java的虚拟机）

###  （2）Java虚拟机（Java Virtual Machine）
![image-20230510100056737](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305101000915.png)
Java虚拟机是一个由软件或硬件模拟出来的计算机，所有的程序只要有Java虚拟机的支持，就可以实现程序的执行，并且不同的操作系统上会有不同版本的JVM存在，这样就可以实现移植性。
计算机高级编程语言类型：编译型 解释型Java语言程序需要先编译形成字节码文件，而后在JVM进行解释文件，解释所有Java程序的解释都要放在虚拟机上处理，Java虚拟机（JVM）是用来读取并处理经编译过的与平台无关的字节码class文件。
Java编译器针对Java虚拟机产生的class文件，因此是独立于平台的，Java解释器负责将Java虚拟机的代码在特定的平台上运行。

###  （3）JVM应用程序运行机制

![屏幕截图 2023-05-10 090503](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/202305100959211.png)
所有*.java的源代码程序最终都是需要经过编译后才可以使用的，但是编译造成的程序代码并不是绑定在某个具体操作系统上的程序，而是一种通用性的程序，而这种通用性的程序就是JVM所能够识别的代码。

所有的程序并不是直接运行在操作系统上，而是通过JVM执行，这样一来肯定要比直接操作在系统上执行的程序的处理速度要慢，先期的确是一个问题，但是后来由于硬件技术的飞跃发现这些问题已经可以忽略了，但是目前依然会存在有JVM调优问题。

------

#  Java 02 搭建Java开发环境

##  1. JDK 介绍

### （1）JDK 特性

Java语言属于编译型与解释型的开发语言，对于Java语言，如果要想进行行开发，就一定要进行JDK的安装与配置，而JDK要想获取则需要通过官方网站获得，并且也需要在本机上进行配置。

主要的特性是提供了Lambda表达式

### （2）JDK 发展历程

最早的时候JDK都是有SUN公司提供的（www.sun.com），但是后来SUN公司被Oracle公司收购，之后如果还要获得则就必须登陆Oracle官方网站（www.Oracle.com），

对于JDK而言，其本身也有一段自己的发展历史，主要有如下的几个标志性的版本：

【1995年05月23】，JDK1.0的开发包发布，同时在1996年正式提供下载，标志着Java的诞生；

【1998年1月04】，JDK1.2版本推出，而后Java正式更名为Java2（只是Java的升级版本）；

【2005年05月23】，推出了JDK1.5版本，同时这个版本也是带来新特性以及开发支持更多的标志性的历史版本，可以说这一版本直接决定了Java后续十年的技术核心；

【2014年】 Java提供了JDK1.8版本，并且支持有Lambda表达式，可以使用函数编程；

【2017年 】Java提供了JDK1.9版本，进一步提升JDK1.8的稳定性；

【2018年】Java提供了JDK1.10版本，是属于JDK1.9的稳定版本；

（但是需要注意对于JDK1.8 、JDK1.9、JDK1.10三个版本做一个特别说明：如果要进行实际项目的生产环境部署，现阶段还行该以JDK1.8为主；JDK1.9和JDK1.10的区别不大，也就是说不管是使用JDK1.9或者JDK1.10效果是类似的）。

## 2.下载 Java 8

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


## 3. Java8（JDK）安装

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



## 3. JDK环境变量配置

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
