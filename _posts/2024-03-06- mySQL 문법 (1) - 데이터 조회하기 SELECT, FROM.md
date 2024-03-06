---
title: mySQL 문법 (1) - 데이터 조회하기 SELECT, FROM
author: yeahyun
date: 2024-03-06
categories:
  - mySQL
  - Grammar
tags:
  - mySQL
image: https://ifh.cc/g/wvbwro.png
---
SELECT, FROM
---
#### 01. SELECT

SELECT 는 데이터를 가져오는 기본 명령어로, 데이터를 조회하는 모든 Query에 사용된다.
기본적으로 `컬럼`을 선택한다고 생각하면 된다.
<br>

#### 02. FROM

FROM 은 데이터를 가져올 테이블을 특정해주는 명령어이다.
기본적으로 `테이블`을 선택한다고 생각하면 된다.


<br>
<br>
## 문법보기

#### 01. 테이블의 모든 컬럼 불러오기

```sql
select * from food_orders
```

위의 쿼리를 해석하면, `food_orders 라는 테이블에서 모든 컬럼을 선택해서 가져와줘` 가 된다.

![이미지](https://ifh.cc/g/TDTm3v.jpg)

<br>

#### 02. 테이블의 원하는 컬럼 불러오기

```sql
select order_id, restaurant_name from food_orders
```

위의 쿼리를 해석하면, `food_orders 라는 테이블에서 order_id / restaurant_name 컬럼을 선택해서 가져와줘` 가 된다.

![이미지](https://ifh.cc/g/rhN5p3.png)