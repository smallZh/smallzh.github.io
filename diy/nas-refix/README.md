# Nas改装路

## 缘起

在没有接触到Nas之前，我一直觉得自己的电脑硬盘空间小，总觉得512G不够用，总想着至少得搞个1T、2T的才行，存点照片、视频、书籍、代码啥的。

偶然间，看到别人博客里提到“黑群晖”，出于好奇，点进去看了看，才了解到Nas，搜索了一下，Nas是这样定义的

> NAS（Network Attached Storage：网络附属存储）按字面简单说就是连接在网络上，具备资料存储功能的装置，因此也称为“网络存储器”。它是一种专用数据存储服务器。它以数据为中心，将存储设备与服务器彻底分离，集中管理数据，从而释放带宽、提高性能、降低总拥有成本、保护投资。其成本远远低于使用服务器存储，而效率却远远高于后者。国际著名的NAS企业有Netapp、EMC、OUO等。
>> 出自《百度百科》

随后，搜索了一下Nas照片，看看长啥样

![](/_assets/img/diy/refit_nas/1-1.jpg)
![](/_assets/img/diy/refit_nas/1-2.jpg)
![](/_assets/img/diy/refit_nas/1-3.jpg)

>> 来源于百度图片

看着颜值还挺好看，淘宝搜索了一下，了解到，前两种硬盘数量少的，基本是家用、个人使用，后面这种多硬盘的，是企业使用。

看着Nas照片，顿时产生一种“想见恨晚”的感觉，这不就是自己苦苦追寻的大空间嘛，但，在盘位和价格之间产生了犹豫，2盘位觉着少，4盘位被价格劝退，而且，自己是真的有大空间容量的需求，还是懒的删掉无用文件？

**当你拿不定主意，而且也不是很着急的时候，最好先停一停，再做决定**

基于这条忠告，我并没有立即入手一台Nas。后来，想到老家有一台旧笔记本电脑，一直吃灰，放在家里吧，没人用，卖掉吧，不值钱。

忽然间，想到，能不能将它改装成Nas呢？

Nas，网络附加存储器，说白点，不就是 `多块硬盘 + 一台低配服务器` 嘛？

如果我的旧电脑能挂载多块硬盘，那就能改装成Nas，于是，在某次放假回老家时，带走了吃灰的旧电脑，开启了这一段“艰辛”的Nas改装路。

# 海尔R410，陪伴了我的整个大学

## 追忆

由于是计算机专业，笔记本电脑就成了必不可缺的武器，为了给家里省点钱，本着够用、能编程、能完成学期作业就行的要求，选了这款海尔R410，在2012年的时候，大概2k多，2核2G内存320G硬盘，装着win7系统，足够完成课堂、期末的结课作业。

<img src="/_assets/img/diy/refit_nas/2-1.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/2-2.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/2-3.jpg" width="200" height="200" />

从入门课C语言、到JavaSE、JavaEE、SQLServer数据库等等，完成了多个结课项目。

课余期间，从穿越火线、到英雄联盟，同窗室友通力合作，爆出第一把黄金AK，LOL中的完美团战，已然记不清，曾经出现过多少个欢快的瞬间。

不管是不是大脑的选择性记忆，留下开心的，丢掉痛苦的，但，**追忆总是美好的**。

看着手里的R410笔记本，着实不太忍心动手拆机，但是，**物品的价值在于使用**，留着吃灰，是对它的不重尊。

## 拆机

网上花了20.86元，买了一套螺丝刀，

<img src="/_assets/img/diy/refit_nas/2-4.jpg" width="200" height="200" />，

开始了拧螺丝拆机，后盖打开后，

<img src="/_assets/img/diy/refit_nas/2-5.jpg" width="400" height="200" />，

下面没拍到，是一块硬盘，最终，拆碎成

|主板|CPU|内存条|硬盘|
|---|---|---|---|
|<img src="/_assets/img/diy/refit_nas/2-6.jpg" width="400" height="200" />|<img src="/_assets/img/diy/refit_nas/2-7.jpg" width="400" height="200" />|<img src="/_assets/img/diy/refit_nas/2-8.jpg" width="400" height="200" />|<img src="/_assets/img/diy/refit_nas/2-9.jpg" width="400" height="200" />|

由于拆机当时，没有及时拍照，没有留下后背完整的图片，于是，从网上找了两张侧面图

<img src="/_assets/img/diy/refit_nas/2-10.jpg" width="800" height="200" />，
<img src="/_assets/img/diy/refit_nas/2-11.jpg" width="800" height="100" />

一共有3个USB接口。

从主板来看，左下角，有一个WiFi扩展接口，

<img src="/_assets/img/diy/refit_nas/2-6.jpg" width="800" height="400" />

如果改装成Nas的话，可能得从这两个地方入手。

# 改装Nas的整体思路

## 思路
根据主板的
1. usb扩展口数量
1. pci-e扩展口

初步定为两种方案

## 散热改装

笔记本电脑本身的散热器长这样

<img src="/_assets/img/diy/refit_nas/3-1.jpg" width="200" height="200" />

记得大学时，一学期不清理散热器灰尘，当玩游戏时、看网页视频时，时间稍微长点，电脑就黑屏了。每次除尘后，就好很多。

当然，如果只是做Nas，目前这个散热器就够用，但，我为了追求改装的机制，特意加装了两个散热器，替换原有的散热器。

其中，CPU散热器是台式机的双管散热器

<img src="/_assets/img/diy/refit_nas/3-2.jpg" width="200" height="200" />

另一个是南北桥散热器

<img src="/_assets/img/diy/refit_nas/3-3.jpg" width="200" height="200" />

因为笔记本电脑的散热器更像是定制的，不兼容这种通用的散热器，因此，散热器的固定，就成了一个头大的问题。

# 采用pci-e转sata扩展卡

::: warning 结局
先说结论：这个方案，我失败了
:::

## 过程

由于主板上的两个USB接口，是通过扩展线延伸的，并非主板自带的，我就想着采用替换WIFI扩展口，将它改成sata口，网上搜了扩展卡，还真有

<img src="/_assets/img/diy/refit_nas/4-1.jpg" width="200" height="200" />

# 使用usb转sata转换线

::: tip 结局
这个方案，成功了
:::

## 过程

# 外壳设计的艰辛路

# 最终成果和总花费

## 最终成果

在咬牙的坚持下，最终将笔记本改成了Nas，来两个大图展示一下

<img src="/_assets/img/diy/refit_nas/7-1.jpg" width="365" height="365" />
<img src="/_assets/img/diy/refit_nas/7-2.jpg" width="365" height="365" />

开机后的耗电情况，最开始启动时，功率大概在70w左右，稳定运行后，功率在43w左右

开机启动时：
<img src="/_assets/img/diy/refit_nas/7-3.jpg" width="200" height="200" />

稳定运行后：
<img src="/_assets/img/diy/refit_nas/7-4.jpg" width="200" height="200" />

接下来，就是运行一段时间，看看稳定情况怎么样。

## 花费统计

### 工具花费

|名称|金额|图片|
|---|---|---|
|螺丝刀|20.86|<img src="/_assets/img/diy/refit_nas/2-4.jpg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/7-5.jpg" width="100" height="100" />|

### 硬盘花费

|名称|金额|图片|
|---|---|---|

### 配件花费

|名称|金额|图片|状态|
|---|---|---|---|
|CPU风扇|18.9|<img src="/_assets/img/diy/refit_nas/3-2.jpg" width="100" height="100" />|使用|
|南北桥散热器|23|<img src="/_assets/img/diy/refit_nas/3-3.jpg" width="100" height="100" />|使用|
|pci-e转sata扩展卡|45|<img src="/_assets/img/diy/refit_nas/4-1.jpg" width="100" height="100" />|未用|

## 后话

整个过程中，有好几次想放弃，想着干脆买一台得了，但由于不甘心，最终坚持着、歪歪扭扭地走完了这条路。

在这里，我记录下了整个过程，一是对自己的努力、坚持的一份肯定，二是对有改装Nas想法的你提供一点帮助。


> 写于2023-01-29