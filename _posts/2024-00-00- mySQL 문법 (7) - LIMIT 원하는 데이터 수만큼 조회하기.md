---
title: mySQL 문법 (7) - LIMIT 원하는 데이터 수만큼 조회하기
author: yeahyun
date: 2024-03-08
categories:
  - mySQL
  - Grammarㅤ
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
---
## 💡LIMIT
---
#### 01. LIMIT

>The `LIMIT` clause is used to specify the number of records to return.
>The `LIMIT` clause is useful on large tables with thousands of records. Returning a large number of records can impact performance.
{: .command-text}

`LIMIT` 절은 대량의 데이터를 조회할때 유용하게 사용할 수 있다.
만약, customers라는 테이블을 조회했는데, 고객 수가 100,000,000명이면, 이를 조회하는데 컴퓨터에 무리가 갈 수 있고 시간이 굉장히 오래 걸린다.

<br>
<br>
## 💡문법 Syntax
---
#### 01. LIMIT 숫자

```sql
SELECT * FROM 테이블 LIMIT 숫자;
```

<br>
<br>

## 💡사용예시
---
#### 01. LIMIT 예시

##### 1) 3개의 데이터만 조회하기

```sql
SELECT * FROM customers LIMIT 3;
```

>• 조건 1 : 10개만 조회
>• 해석 : 고객들의 정보들 중 3개만 조회해줘
{: .command-text}

![이미지](https://ifh.cc/g/TH3SV3.png)


<br>
##### 2) 최근에 가입한 고객 3명 보기

```sql
SELECT * FROM customers ORDER BY customer_id DESC LIMIT 3;
```

>• 조건 1 : 고객이 가입한 아이디를 내림차순으로 정렬하고, 그중 3개만 조회
>• 해석 : 고객 아이디를 내림차순으로 정렬하고, 그중 3개를 고객 테이블에서 가져와줘
{: .command-text}

![이미지](https://ifh.cc/g/y1aNgH.png)

<br>