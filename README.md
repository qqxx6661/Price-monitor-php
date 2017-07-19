price-monitor-php
-----

# 简介
**该为旧版本备份，除特殊情况，不再更新。新版采用flask+sqlite+requests，功能更完善**

**新版项目地址：<a href="https://github.com/qqxx6661/flask_yzd">点我</a>**

**核心爬虫代码项目地址：<a href="https://github.com/qqxx6661/price-monitor">点我</a>**

**京东商城商品价格监控，用户自行设置商品和预期价格，低于预期价格后自动发送邮件提醒用户抢购。**

**目前已经开放（新版）测试：访问<a href="http://www.usau-buy.me/">电商监控系统</a>便可体验。**


-----

# 项目依赖
**1.php**
**2.mysql**
**3.python**自行安装，建议2.7

- requests (2.13.0+)
- mysql-connector-python（建议下载源码安装，pip容易报错）
- bs4
- lxml
- gevent

-----
# 使用步骤
## 以下步骤为php版搭建步骤
-----
**有两种使用方式：**

- 直接使用数据库 

- 搭建web端（本地或云上，推荐！！！）

**1. 本地使用**

- 使用提供的pricemonitor.sql文件建立Mysql数据库pricemonitor，见mysql文件夹。数据库默认账号密码为root

- （如搭建网页端，则跳过该步！）在数据库user表中新建用户，monitor表中新建要监控的商品，必填项为item_id, user_price, status=1（监控）/0（不监控）, user_id

- 在price-monitor-server文件夹下新建mailbox.txt文件，内容为三行

        第一行为发送邮箱地址
        第二行为发送邮箱密码
        第三行为邮箱的stmp

       举例：
```
        xxxxxxxxx@xxx.edu.cn  
        xxxxxxxx
        stmp.xxx.edu.cn
```

- 运行price-monitor-server/ProxyPool下的proxypool.py，开启代理抓取。感谢该代理池原作者。

- 如果是第一次运行代理池，由于代理池数据库之前没有数据，所以需要等待片刻。

- 运行price-monitor-server/下的main.py



**2. 搭建web端使用（可部署在VPS）**

- 首先配置LNMP或者LAMP的组合。

- 如果对搭建web服务器不熟悉可以看这里：<a href="https://lnmp.org/download.html">LNMP一键搭建</a>。这是我在百度找的，非打广告。

- 将php文件夹下的price放入你配置的存放网页的文件夹下。

- 之后将**1.本地使用**的全部步骤完成即可！


# Introduction

monitor price changes in JD.com, users can set expected price of specific item. Once the price is lower than excepted, the server will send an e-mail to user.


