# mysql 常使用的系统查询命令
#### 系统参数查询命令
```
SHOW DATABASES;                  # 显示当前数据库服务器创建了哪些数据库
SHOW TABLES;                     # 显示当前数据库创建了哪些数据库表
SHOW CREATE DATABASE upmallsnew; # 显示upmallsnew数据库的创建脚本
SHOW CREATE TABLE orders;        # 显示orders 表创建的sql语句
DESC orders;                     # 显示 当前数据库中的 orders 表的字段属性
SHOW ENGINES; 					 # 显示当前mysql的支持的数据库引擎每个引擎的特性
SHOW VARIABLES;                  # 显示数据库服务器的基本参数
SHOW VARIABLES LIKE '%storage_engine%'; # 筛选某些特征的变量值
SELECT @@tx_isolation;                  # 当前会话的事务隔离级别
SELECT @@global.tx_isolation;           # 查看系统当前的事务隔离级别
SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED; # 修改当前会话的事务隔离级别
SET GLOBAL TRANSACTION ISOLATION LEVEL REPEATABLE READ;   # 修改系统当前的事务隔离级别
```