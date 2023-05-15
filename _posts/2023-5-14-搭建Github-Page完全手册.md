---
layout:     post
title:      搭建Github Page完全手册
subtitle:   技术博文
date:       2023-5-14
author:     Draper-crypto
header-img: img/blogimg/post-bg-coffee.jpeg
catalog: 	 true
tags:
    - 网站搭建
    - Github
---

# 一、前期准备

> 注意：不想在本地安装软件或环境的读者可以跳过此章节

1. 注册`Github`账号（必备）
2. 下载`GitHub Desktop`：https://central.github.com/deployments/desktop/desktop/latest/win32（可使用`git`代替）
3. 

# 二、快速入门

## 1.模板参考

作者使用的模板来源：https://github.com/qiubaiying/qiubaiying.github.io

零基础的朋友可以直接拉取他的仓库

搭建方法参考文章：
[搭建方法参考](https://qiubaiying.github.io/2017/02/06/%E5%BF%AB%E9%80%9F%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)

## 2.拉取仓库

（1）打开上文模板链接

![image-20230514224926314](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514224926314.png)

（2）转跳到如下界面

![image-20230514225022141](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514225022141.png)

（3）修改以下内容

```
Repository name = 存储库名称 = 你想给他取的存储库名字
仓库名称格式：你的Github账号名.github.io
```

>注意：这里的名字就是访问他的网址

![image-20230514225222001](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514225222001.png)


![image-20230514225428887](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514225428887.png)

（4）修改仓库名

> 如果您在上部部分仓库名修改有误、不正确、报404错误请参考此章节

修改格式：
```
你的Github账号名.github.io，然后 Rename
```

![image-20230514230523280](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514230523280.png)

## 3.测试访问

按如上步骤来来应显示如图所示

![image-20230514232212722](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514232212722.png)

#三、完善

> 推荐使用`GitHub Desktop`将仓库拉取到本地，然后使用`vscode`编辑

## 1.增加左侧栏目中原作者未提供的转跳链接

（1）打开`_config.yml`

找到`SNS settings`部分

```
# SNS settings
RSS: false
zhihu_username:     你的用户名
github_username:    你的用户名
csdn_username:   你的用户名
```

原作者并未提供csdn或其他链接的修改代码

（2）此处添加你想要的链接的变量名

例如CSDN的变量名为：`csdn_username`
![image-20230514233259668](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514233259668.png)

(3)添加完成后修改

`\_layouts\page.html`中

修改为：

```html
{% if site.csdn_username %}
	<li>
        <a target="_blank" href="https://blog.csdn.net/{{ site.csdn_username }}">
        	<span class="fa-stack fa-lg">
        		<i class="fa fa-circle fa-stack-2x"></i>
        		<i class="fa fa-stack-1x fa-inverse">C</i>
        	</span>
     	</a>
	</li>
{% endif %}
```

![image-20230514233912169](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514233912169.png)

(4)刷新测试

正常应为下图所示

![image-20230514234459795](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514234459795.png)

## 2.更改域名

（1）域名购买方推荐使用

- [godaddy]:https://www.godaddy.com/zh-sg

- [阿里云-万网]:https://wanwang.aliyun.com/

（2）作者使用的是阿里云万网域名

可以看到.top域的域名非常的便宜（推荐使用）

![image-20230514234718681](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514234718681.png)

（3）购买完成后，回到Github已经可以访问的库中，点击setting

- 选择Pages选项

![image-20230514235045476](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230514235045476.png)

- 

##  3.添加SSL证书实现https访问

