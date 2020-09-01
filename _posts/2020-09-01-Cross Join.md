---
layout: post
title: Cross Join
subtitle :
tags: [HiveQL, Join]
author: Minji Kwon
comments : False
---
# Cross Join
- Cross Join은 Cartesian product로도 알려짐.
c.f) Cartesian product는 A 테이블의 행들이 B 테이블의 행들과 모두 짝지어지는 경우임. 예를 들어 A 테이블이 10개의 행을, B 테이블이 13개의 행을 가지고 있으면 result set은 130개의 행이 됨.

- Cross Join을 포함하는 SQL문에 WHERE 절이 있으면 Cross Join을 먼저 처리하고 WHERE 절을 처리함.

- Cross Join은 JOIN 키워드나 CROSS JOIN 키워드를 사용함.
c.f) CROSS 키워드가 명시되어 있지 않으면 기본적으로 JOIN은 CROSS JOIN을 의미함. 하지만 ON이나 WHERE 절에 equality conditions가 명시되어 있다면 INNER JOIN을 의미함.

- 아래 예시 모두 Cross Join임.
SELECT * FROM A JOIN B;
SELECT * FROM A JOIN B WHERE A.id = 1;
SELECT * FROM A CROSS JOIN B;

- 테이블 A와 B를 Cross Join을 한 result set을 C와 Join하는 경우
SELECT * FROM A CROSS JOIN B JOIN C on A.id = C.id;