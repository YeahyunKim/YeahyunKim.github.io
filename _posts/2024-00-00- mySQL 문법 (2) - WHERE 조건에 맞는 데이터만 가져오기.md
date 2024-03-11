---
title: mySQL 문법 (2) - WHERE 조건에 맞는 데이터만 가져오기
author: yeahyun
date: 2024-03-08
categories:
  - mySQL
  - Grammar   
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
---
## 💡WHERE
---
#### 01. WHERE 절이란

>The `WHERE` clause is used to filter records.
>It is used to extract only those records that fulfill a specified condition.
{: .command-text}

`WHERE` 절은 데이터를 필터링하여 원하는 조건에 맞는 데이터를 불러오는데 사용된다.
여기서, 데이터 조회 뿐만 아닌, `UPDATE`, `DELETE` 등 에서도 사용이 가능하다.



<br>
<br>

## 💡문법 Syntax
---
#### 01. 한개의 데이터 필터링하기

```sql
SELECT * FROM 테이블
WHERE 조건 = "값"
```

<br>
#### 02. 한개 이상의 데이터 필터링하기

```sql
SELECT * FROM 테이블
WHERE 조건 = 값 and 조건 = 값
```

<br>
<br>


## 💡사용예시
---
#### 01. 특정 데이터만 필터링 하기

```sql
SELECT * FROM food_orders WHERE cuisine_type = 'Korean';
```

`food_orders 라는 테이블에서 모든 컬럼을 선택하는데, 그중 한식을 판매하는 모든 데이터를 모여줘`

![이미지](https://ifh.cc/g/jcz1BJ.png)
<br>
<br>
#### 02. 한개 이상의 데이터 필터링 하기

```sql
SELECT * FROM food_orders WHERE cuisine_type = 'Korean' and price > 20000;
```

`WHERE` 절에 한개 이상의 데이터를 필터링 하고 싶으면, `and` 를 사용하면 된다.
위의 쿼리를 해석하면, 
`food_orders 라는 테이블에서 모든 컬럼을 선택하는데, 그중 가격이 20,000원 이상인 한식 데이터를 모두 보여줘`

![이미지](https://ifh.cc/g/vb6pch.png)