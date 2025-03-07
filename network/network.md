# 网络层

主要提供2个核心功能：分组转发和路由选择

这一层的主要设备是：路由器

网络层就是一场**路由器大接力**

---

网络连接的设备：中继器、集线器、交换机、网桥、路由器和网关等。

路由器是网络层设备。

交换机和网桥是数据链路层设备，交换机就是多端口的网桥。

集线器和中继器都是物理层设备。

## 网络分类
数据报网络: 按照**目的主机地址**进行路由选择，是一种**无连接**网络

虚电路(VC)网络: 在源主机和目的主机之间建立一条**网络层逻辑连接**，是一种**有链接**网络

## 路由器
按照**功能体系结构**分为4部分：输入端口、交换结构、输出端口和路由处理器(CPU)

其中交换结构分为3种：基于内存交换、基于总线交换、基于网络交换

## 网络层拥塞
一种**连续过载**的网络状态

解决方法包含2个方面：增加网络资源或者减小网络负载

网络层常采用的拥塞控制措施有 4 种，其中**流量感知路由**和**准入控制**属于拥塞预防；**流量调节**和**负载脱落**属于拥塞消除。

## IPv4协议

IPv4的格式、IP分片的计算公式

IP地址分为2个部分：NetID(网络部分)和HostID(主机部分)

IP地址的3种表示方法：二进制法、4位十进制、16进制

子网划分表示：
1. 子网表示法：a.b.c.d/x ，其中x表示NetID位数
2. 子网掩码：用于计算子网的范围
3. 直接广播地址：使用**子网掩码反码**与主机地址做**或运算**

## ICMP协议
互联网控制报文协议

Internet **网络层**主要协议之一

主要功能是进行主机或路由器间的**网络层差错报告**与**网络探测**

## 路由算法
最常用的有：
1. 链路状态路由选择算法，使用Dijkstra算法
2. 距离向量路由选择算法，基于B-F方程

层次化路由选择：实现大规模网络路由选择最有效、可行的解决方案

## Internet路由选择协议

分为两种：
1. IGP: Internet的自治系统内路由选择协议称为**内部网关协议**(Interior Gateway Protocol, IGP)
   
2. EGP: Internet 的自治系统间路由选择协议称为**外部网关协议**(Exterior Gateway Protocol, EGP)。

典型的 IGP 协议有:
1. 路由信息协议RIP(Routing InformationProtocol)
2. 开放最短路径优先协议OSPF(Open Shortest Path First, OSPF)等；
   
典型的EGP协议:
1. 边界网关协议 BGP(Border Gateway Protocol)