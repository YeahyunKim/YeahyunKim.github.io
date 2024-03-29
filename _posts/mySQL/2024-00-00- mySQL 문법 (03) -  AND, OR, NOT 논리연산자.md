---
title: mySQL 문법 (03) - AND, OR, NOT 연산자
author: yeahyun
date: 2024-03-08
categories:
  - mySQL
  - Grammarㅤ
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
description:
  - 논리 연산자 사용하기
---
## 💡AND, OR, NOT 논리연산자
---
#### 01. AND

>The `AND` operators are used to filter records based on more than one condition:
{: .command-text}

`AND` 연산자는 두개의 조건이 모두 `true` 인 경우의 데이터를 필터링 합니다.  
`AND` 연산자는 `WHERE`절과 조합하여 사용할 수 있습니다.

<br>
#### 02. OR

>The `OR` operators are used to filter records based on more than one condition:
{: .command-text}

`OR` 연산자는 두개중 하나의 조건이 `true` 인 경우의 데이터를 필터링 합니다.  
`OR` 연산자는 `WHERE`절과 조합하여 사용할 수 있습니다.

<br>
#### 03. NOT

>The `NOT` operator displays a record if the condition(s) is NOT TRUE.
{: .command-text}

`NOT` 연산자는 조건이 `true`가 아닌 경우의 데이터를 필터링 합니다.  
`NOT` 연산자는 `WHERE`절과 조합하여 사용할 수 있습니다.
<br>
<br>

## 💡문법 Syntax
---
#### 01. AND 구문

```sql
SELECT * FROM 테이블
WHERE 조건1 AND 조건2 AND 조건3 ...;
```

<br>
#### 02. OR 구문

```sql
SELECT * FROM 테이블
WHERE 조건1 OR 조건2 OR 조건3 ...;
```

<br>
#### 03. NOT 구문

```sql
SELECT * FROM 테이블
WHERE NOT 조건1;
```
<br>
<br>


## 💡사용예시
---
#### 01. AND 예시

```sql
SELECT * FROM food_orders WHERE cuisine_type = 'Korean' AND price > 20000;
```

>• 조건 1 : cuisin_type = 'Korean'  
>• 조건 2 : price > 20000  
>• 해석 : food_orders 라는 테이블에서 모든 컬럼을 선택하는데, 그중 가격이 20,000원 이상인 한식 데이터를 모두 보여줘
{: .command-text}

![이미지](https://ifh.cc/g/vb6pch.png)<br>
<br>
#### 02. OR 예시

```sql
SELECT * FROM food_orders WHERE cuisine_type = 'Korean' OR price > 20000;
```

>• 조건 1 : cuisin_type = 'Korean'  
>• 조건 2 : price > 20000  
>• 해석 : food_orders 라는 테이블에서 모든 컬럼을 선택하는데, 그중 가격이 20,000원 이거나, 한식인 데이터를 모두 보여줘
{: .command-text}

**두개의 조건중 하나를 충족하는 데이터를 불러온다. 위의 `AND` 보다 많은 데이터가 조회된 것을 볼 수 있다.** 

![이미지](https://ifh.cc/g/woWk9g.jpg)

<br>
<br>
#### 03. NOT 예시

```sql
SELECT * FROM food_orders WHERE NOT cuisine_type = 'Korean'
```

>• 조건 1 : cuisin_type = 'Korean' 이외
>• 해석 : food_orders 라는 테이블에서 모든 컬럼을 선택하는데, 그중 음식타입이 한식이 아닌 모든 데이터를 보여줘
{: .command-text}

**음식타입이 'Korean' 이 아닌 모든 데이터를 조회한다** 

![이미지](https://ifh.cc/g/3BD3XT.jpg)


