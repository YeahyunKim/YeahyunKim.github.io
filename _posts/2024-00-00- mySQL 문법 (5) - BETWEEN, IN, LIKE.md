---
title: mySQL 문법 (5) - BETWEEN, IN, LIKE
author: yeahyun
date: 2024-03-08
categories:
  - mySQL
  - Grammar   
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
---
## 💡BETWEEN, IN, LIKE
---
#### 01. BETWEEN

>The `BETWEEN` operator selects values within a given range. The values can be numbers, text, or dates.
>The `BETWEEN` operator is inclusive: begin and end values are included.
{: .command-text}

`BETWEEN` 연산자는 주어진 범위 내의 값을 선택하고, 값은 숫자, 문자열 혹은 날짜일 수 있습니다.
`BETWEEN` 연산자는 시작 및 끝 값이 포함되어있어, 조건의 값을 포괄합니다.

<br>
#### 02. IN

>The `IN` operator allows you to specify multiple values in a `WHERE` clause.
>The `IN` operator is a shorthand for multiple `OR` conditions.
{: .command-text}

`IN` 은 여러개의 값을 지정할 수 있도록 만들어줍니다.


<br>
#### 03. LIKE

>The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column.   
>There are two wildcards often used in conjunction with the `LIKE`  operator:   
>	- The percent sign (%) represents zero, one, or multiple characters
>	- The underscore sign (_) represents one, single character   
>The percent sign and the underscore can also be used in combinations!
{: .command-text}

`LIKE` 는  문자열 내에서 **내가 원하는 문자열 혹은 값을 찾아내는 함수입니다.**
`LIKE` 함수는 `WILDCARDS` 문자들과 함께 쓰이기도 합니다.

| WILDCARD | 설명                     |
| -------- | ---------------------- |
| %        | 0개 이상의 문자를 대신 표현할 수 있음 |
| _        | 1개의문자를 표현              |


<br>
<br>
## 💡문법 Syntax
---
#### 01. BETWEEN

```sql
SELECT * FROM 테이블
WHERE 컬럼 BETWEEN 조건1 and 조건2; 
```

<br>
#### 02. IN

```sql
SELECT * FROM 테이블
WHERE 컬럼 in (조건1, 조건2, 조건3)
```

<br>
#### 03. LIKE

```sql
SELECT * FROM 테이블
WHERE 컬럼 LIKE 조건
```

<br>
<br>

## 💡사용예시
---
#### 01. BETWEEN 예시

##### 1) 사이값 구하기

```sql
SELECT * FROM customers WHERE age BETWEEN 20 and 30;
```

>• 조건 1 : 20 <= age <= 30
>• 해석 : customers 라는 고객 테이블에서 고객의 나이가 20~30인 고객들의 데이터를 불러와줘
{: .command-text}

![이미지](https://ifh.cc/g/jNrpab.png)


<br>
##### 2) 다른 쿼리와 비교

```sql
SELECT * FROM customers WHERE age BETWEEN 20 and 30;

SELECT * FROM customers WHERE age >= 20 and age <= 30;

SELECT * FROM customers WHERE age > 19 and age < 31;
```

>위의 세개 쿼리는 모두 같은 값을 조회하여 결과로 보여준다. 
>하지만 가독성을 따져보았을때 BETWEEN 이 더 간편한 가독성을 보여준다.
{: .command-text}

<br>
#### 02. IN 예시

##### 1) 여러가지 값을 한번에 필터링 할 때
```sql
SELECT * FROM customers WHERE age in (29, 31, 39)
```

>• 조건 1 : age = 29, age = 31, age = 39
>• 해석 : customers 라는 고객 테이블에서 고객의 나이가 29, 31, 39인 고객들의 데이터를 불러와줘
{: .command-text}


![이미지](https://ifh.cc/g/fmjGSO.jpg)


<br>
<br>
#### 03. LIKE 예시
---
##### 1) 같은 문자 값 찾기
```sql
SELECT * FROM customers WHERE name LIKE "김예연";
```

>• 조건 1 : name = "김예연"
>• 해석 : 고객 테이블에서 이름이 "김예연"이란 고객들의 정보를 가져와줘.
{: .command-text}


<br>
##### 2) 같은 숫자 값 찾기
```sql
SELECT * FROM customers WHERE age LIKE 39;
```

>• 조건 1 : age = 39
>• 해석 : 고객 테이블에서 나이가 39살인 고객들의 정보를 가져와줘.
{: .command-text}

<br>
##### 3) 마지막이 특정 문자로 끝나는 값 찾기 '%t'
```sql
SELECT * FROM customers WHERE name LIKE '%연'
```

>• 조건 1 : name에서 '연' 문자로 끝나는 모든 값
>• 해석 : 고객 테이블에서 이름이 '연'으로 끝나는 모든 고객들의 정보를 가져와줘
{: .command-text}

![이미지](https://ifh.cc/g/3JoTbp.jpg)

<br>
##### 4) 처음이 특정 문자로 시작하는 값 찾기 't%'

```sql
SELECT * FROM customers WHERE name LIKE '김%'
```

>• 조건 1 : name에서 '연' 문자로 끝나는 모든 값
>• 해석 : 고객 테이블에서 성이 '김' 씨인 모든 고객들의 정보를 가져와줘
{: .command-text}

![이미지](https://ifh.cc/g/Z1LwOM.jpg)

<br>
##### 5) 가운데가 특정 문자인 값 찾기 '%t%'

```sql
SELECT * FROM customers WHERE name LIKE '%예%'
```

>• 조건 1 : name에서 중간에 '예' 문자가 있는 모든 값
>• 해석 : 고객 테이블에서 이름의 가운데에 '예' 가 있는 모든 고객들의 정보를 가져와줘.
{: .command-text}

![이미지](https://ifh.cc/g/YARvqC.jpg)


>%김% 으로 조회를 하면 `김예연` 이 조회가 된다. 그 이유는, %는 어떠한 문자가 와도 상관이 없기 때문에, `김예연` 도 조회를 한다.
{: .prompt-danger}

<br>
##### 6) 문자열 개수를 정해두고, 특정 문자 조회하기 '(underbar)text'

```sql
SELECT * FROM customers WHERE name LIKE "_민_"
```

>• 조건 1 : name에서 3개의 문자로 이루어져 있고, 가운데에 '민' 이라는 문자를 가지고 있는 값
>• 해석 : 고객 테이블에서 이름이 3자이면서, 가운데가 '민' 자인 모든 고객들을 불러와줘.
{: .command-text}

![이미지](https://ifh.cc/g/Nj4MFz.png)