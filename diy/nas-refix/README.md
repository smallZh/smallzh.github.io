# Nas改装，路漫漫，其...

## 缘起
2022年的下半年，我无意间，在电脑上看到了别人的一篇博客标题，里面提到了“黑群晖”，出于好奇，便点进去看了看，于是，便接触到了Nas，初见，便是一种“相见恨晚”的感觉，直觉告诉我，这东东就是我想要的。粗略的看完博客，我马上度娘了一下Nas，是这样定义的

> NAS（Network Attached Storage：网络附属存储）按字面简单说就是连接在网络上，具备资料存储功能的装置，因此也称为“网络存储器”。它是一种专用数据存储服务器。它以数据为中心，将存储设备与服务器彻底分离，集中管理数据，从而释放带宽、提高性能、降低总拥有成本、保护投资。其成本远远低于使用服务器存储，而效率却远远高于后者。国际著名的NAS企业有Netapp、EMC、OUO等。
>> 出自《百度百科》

随后，继续度娘了一下Nas照片，看看长啥样

<img src="/_assets/img/diy/refit_nas/1-1.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/1-2.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/1-3.jpg" width="200" height="200" />

>> 来源于百度图片

从图片上看，前两种的颜值还挺高，随后，我某宝、拼刀刀搜索了一下，了解到，前两种硬盘数量少的，基本是家用，属于个人使用，后面这种多硬盘的，是企业用的。

我看着这些Nas照片，下意识的感触到，这不就是自己苦苦追寻的大空间嘛。

遥想2012年当初的时候，电脑的硬盘空间多是320G机械硬盘，那会我买的一台海尔笔记本，就这么个硬盘空间，随着硬盘技术的发展，近几年，电脑基本都配置了512G的固态硬盘，读写速度加快的同时，容量也变大不少，比如，我现在用的Dell笔记本，就是512G的固态硬盘，但即便是512G，我现在仍然是不够用（主要我里面需要存放的文件很多）。在电脑的使用过程中，各种资料文件、软件产生的中间文件、临时文件等等，使得硬盘中的文件越来越多，尤其是Window系统的C盘，用着用着就出现了”红盘“，这还是我刻意将一些软件装在D盘的情况下。

<img alt="window的C红盘" src="/_assets/img/diy/refit_nas/1-4.jpg" width="200" height="200" />

每当我看到这条红，总想着，这tm如果是股票、基金的红，那多爽！但现实是，这是系统警告我：“你磁盘空间不够啦，给我悠着点放东西，要么赶快清理，要么给我加空间，不然，小心我给你罢工，后果很严重的，你晓得哈！！”

对我来说，显然加空间是不现实的，把电脑的512G换1T？这个操作既要备份原文件，又要还原原文件，还得拆机换硬盘，真是费时费力，我宁愿选择将一些数据移到U盘、移动硬盘里，也比这个操作更划算。另外的方式，就是清理文件，时不时的清理一次。这种时不时的移动、清理文件，让我非常的渴望大空间，总想着至少得搞个2T、4T、8T，甚至20T硬盘空间才爽，有了这么大的空间，那可以说，我自己想存啥存啥，照片、歌、电影、电子书、代码啥的，那是随便存呀，妥妥一种中了几千万彩票的心态，那真是《明朝那些事里》对张士诚的说法:

> 手里拿着馒头，想蘸红糖蘸红糖，想蘸白糖蘸白糖

想想都觉得的乐的不行。

休息时，我在某宝、拼刀刀里又看了Nas，最终在盘位和价格之间产生了犹豫，2盘位吧，觉着少，4盘、6盘位，被价格劝退，当时，脑袋里产生了一个至今记忆尤深的想法：*我是真的需要这么大的空间？还是想体验这种个人大空间的爽呢？*

如果是想体验大空间的爽，那代价就是多花点钱，以及以后可能会出现的“买这么大空间的干啥”的懊恼。

**Tip: 当你产生犹豫时，而且也不是很着急的时候，最好先停一停，之后，再做决定**

基于这条忠告，我并没有立即入手一台Nas，而是先暂停一下自己如遇知己、如遇伯乐的兴奋，让子弹先飞一会嘛。

在随后的时间里，我时不时的会想到Nas，某天，忽然觉得，Nas，网络附加存储器，说白点，不就是 `多块硬盘 + 一台低配服务器` 嘛？

我那台2012年买的海尔笔记本，现在，在老家不一直吃灰呢嘛，在老家里，一直没人用，如果卖掉吧，又卖不了几个钱。

那我能不能将它改装成Nas呢？

如果我对Nas的这个看法正确，而且这台海尔笔记本也能挂载多块硬盘，那不就能改装成Nas嘛。

于是，在某次放假，我回老家时，带走了这台吃灰的旧海尔笔记本，开启了这一段“艰辛”的Nas改装路。

## 追忆：海尔R410，陪伴了我的整个大学

大学期间，我学的是计算机专业，因此，一台笔记本电脑，那就是一把必不可缺的武器。2012年的寒假，回到老家后，父母答应给我买台笔记本电脑，我呢，体谅父母挣钱的不易，为了给家里省点钱，本着能编程、能完成学期作业、能玩一些流行的游戏 的要求，去我县城众多的电脑店里，选了这款海尔R410笔记本。在2012年的时候，这款笔记本大概2k多，2核2G内存320G硬盘，装着win7系统。这配置足够我完成课堂、期末的结课作业，玩一些当时的流行游戏，比如，当时很火的穿越火线。

<img src="/_assets/img/diy/refit_nas/2-1.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/2-2.jpg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/2-3.jpg" width="200" height="200" />

从入门课C语言、到JavaSE、JavaEE、SQLServer数据库等等，这台海尔笔记本帮我完成了多个课堂、结课项目，不至于让我去趁图书馆机房的电脑、去网吧赶作业。

课余期间，从穿越火线、到后来的英雄联盟，至今记得，我和室友通力合作，穿越火线中爆出的第一把黄金AK，LOL中打出的完美团战等等，这台海尔笔记本，不知带给了多少个欢快的瞬间。

不管是不是大脑的选择性记忆，留下开心的，丢掉痛苦的，但，**追忆总是美好的**。

我看着手里的R410笔记本，着实不太忍心动手拆机，但是，**物品的价值在于使用**，留着吃灰，是对它的不尊重。

> 廉颇老矣，尚能饭否？

与其病老家中，哪如征战沙场，何其壮哉？

## 拆机：确定改装思考

从外观来看这台海尔R410，它有一个圆孔的电源口、一个网线口、3个USB口。另外它支持无线WIFI，有一块在左下角的320G机械硬盘（我在大学期间给这台笔记本加过一个4G内存条，所以知道硬盘在左下角）。目前，我仅能得到这些信息，如果想进一步得到更多的信息，那只能拆机，从内部看看，还有哪些信息可以利用。于是，我网上花了20.86元，买了一套螺丝刀，

<img src="/_assets/img/diy/refit_nas/2-4.jpg" width="200" height="200" />，

开始了拧螺丝拆机，笔记本的后盖打开后，是它的主板，只能看到主板的一面，因为是拆的后盖，我把这面主板叫**主板背面**，如下：

<img src="/_assets/img/diy/refit_nas/2-5.jpg" width="400" height="200" />，

笔记本内部主板的前面，当时忘记拍照，主要是一块硬盘，DVD驱动，最终，笔记本被拆碎成这几个：

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

<img src="/_assets/img/diy/refit_nas/disk-1.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-2.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-3.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-4.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-6.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-7.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-9.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-10.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-12.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-13.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-14.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-15.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-16.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-17.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-18.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-19.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/disk-20.jpeg" width="200" height="200" />


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

<img src="/_assets/img/diy/refit_nas/disk-1.jpeg"/>
<img src="/_assets/img/diy/refit_nas/disk-2.jpeg" />
<img src="/_assets/img/diy/refit_nas/disk-5.jpeg" />
<img src="/_assets/img/diy/refit_nas/disk-8.jpeg"/>

# 外壳设计的艰辛路

先用软件[QCAD](https://qcad.org)设计出外壳的形状，然后导出成PDF文件，发给亚克力板商家进行制作。

因为QCAD专业版每次只能试用30分钟，而我只是业余使用，所以，就每设计一点保存一点，30分钟后重新再打开软件。

设计图文件如下：

<a href="/_assets/img/diy/refit_nas/design-test/NAS机箱.dxf">QCAD学习</a>

<a href="/_assets/img/diy/refit_nas/design/nas-v1.dxf">外形设计</a>
外形图最终如下：

<img src="/_assets/img/diy/refit_nas/design/nas-v1.png" />

<img src="/_assets/img/diy/refit_nas/shape-1.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-2.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-3.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-4.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-5.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-6.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-7.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-8.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-9.jpeg" width="200" height="200" />
<img src="/_assets/img/diy/refit_nas/shape-10.jpeg" width="200" height="200" />


# 最终成果和总花费

## 最终成果

在咬牙的坚持下，最终将笔记本改成了Nas，来两个大图展示一下

<img src="/_assets/img/diy/refit_nas/result-1.jpg" width="365" height="365" />
<img src="/_assets/img/diy/refit_nas/result-2.jpg" width="365" height="365" />
<img src="/_assets/img/diy/refit_nas/result-3.jpeg" width="365" height="365" />
<img src="/_assets/img/diy/refit_nas/result-4.jpeg" width="365" height="365" />


<img src="/_assets/img/diy/refit_nas/disk-11.jpeg" />

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
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-1.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-2.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-3.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-4.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-5.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-6.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-7.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-8.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-9.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-10.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-11.jpeg" width="100" height="100" />|
|计量插座|27.8|<img src="/_assets/img/diy/refit_nas/tool-12.jpeg" width="100" height="100" />|

### 硬盘花费

|名称|金额|图片|
|---|---|---|
|日立2T|140.65|<img src="/_assets/img/diy/refit_nas/disk-14.jpeg"/>|
|企业4T|214.29|<img src="/_assets/img/diy/refit_nas/disk-18.jpeg"/>|

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