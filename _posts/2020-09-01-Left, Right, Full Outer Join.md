---
layout: post
title: Outer Join
subtitle : Left, Right, Full Outer Join
tags: [HiveQL, Join]
author: Minji Kwon
comments : False
---

# Left Outer Join, Right Outer Join, Full Outer Join

예를 들어, 다음과 같은 Table A, TableB가 있음.

## Table A

| Id  | Data |
| :-------: | :-------: |
| 1 | A11 |
| 1 | A12 |
| 1 | A13 |
| 2 | A21 |
| 3 | A31 |

## Table B

| Id  | Data |
| :-------: | :-------: |
| 1 | B11 |
| 2 | B21 |
| 2 | B22 |
| 2 | B23 |
| 4 | B41 |

왼쪽 외부조인을 하는 경우,
SELECT * FROM A LEFT OUTER JOIN B ON A.id = B.id;
다음과 같이 결과가 나옴.

| Id  | Data | Id  | Data |
| :-------: | :-------: | :-------: | :-------: |
| 1 | A11 | 1 | B11 |
| 1 | A12 | 1 | B11 |
| 1 | A13 | 1 | B11 |
| 2 | A21 | 2 | B21 |
| 2 | A21 | 2 | B22 |
| 2 | A21 | 2 | B23 |
| 3 | A31 | | | |

오른쪽 외부조인을 하는 경우,
SELECT * FROM A RIGHT OUTER JOIN B ON A.id = B.id;
다음과 같이 결과가 나옴.

| Id  | Data | Id  | Data |
| :-------: | :-------: | :-------: | :-------: |
| 1 | A11 | 1 | B11 |
| 1 | A12 | 1 | B11 |
| 1 | A13 | 1 | B11 |
| 2 | A21 | 2 | B21 |
| 2 | A21 | 2 | B22 |
| 2 | A21 | 2 | B23 |
| | | 4 | B41 | |

완전 외부조인을 하는 경우,
SELECT * FROM A FULL OUTER JOIN B ON A.id = B.id;
다음과 같이 결과가 나옴.

| Id  | Data | Id  | Data |
| :-------: | :-------: | :-------: | :-------: |
| 1 | A11 | 1 | B11 |
| 1 | A12 | 1 | B11 |
| 1 | A13 | 1 | B11 |
| 2 | A21 | 2 | B21 |
| 2 | A21 | 2 | B22 |
| 2 | A21 | 2 | B23 |
| 3 | A31 | | |
| | | 4 | B41 |