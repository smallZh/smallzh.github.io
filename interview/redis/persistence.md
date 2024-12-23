## 持久化题目
---
## 1 什么是Redis持久化？⭐ :id=p-concept
持久化就是把内存的数据写到磁盘中去，防止服务宕机了内存数据丢失。

## 2 Redis 的持久化机制是什么? ⭐⭐⭐⭐ :id=p-tenet
> 各自的优缺点

Redis 提供两种持久化机制 RDB（默认） 和 AOF 机制:

**RDB：是Redis DataBase缩写快照**

RDB是Redis默认的持久化方式。按照一定的时间将内存的数据以快照的形式保存到硬盘中，对应产生的数据文件为dump.rdb。通过配置文件中的save参数来定义快照的周期。

![](../imgs/redis_3.png)

优点：
1. 只有一个文件 dump.rdb，方便持久化。
2. 容灾性好，一个文件可以保存到安全的磁盘。
3. 性能最大化，fork 子进程来完成写操作，让主进程继续处理命令，所以是 IO 最大化。使用单独子进程来进行持久化，主进程不会进行任何 IO 操作，保证了 redis 的高性能
4. 相对于数据集大时，比 AOF 的启动效率更高。

缺点：
1. 数据安全性低。RDB 是间隔一段时间进行持久化，如果持久化之间 redis 发生故障，会发生数据丢失。所以这种方式更适合数据要求不严谨的时候)

**AOF：持久化**

AOF持久化(即Append Only File持久化)，则是将Redis执行的每次写命令记录到单独的日志文件中，当重启Redis会重新将持久化的日志中文件恢复数据。
当两种方式同时开启时，数据恢复Redis会优先选择AOF恢复。

![](../imgs/redis_4.png)

优点：
1. 数据安全，aof 持久化可以配置 appendfsync 属性，有 always，每进行一次 命令操作就记录到 aof 文件中一次。
1. 通过 append 模式写文件，即使中途服务器宕机，可以通过 redis-check-aof 工具解决数据一致性问题。
1. AOF 机制的 rewrite 模式。AOF 文件没被 rewrite 之前（文件过大时会对命令 进行合并重写），可以删除其中的某些命令（比如误操作的 flushall）)

缺点：
1. AOF 文件比 RDB 文件大，且恢复速度慢。
1. 数据集大的时候，比 rdb 启动效率低。


**优缺点比较**
1. AOF文件比RDB更新频率高，优先使用AOF还原数据。
1. AOF比RDB更安全也更大
1. RDB性能比AOF好
1. 如果两个都配了优先加载AOF

## 3 如何选择合适的持久化方式? ⭐⭐ :id=select-p
1. 一般来说， 如果想达到足以媲美PostgreSQL的数据安全性，你应该同时使用两种持久化功能。在这种情况下，当 Redis 重启的时候会优先载入AOF文件来恢复原始的数据，因为在通常情况下AOF文件保存的数据集要比RDB文件保存的数据集要完整。
1. 如果你非常关心你的数据， 但仍然可以承受数分钟以内的数据丢失，那么你可以只使用RDB持久化。
1. 有很多用户都只使用AOF持久化，但并不推荐这种方式，因为定时生成RDB快照（snapshot）非常便于进行数据库备份， 并且 RDB 恢复数据集的速度也要比AOF恢复的速度要快，除此之外，使用RDB还可以避免AOF程序的bug。
1. 如果你只希望你的数据在服务器运行的时候存在，你也可以不使用任何持久化方式。

## 4 Redis持久化数据和缓存怎么做扩容？⭐ :id=ext-p
1. 如果Redis被当做缓存使用，使用一致性哈希实现动态扩容缩容。
1. 如果Redis被当做一个持久化存储使用，必须使用固定的keys-to-nodes映射关系，节点的数量一旦确定不能变化。否则的话(即Redis节点需要动态变化的情况），必须使用可以在运行时进行数据再平衡的一套系统，而当前只有Redis集群可以做到这样。