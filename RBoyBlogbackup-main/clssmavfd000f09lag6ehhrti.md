---
title: "Wifi路由器干扰罗技g304鼠标"
datePublished: Tue Jan 23 2024 16:00:00 GMT+0000 (Coordinated Universal Time)
cuid: clssmavfd000f09lag6ehhrti
slug: wifig304
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708327775066/c84429bc-bbda-4869-850e-9c70fc475e19.jpeg
tags: bug, rboy

---

### **产生这个问题的原因是：**

为了提升无线设备日常使用内网的传输速度，我把主路由H3C NX30Pro放到了桌面上，无线设备的速度确实得到了质的提升，但突然发现鼠标卡卡的，疯狂掉帧，卡顿，最开始还以为是鼠标没电了，所以换了好几个电池，但问题依旧。

![IMG20240119124747](https://cdn.jsdelivr.net/gh/rboyy/picx-images-hosting@master/20240124/IMG20240119124747.jpg align="left")

### **发现问题：**

键盘鼠标这些无线USB插头多数都是2.4G，所以才想到和路由器的2.4G有干扰，

根治这个问题当然是关闭2.4G保留5G,但目前还有很多智能设备只支持2.4G，

所以并不能简单粗暴的关闭2.4G解决问题。

于是上网搜索相关信息，确实有人和我遇到了一样的问题，但是并没有人提供除关闭2.4G WIFI以外的解决方案。

只能试一下切换WIFI 2.4G信道能不能解决问题，于是从12信道切换到4信道，试了两三天，确实有慢慢好转，但鼠标还是会偶尔卡顿，所以切换低信道可能是有点用的，但并不确定......

![1706096922339](https://cdn.jsdelivr.net/gh/rboyy/picx-images-hosting@master/20240124/1706096922339.jpg align="left")

### **解决方案：**

产生这个问题的根本原因其实是USB接收器距离WIFI天线实在是太近了，

不管是显示器自带的USBHUB还是机箱前面板，都没有远离路由器天线的强干扰范围。

**所以我把接收器插到电脑后置板载接口就好了..... 就是这样.....**