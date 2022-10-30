# mysql 创建及使用方法
### 一、startService
```text
Win + R 输入 services.msc
```
### 二、连接mysql
```cmd
# mysql -h localhost -u root -p
Enter password:******
```
- -h 后面的参数表示hostname 为服务器的`主机地址`当客户端和服务器在`同一台`机器上时，可以使用`localhost` 或 `127.0.0.1`
- -u 参数username 为登陆MySQL服务的`用户名`
- -p 参数指代`密码`
### 三、数据库
#### 1.查看
```sql
SHOW DATABASES;
```
#### 2.创建
```sql
create database if not exists test_db_char 
default charcter set utf8
default collate utf8_general_ci;
```

* collate `校对`字符集
#### 3.删除
```sql
drop database <数据库名>;
```
#### 4.选择
```sql
use <数据库名>;
```
