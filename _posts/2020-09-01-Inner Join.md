---
layout: post
title: Inner Join
subtitle :
tags: [HiveQL, Join]
author: Minji Kwon
comments : False
---
# Inner Join

Hive에서 Join은 equality conditions만 지원됨.

SELECT A.* FROM A JOIN B ON A.id = B.id;

SELECT A.* FROM A JOIN B ON A.id <> B.id; (X, Hive에서는 non-equality conditions을 지원하지 않음.)

SELECT A.* FROM A, B where A.id = B.id;
SELECT A.*, B.* FROM A JOIN B ON A.id = B.id;
(둘의 차이는...?)


==============================================================
(map/reduce job이라...)
SELECT a.fname, b.lname, c.address FROM Sales a JOIN Sales_orc b ON a.id = b.id
join Sales_info c ON c.id = b.id;
(The seventh statement joins three tables: Sales, Sales_orc, and Sales_info. For this statement, only a
single map/reduce job is run because as per Hive if joining clauses contain the same columns from tables,
then only one map/reduce job is run. As per this example, Sales_orc uses the id column in both the
joining clauses so only one map/reduce job is created.)

SELECT a.fname, b.lname, c.address FROM Sales a JOIN Sales_orc b ON a.id = b.id
join Sales_info c ON c.address = b.address;
(The last statement joins three multiple tables, but this time the map/reduce jobs are two in place on one.
The result of the Sales and Sales_orc tables is the first of the two map/reduce jobs, which is joined to
the Sales_info table, the second map/reduce job.)