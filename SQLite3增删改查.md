## SQLite3
- 安装sqlite3
> windows:下载sqlite3，解压到自定义路径，将自定义路径加入PATH环境变量
> Linux：自带
---
- 点命令
    - 在命令行，输入`sqlite3`，进入命令提示符，可以输入各种点命令。
    - 输入`.help`可以查看命令及用法
    - 常用命令：  

| 命令                 | 用途                     |
| :------------------: | :----------------------: |
| .databases           | 查看当前所有数据库       |
| .tables              | 查看当前所有表           |
| .schema table_name   | 查看指定表结构           |
| .quit                | 退出                     |
| .dump                | 导出完整数据库到指定文件 |

---

- 创建数据库
> 在命令行界面，输入`sqlite3 database_name.db`即可在当前文件路径下创建一个数据库  
> 可用`.databases`查看当前数据库
---
- 数据库导出和导入
> 在命令行界面，使用`$sqlite3 testDB.db .dump > testDB.sql`，将testDB.db导出到testDB.sql文件  
> 导入文件，使用`$sqlite3 testDB.db < testDB.sql`即可将testDB.sql恢复为testDB.db
---
- 创建表
```sql
create table database_name.table_name (
column1 datatype primary key ,
column2 datatype ,
...
columnN datatype,
);
```
> 可以创建`table_nmae`，也可以指定带有`table_name`的`database_name`
---
- 删除表
```sql
drop table database_name.table_name;
```
> 可以直接删除`table_name`，也可以指定带有表名的数据库名称
---
- 增
```sql
insert into table_name [(column1,column2...columnN)] values (value1,value2...valueN);
```
> column1,column2...columnN是要插入表的列的名称，values是与列一一对应的值。也可以不指定列，直接添加值，但需要保证值与列在表中的顺序一致
---
- 删
```sql
delete from table_name [where condition];
```
> 使用`where`来选择符合条件的记录删除，可以使用`and`或`or`运算符来选择多个条件
> 当不带有`where`时，表中所有的记录都会被清除。
> 
---
- 改
```sql
update table_name set column1 = value1, column2 = value2...columnN = valueN [where condition];
```
> 使用`update`修改表中已有记录，可以使用`where`来更新指定行记录
> 不使用`where`时将更新所有行的记录