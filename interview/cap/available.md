## 高可用相关问题
---

## 怎么理解高可用？ ⭐ :id=ha-concept
一个服务器或节点坏了，但不影响整个系统的正常运行，如果系统做到了这一点，那么就实现了高可用

## 高可用的降级？ ⭐ :id=ha-demotion
1. 降级开关集中化管理：将开关配置信息推送到各个应⽤
1. 可降级的多级读服务：如服务调⽤降级为只读本地缓存
1. 开关前置化：如Nginx+lua(OpenResty)配置降级策略，引流流量；可基于此做灰度策略
1. 业务降级：⾼并发下，保证核⼼功能，次要功能可由同步改为异步策略或屏蔽功能

## 高可用的限流？ ⭐ :id=ha-limit
1. ⽬的: 防⽌恶意请求攻击或超出系统峰值
1. 实践：恶意请求流量只访问到Cache、穿透后端应⽤的流量使⽤Nginx的limit处理、恶意IP使⽤Nginx Deny策略或者iptables拒绝

## 高可用的切流量？ ⭐ :id=ha-cut
1. ⽬的：屏蔽故障机器
1. 实践:  DNS: 更改域名解析⼊⼝，如DNSPOD可以添加备⽤IP，正常IP故障时，会⾃主切换到备⽤地址;⽣效实践较慢、HttpDNS: 为了绕过运营商LocalDNS实现的精准流量调度LVS/HaProxy/Nginx: 摘除故障节点

## 高可用的可回滚？ ⭐ :id=ha-rollback
1. 发布版本失败时可随时快速回退到上⼀个稳定版本