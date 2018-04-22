---
layout: post
title: postgresql 笔记
tag: postgresql
---

计算表占用空间大小

pg_database_size(name)	指定名称的数据库使用的磁盘空间

pg_table_size(regclass)	bigint	指定表OID或表名的表使用的磁盘空间，除去索引（但是包含TOAST，自由空间映射和可视映射）




```sql
postgres=# select pg_database_size('shifenzheng');
 pg_database_size
------------------
       4748026028
(1 row)

postgres=# select pg_size_pretty(pg_database_size('shifenzheng'));
 pg_size_pretty
----------------
 4528 MB
(1 row)

```

计算数据库的大小（不含索引）
pg没有提供计算不含索引的数据库大小的函数，只能通过下面的方式计算。
```
sum(pg_table_size(table_name)) from (SELECT ('"' || tablename || '"') AS table_name
FROM pg_tables
where schemaname = 'public') as tn;
```