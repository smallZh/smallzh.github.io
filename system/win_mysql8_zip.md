从 官网：https://downloads.mysql.com/archives/community/ 下载 zip安装包

解压到安装目录，比如：`E:\mysql8`

在安装目录下创建 my.ini配置文件，内容如下：
注意：修改mysql的安装目录和数据目录

```txt
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
 
[mysqld]
# 绑定端口
bind-address = 0.0.0.0
# 设置3306端口
port = 3306
# 设置mysql的安装目录
basedir=E:\mysql-8.0.41
# 设置mysql数据库的数据的存放目录
datadir=D:\mysql8\data
# 允许最大连接数
max_connections=10000
# 允许最大连接人数
max_user_connections=1000
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
 
# 连接时间
wait_timeout=2147483
interactive_timeout=31536000
```

进入安装目录执行以为命令

```shell
# 进入目录
cd e:\mysql8\bin

# 初始化mysql数据库
mysqld --initialize-insecure --user=mysql --console

# 注册mysql服务
mysqld --install

# 启动mysql 服务
net start mysql
```

登录mysql数据库，设置root密码。从控制台的输出能看出，数据库初始化时，root密码为空

```shell
# 在mysql安装目录的bin目录下执行
mysql -u root -p

# 修改root的用户密码
alter user 'root'@'localhost' identified by 'root';
flush privileges;
```
