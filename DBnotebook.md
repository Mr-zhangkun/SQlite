## SQlite

### sqlite介绍
什么是sqlite?  
SQLite是一个进程内的库，实现了自给自足的、无服务器的、零配置的、事务性的 SQL 数据库引擎。  

sqlite的优点:
* 不需要一个单独的服务器进程或操作的系统（无服务器的）。
* SQLite 不需要配置，这意味着不需要安装或管理。
* 一个完整的 SQLite 数据库是存储在一个单一的跨平台的磁盘文件。
* SQLite 是非常小的，是轻量级的，完全配置时小于 400KiB，省略可选功能配置时小于250KiB。
* SQLite 是自给自足的，这意味着不需要任何外部的依赖。
* SQLite 事务是完全兼容 ACID 的，允许从多个进程或线程安全访问。
* SQLite 支持 SQL92（SQL2）标准的大多数查询语言的功能。

### sqlite安装
安装sqlite的Ｃ语言库
```sh
1. $sudo apt-get update
2. $sudo apt-get install  libsqlite3-dev
检查是否安装成功： cd  /usr/include 中查看是否有sqlite3.h文件
3. $sudo apt-get install sqlite3
```
### sqlite基本命令

```sh
$ sqlite3 name.db        　 //创建数据库
sqlite>.help　　　　　　　　　 //查看帮助
sqlite>.database        　  //文件存放位置
sqlite>.tables          　  //查看表
sqlite>.schema           　 //查看表结构
sqlite>.exit            　  //退出
```

### 常见语句
* 创建表
```sql
sqlite>create table COMPANY(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL
);
```
* 删除表
```sql
sqlite>.tables
COMPANY       test.COMPANY                                 //先查看表存在
sqlite>drop table COMPANY;　　　　                         　//执行删除命令
sqlite>
```
* 插入数据
```sql
sqlite>insert into COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
       values (1, 'Paul', 32, 'California', 20000.00 );
-------------------------------------------------------
sqlite>insert into COMPANY values (7, 'James', 24, 'Houston', 10000.00 );        //两种方法
```
* 删除数据
```sql
sqlite>delete from COMPANY where ID = 7;                        　//删除一行
sqlite>delete from COMPANY；　　　　　　　　　　　　　　　              //删除所有
```
* 修改数据
```sql
sqlite>update COMPANY set ADDRESS = 'Texas' WHERE ID = 6;         //修改一行
sqlite>update COMPANY set ADDRESS = 'Texas', SALARY = 20000.00;   //修改两列
```
* 查询数据
```sql
sqlite>select * from COMPANY;                                      //查询一行
sqlite>select * from COMPANY where id = 2;                        //查询所有
```
* 修改表名称
```sql
sqlite>alter table oldname rename to newname;
```
### 参考
* [菜鸟教程](http://www.runoob.com/sqlite/sqlite-drop-table.html)
