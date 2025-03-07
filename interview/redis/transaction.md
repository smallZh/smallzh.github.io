## 事务相关
---
## 1 什么是事务？⭐ :id=t-concept
事务是一个单独的隔离操作：事务中的所有命令都会序列化、按顺序地执行。事务在执行的过程中，不会被其他客户端发送来的命令请求所打断。
事务是一个原子操作：事务中的命令要么全部被执行，要么全部都不执行。

## 2 Redis事务的概念? ⭐⭐⭐ :id=redis-t-concept
Redis 事务的本质是通过MULTI、EXEC、WATCH等一组命令的集合。事务支持一次执行多个命令，一个事务中所有命令都会被序列化。在事务执行过程，会按照顺序串行化执行队列中的命令，其他客户端提交的命令请求不会插入到事务执行命令序列中。
总结说：redis事务就是一次性、顺序性、排他性的执行一个队列中的一系列命令。

## 3 Redis事务的三个阶段? ⭐⭐⭐ :id=t-three-stage
1. 事务开始 MULTI
1. 命令入队
1. 事务执行 EXEC

事务执行过程中，如果服务端收到有EXEC、DISCARD、WATCH、MULTI之外的请求，将会把请求放入队列中排队

## 4 Redis事务相关命令? ⭐⭐ :id=t-command
Redis事务功能是通过MULTI、EXEC、DISCARD和WATCH 四个原语实现的
Redis会将一个事务中的所有命令序列化，然后按顺序执行。

1. redis 不支持回滚，“Redis 在事务失败时不进行回滚，而是继续执行余下的命令”， 所以 Redis 的内部可以保持简单且快速。
1. 如果在一个事务中的命令出现错误，那么所有的命令都不会执行；
1. 如果在一个事务中出现运行错误，那么正确的命令会被执行。

命令:
1. WATCH 命令是一个乐观锁，可以为 Redis 事务提供 check-and-set （CAS）行为。 可以监控一个或多个键，一旦其中有一个键被修改（或删除），之后的事务就不会执行，监控一直持续到EXEC命令。
1. MULTI命令用于开启一个事务，它总是返回OK。 MULTI执行之后，客户端可以继续向服务器发送任意多条命令，这些命令不会立即被执行，而是被放到一个队列中，当EXEC命令被调用时，所有队列中的命令才会被执行。
1. EXEC：执行所有事务块内的命令。返回事务块内所有命令的返回值，按命令执行的先后顺序排列。 当操作被打断时，返回空值 nil 。
1. 通过调用DISCARD，客户端可以清空事务队列，并放弃执行事务， 并且客户端会从事务状态中退出。
1. UNWATCH命令可以取消watch对所有key的监控。

## 5 事务管理（ACID）概述? ⭐ :id=t-manager
1. 原子性（Atomicity）原子性是指事务是一个不可分割的工作单位，事务中的操作要么都发生，要么都不发生。
1. 一致性（Consistency）事务前后数据的完整性必须保持一致。
1. 隔离性（Isolation）多个事务并发执行时，一个事务的执行不应影响其他事务的执行
1. 持久性（Durability）持久性是指一个事务一旦被提交，它对数据库中数据的改变就是永久性的，接下来即使数据库发生故障也不应该对其有任何影响

Redis的事务总是具有ACID中的一致性和隔离性，其他特性是不支持的。当服务器运行在AOF持久化模式下，并且appendfsync选项的值为always时，事务也具有持久性。

## 6 Redis事务支持隔离性吗? ⭐ :id=t-iso
Redis 是单进程程序，并且它保证在执行事务时，不会对事务进行中断，事务可以运行直到执行完所有事务队列中的命令为止。因此，Redis 的事务是总是带有隔离性的。

## 7 Redis事务保证原子性吗，支持回滚吗? ⭐ :id=t-rollback
Redis中，单条命令是原子性执行的，但事务不保证原子性，且没有回滚。事务中任意命令执行失败，其余的命令仍会被执行。

## 8 Redis事务其他实现? ⭐ :id=t-other-impl
1. 基于Lua脚本，Redis可以保证脚本内的命令一次性、按顺序地执行，
其同时也不提供事务运行错误的回滚，执行过程中如果部分命令运行错误，剩下的命令还是会继续运行完
1. 基于中间标记变量，通过另外的标记变量来标识事务是否执行完成，读取数据时先读取该标记变量判断是否事务执行完成。但这样会需要额外写代码实现，比较繁琐