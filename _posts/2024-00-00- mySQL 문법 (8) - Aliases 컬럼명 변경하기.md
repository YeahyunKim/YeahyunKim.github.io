---
title: mySQL 문법 (8) - Aliases 컬럼명 변경하기
author: yeahyun
date: 2024-03-08
categories:
  - mySQL
  - Grammarㅤ
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
---
## 💡Aliases
---
#### 01. Aliases(AS)

>Aliases are used to give a table, or a column in a table, a temporary name.
>Aliases are often used to make column names more readable.
>An alias only exists for the duration of that query.
>An alias is created with the `AS` keyword.
{: .command-text}

`AS` 는 컬럼명, 테이블명에 별칭을 주어, 데이터 조회 후 가독성이 좋아보이게 만드는데 굉장히 효과적이다.  
`AS`는 해당 쿼리가 실행되었을 동안만 존재하고, 직접적으로 테이블에 영향을 주지 않는다.

**테이블에 별칭을 주었으면, 해당 별칭으로 컬럼들을 조회할 수 있다.**

<br>
<br>
## 💡문법 Syntax
---
#### 01. 테이블에 별칭주기

```sql
SELECT * FROM 테이블 AS 별칭
```

<br>
#### 02. 컬럼에 별칭주기

```sql
SELECT 컬럼 AS 별칭 FROM 테이블
```
<br>
<br>

## 💡사용예시
---
#### 01. 컬럼에 별칭주기

##### 1) 하나의 컬럼 별칭주기

```sql
SELECT name AS '이름' FROM customers
```

>• 조건 1 : name 컬럼명에 '이름'이란 별칭주기  
>• 해석 : customers 테이블에서 name 컬럼만 가져와주는데, 컬럼명을 '이름'으로 바꿔줘.
{: .command-text}

![이미지](https://ifh.cc/g/a7816D.png)


<br>
##### 2) 여러개의 컬럼에 별칭주기

```sql
SELECT name AS '이름', email AS '이메일' FROM customers
```

>• 조건 1 : name 컬럼명에 '이름', email 컬럼명에 '이메일' 이란 별칭주기  
>• 해석 : customers 테이블에서 name 과 email 컬럼만 가져와주는데, 컬럼명 각각 '이름', '이메일' 로 바꿔줘.
{: .command-text}

![이미지](https://ifh.cc/g/W7KRXz.png)

<br>
<br>
#### 02. 테이블에 별칭주기
##### 1) 테이블에 별칭주기

```sql
SELECT * FROM customer AS c
```

>• 조건 1 : name 컬럼명에 '이름'이란 별칭주기  
>• 해석 : customers 테이블에서 name 컬럼만 가져와주는데, 컬럼명을 '이름'으로 바꿔줘.
{: .command-text}