---
title: mySQL 문법 (10) - DELETE 데이터 삭제하기
author: yeahyun
date: 2024-03-12
categories:
  - mySQL
  - Grammarㅤ
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
description:
  - 데이터 삭제하기
---
## 💡DELETE
---
#### 01. DELETE

>The `DELETE` statement is used to delete existing records in a table.
{: .command-text}

`UPDATE` 는 테이블의 기존 데이터 값을 삭제하는데 사용한다.

#### 02. 주의사항

>반드시 `WHERE`절을 사용하여 특정 데이터만 삭제하는데 사용하자. 그렇지 않으면 모든 데이터가 삭제될수도...
{: .prompt-danger}

<br>
<br>
## 💡문법 Syntax
---
#### 01. 특정한 컬럼의 데이터값을 삭제할 때

```sql
DELETE FROM 테이블명 WHERE 컬럼1 = '삭제할 값';
```

<br>
#### 02. 모든 데이터를 삭제할 때

```sql
DELETE FROM 테이블명
```
<br>
<br>

## 💡사용예시
---
#### 01. 특정한 컬럼의 데이터값을 삭제할 때

```sql
DELETE FROM Customers
WHERE CustomerID = 1;
```

>• 조건 1 : CustomerID 가 1  
>• 해석 : 고객 테이블 고객 아이디가 1인 고객의 데이터를 삭제해줘
{: .command-text}

<br>
#### 02. 모든 데이터를 삭제할 때

```sql
DELETE FROM Customers;
```

>• 해석 : 고객 테이블의 데이터를 모두 삭제해줘
{: .command-text}
