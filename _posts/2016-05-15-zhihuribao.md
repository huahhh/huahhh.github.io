---
layout: post_layout
title: 我是如何爬下所有知乎日报的
time: 2016年05月15日 星期日
location: 成都
pulished: true
excerpt_separator: "```"
---

作为深度知乎狗一只。[知乎日报](daily.zhihu.com)是每天必刷的东西了。有些时候吧，想着找一篇很久以前的内容，但是奈何知乎官方并不提供搜索。有时候想离线看吧，总是有诸多限制与麻烦。毕竟也做了一段时间爬虫了，趁周末有功夫。写个小爬虫，爬下了所有的知乎日报的内容。

>**知乎日报**：在中国,资讯类移动应用的人均阅读时长是 5 分钟,而在知乎日报,这个数字是 21。以独有的方式为你提供最高质、最深度、最有收获的阅读体验。

## 语言与工具

- **语言**：python

- **模块**：requests，pymongo，json

- **工具**：mongodb，wireshark

------

[TOC]

## 1.确定抓取源

###  WEB页面

当我确定抓取知乎日报时，首先想到的当然时知乎日报的WEB页面。我基本上都是在手机或者时ipad上看知乎日报的。知乎日报的WEB页面还真的没怎么看过。百度之，get。如下。

![Alt text](/assets/img/zhihuribao-1.png)

然而，WEB页面的知乎日报只有近几天的数据，请求加载更多就会提示下载App。如是，WEB版的知乎日报并不是一个很好的抓取源。

### chrome APP

pass掉了WEB页面后，本来想试试抓取手机app的，但是想着又太麻烦。刚好想起来知乎日报还有个chrome app。就从这里入手好了。界面如下。

![Alt text](/assets/img/zhihuribao-2.png)

恩，很好，很简洁舒服，完全符合蕾丝是毛的设计理念。关键的问题时，没有url，我怎么抓呢？~~madeAfucker~~（0.0）
然而这点儿小事儿并难不倒我。是时候祭出我的神器呢——**wireshark**。我们来抓个包吧。

>**Wireshark**（前称Ethereal）是一个网络封包分析软件。网络封包分析软件的功能是撷取网络封包，并尽可能显示出最为详细的网络封包资料。Wireshark使用WinPCAP作为接口，直接与网卡进行数据报文交换

>>**wireshark**：在网络的世界里，没有什么时抓次包解决不了的。如果不行，就抓两次。

开启wireshark，知乎日报的chrome App随便打开个日报内容。然后wireshark停止抓包，抓包结果过滤http。
如是，我们就很轻松的得到了该篇日报的真实地址。

>http://news-at.zhihu.com/api/4/news/8281781

![Alt text](/assets/img/zhihuribao-3.png)

把地址复制到浏览器看看，可以看出知乎日报的数据是以json为格式传输的。

![Alt text](/assets/img/zhihuribao-4.png)

找到单篇日报的url，我们按之前的方法抓包得到列表页的url。

>http://news.at.zhihu.com/api/4/news/before/20160510

恩，单篇的url和列表页的url都拿到了。我们也就确定了抓取源了。


## 2.URL及其返回内容分析






    未完


