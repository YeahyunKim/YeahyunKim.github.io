---
title: mySQL 문법 (09) - UPDATE 데이터 수정하기
author: yeahyun
date: 2024-03-08
categories:
  - mySQL
  - Grammarㅤ
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
description:
  - 데이터 업데이트 하기
---
## 💡UPDATE
---
#### 01. UPDATE

>The `UPDATE` statement is used to modify the existing records in a table.
{: .command-text}

`UPDATE` 는 테이블의 기존 데이터 값을 수정하는데 사용한다.

#### 02. 주의사항

>반드시 `WHERE`절을 사용하여 특정 데이터만 수정하는데 사용하자. 그렇지 않으면 모든 기록이 업데이트 될 수 있기 때문..
{: .prompt-danger}

<br>
<br>
## 💡문법 Syntax
---
#### 01. 특정한 컬럼의 데이터값을 수정할 때

```sql
UPDATE 테이블명 SET 컬럼1 = '변경할 값' WHERE 조건1;
```

<br>
#### 02. 여러개 컬럼의 데이터값을 수정할 때

```sql
UPDATE 테이블명 SET 컬럼1 = '변경할 값', 컬럼2 = '변경할 값' WHERE 조건1;
```
<br>
<br>

## 💡사용예시
---
#### 01. 여러개의 컬럼 데이터 수정하기

```sql
UPDATE Customers  
SET ContactName = 'Alfred Schmidt', City = 'Frankfurt'  
WHERE CustomerID = 1;
```

>• 조건 1 : CustomerID 가 1  
>• 해석 : 고객 테이블 고객 아이디가 1인 고객의 이름과 도시명을 조건처럼 바꿔줘
{: .command-text}
