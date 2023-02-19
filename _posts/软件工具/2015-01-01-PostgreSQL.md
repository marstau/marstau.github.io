---
layout: post
title: PostgreSQL
category: 软件工具
tags: software
keywords: PostgreSQL
description: 
---

## 安装使用 

```
brew install postgres # Homebrew安装PostgreSQL不用再执行initdb来完成安装过程
brew services start postgresql # 启动

psql postgres # 默认系统用户名,密码空 postgres数据库.
```
## 命令

```
select * from current_user;
select user;

select * from pg_tables; #得到当前db中所有表的信息
select * from pg_tables where schemaname='public'; # 得到所有用户自定义表
 \d tablename; # 查看表结构

psql -h localhost  -d databaseName  -U username -f  filename # 导入数据库文件
\l #列举数据库
\c databaseName #选择数据库
\dt # 查看该库中所有表
\d 表名 # 查看某个库中的某个表结构
\encoding # 显示字符集
\q # 退出
```


#### Postgres Connection url[More](https://stackoverflow.com/questions/3582552/postgres-connection-url)

```
If you use Libpq binding for respective language, according to its documentation URI is formed as follows:

postgresql://[user[:password]@][netloc][:port][/dbname][?param1=value1&...]
Here are examples from same document

postgresql://
postgresql://localhost
postgresql://localhost:5433
postgresql://localhost/mydb
postgresql://user@localhost
postgresql://user:secret@localhost
postgresql://other@localhost/other`b?connect_timeout=10&application_name=myapp
postgresql://localhost/mydb?user=other&password=secret
```

## Reference

* []