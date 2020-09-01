---
layout: post
title: Left Semi Join
subtitle :
tags: [HiveQL, Join]
author: Minji Kwon
comments : False
---

# Left Semi Join

- Left Semi Join은 IN/EXISTS의 역할.
- Left Semi Join에서 오른편 테이블은 JOIN 절에서만 사용될 수 있고 WHERE 이나 SELECT 절에서는 사용될 수 없음.

SELECT A.*, B.* FROM A LEFT SEMI JOIN B ON A.id = B.id;(X, 오른편 테이블은 SELECT 절에서 사용될 수 없음.)

SELECT A.* FROM A LEFT SEMI JOIN B ON A.id = B.id WHERE B.id = 1; (X, 오른편 테이블은 WHERE 절에서 사용될 수 없음.)


SELECT A.* FROM A LEFT SEMI JOIN B ON A.id = B.id;

===

SELECT A.* FROM A WHERE A.id IN (SELECT B.id FROM B);