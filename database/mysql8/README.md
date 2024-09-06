# MySql8相关

## 安装并启动MySql

这里使用MySql版本为 `8.0.4` 的 Docker 镜像

拉取镜像

```shell
docker pull mysql:8.0.4
```

创建配置文件和存放数据目录

```shell
mkdir -p /home/mysql/conf
mkdir -p /home/mysql/data
mkdir -p /home/mysql/mysql-files
```

启动容器

```shell
docker run --name mysql8 --restart=always -v /home/mysql/conf/my.cnf:/etc/mysql/my.cnf -v /home/mysql/data:/var/lib/mysql -v /home/mysql/mysql-files:/var/lib/mysql-files -v /etc/localtime:/etc/localtime:ro -p 3306:3306 -e MYSQL_ROOT_PASSWORD=12345687@Smallzh -d mysql:8.0.4
```

其中，

`-v /etc/localtime:/etc/localtime:ro` 表示，本机时间与数据库时间同步

授权root用户远程访问

```shell
docker exec -it mysql8 /bin/bash
mysql -uroot -p
# 授权root远程访问
use mysql;
select Host, User, authentication_string, plugin from user;
# 如果没有 rooter@%用户的话，创建用户
create user 'rooter'@'%' identified with mysql_native_password by '12345687@Sz';
grant all privileges on *.* to 'rooter'@'%' with grant option;
flush privileges;
```