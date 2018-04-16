---
layout: post
title: postgresql 笔记
tag: postgresql
---

计算表占用空间大小
pg_database_size(name)	指定名称的数据库使用的磁盘空间
pg_table_size(regclass)	bigint	指定表OID或表名的表使用的磁盘空间，除去索引（但是包含TOAST，自由空间映射和可视映射）

