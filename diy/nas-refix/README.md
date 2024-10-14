# Nas改装，路漫漫，其...

## 缘起

2012年左右的时候，电脑的硬盘空间多是320G的，那会我买的一台海尔电脑就这么个空间，近几年基本都配置了512G的，但即便是512G，在使用过程中，硬盘也会逐渐不够用，在Window里显示”红盘“，所以，我一直觉得，即便是512G，仍然是不够用，硬盘空间仍然是小的（当然不排除我里面需要存放的文件多），总想着至少得搞个1T、2T的才行，存点照片、视频、书籍、代码啥的。

偶然间，看到别人博客里提到“黑群晖”，出于好奇，点进去看了看，了解到Nas，感觉这东东就是自己想要的，于是，搜索了一下，Nas是这样定义的

> NAS（Network Attached Storage：网络附属存储）按字面简单说就是连接在网络上，具备资料存储功能的装置，因此也称为“网络存储器”。它是一种专用数据存储服务器。它以数据为中心，将存储设备与服务器彻底分离，集中管理数据，从而释放带宽、提高性能、降低总拥有成本、保护投资。其成本远远低于使用服务器存储，而效率却远远高于后者。国际著名的NAS企业有Netapp、EMC、OUO等。
>> 出自《百度百科》

随后，搜索了一下Nas照片，看看长啥样

<img src="/_assets/img/diy/refit_nas/1-1.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/1-2.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/1-3.jpg" width="200" height="200" />

>> 来源于百度图片

看着颜值还挺高，某宝、拼刀刀搜索了一下，了解到，前两种硬盘数量少的，基本是家用，属于个人使用，后面这种多硬盘的，是企业用的。

看着Nas照片，顿时产生一种“相见恨晚”的感觉，这不就是自己苦苦追寻的大空间嘛，但，在盘位和价格之间产生了犹豫，2盘位觉着少，4盘位被价格劝退，而且，最重要的是：*我是真的需要大空间容量？还是懒的删掉无用文件呢？*

**Tip: 当你拿不定主意，而且也不是很着急的时候，最好先停一停，再做决定**

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

看着手里的R410笔记本，着实不太忍心动手拆机，但是，**物品的价值在于使用**，留着吃灰，是对它的不尊重。

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

如果改装成Nas的话，可能得从USB、WIFI扩展接口这两个地方入手。

## 改装思路

大体上是2个思路， 第一个思路，**更换WIFI扩展，将其扩展成sata**。因为主板上的WIFI扩展口是一个pci-e扩展口，所以，我当时想，既然可以扩展成WIFI，那是不也能扩展成sata呢？第二个思路，**将USB口转换为sata**。这个比较常见，我看到过很多人将一块2T的硬盘通过一个转换盒，插入到主机的USB口中，系统也能正常识别到硬盘。

我很倾向于第一个思路，总感觉这样的方式从*主板整体性*来看，更*融洽*一些，相比于第二个思路，usb转sata，总觉的后者是那么的不正规，而且，主板上的两个USB接口，是通过扩展线延伸的，并非主板自带的，于是，我先尝试了第一个思路，在某宝上搜索pci-e转sata卡，还真有

<img src="/_assets/img/diy/refit_nas/4-1.jpg" width="200" height="200" />

那然后，就下单买了，同时，也买了一块2T的硬盘，还有一个sata转接线。接上之后，很遗憾，失败了，系统识别不出硬盘。

>> 采用pci-e转sata扩展卡的结局：失败了!!

我不太懂硬件，实在搞不懂为啥这块pci-e转接卡不能用，于是，只能选择第二个思路，*使用usb转sata转换线*，当然，这个结局肯定是成功了。

## 改装过程

## 散热改装

笔记本电脑本身的散热器长这样

<img src="/_assets/img/diy/refit_nas/3-1.jpg" width="200" height="200" />

记得大学时，一学期不清理散热器灰尘，当玩游戏时、看网页视频时，时间稍微长点，电脑就黑屏了。每次除尘后，就好很多。

当然，如果只是做Nas，目前这个散热器就够用，但，我为了追求改装的机制，还有一种对散热的执念（我认为这个才是主要原因），特意加装了两个散热器，替换原有的散热器。

其中，CPU散热器是台式机的双管散热器

<img src="/_assets/img/diy/refit_nas/3-2.jpg" width="200" height="200" />

另一个是南北桥散热器

<img src="/_assets/img/diy/refit_nas/3-3.jpg" width="200" height="200" />

因为笔记本电脑的散热器更像是定制的，不兼容这种通用的散热器，因此，散热器的固定，就成了一个头大的问题。

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