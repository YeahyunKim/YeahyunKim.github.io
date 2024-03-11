---
title: mySQL 문법 (6) - ORDER BY 오름차순,내림차순으로 정렬하기
author: yeahyun
date: 2024-03-08
categories:
  - mySQL
  - Grammarㅤ
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
---
## 💡ORDER BY
---
#### 01. ORDER BY

>The `ORDER BY` keyword is used to sort the result-set in ascending or descending order.   
>The `ORDER BY` keyword sorts the records in ascending order by default. To sort the records in descending order, use the `DESC` keyword.
{: .command-text}

`ORDER BY` 는 결과의 집합을 오름차 / 내림차순으로 정렬하는데 사용된다.

<br>
<br>
## 💡문법 Syntax
---
#### 01. ORDER BY ASC(오름차순)

```sql
SELECT * FROM 테이블 ORDER BY 컬럼1 ASC, 컬럼2 ASC
```

<br>
#### 02. ORDER BY DESC(내림차순)

```sql
SELECT * FROM 테이블 ORDER BY 컬럼1 DESC, 컬럼2 DESC
```


<br>
<br>

## 💡사용예시
---
#### 01. ORDER BY ASC 예시 (오름차순)

##### 1) 나이컬럼을 기준으로 오름차순으로 가져오기

```sql
SELECT * FROM customers ORDER BY age ASC;
```

>• 조건 1 : 없음
>• 해석 : 나이를 오름차순으로 정렬한 고객 정보 테이블을 가져와줘
{: .command-text}

![이미지](https://ifh.cc/g/TjRLFb.png)

>근데 한살이 어떻게 있지?;;
{: .command-text}

<br>
##### 2) 두개의 컬럼을 오름차순으로 정리하기

```sql
SELECT * FROM customers ORDER BY age ASC, name ASC;
```

>• 조건 1 : 없음
>• 해석 : 나이를 오름차순으로 정렬하고, 그중 이름을 오름차순으로 정리한 고객 정보 테이블을 가져와줘
{: .command-text}

![이미지](https://ifh.cc/g/y1aNgH.png)

<br>

#### 03. ORDER BY DESC 예시 (내림차순)

##### 1) 나이컬럼을 기준으로 내림차순으로 가져오기

```sql
SELECT * FROM customers ORDER BY age DESC;
```

>• 조건 1 : 없음
>• 해석 : 나이를 오름차순으로 정렬한 고객 정보 테이블을 가져와줘
{: .command-text}

![이미지](https://ifh.cc/g/AaRXzJ.png)

<br>
##### 2) 두개의 컬럼을 내림차순으로 정리하기

```sql
SELECT * FROM customers ORDER BY age DESC, name DESC;
```

>• 조건 1 : 없음
>• 해석 : 나이를 내림차순으로 정렬하고, 그중 이름을 내림차순으로 정리한 고객 정보 테이블을 가져와줘
{: .command-text}

![이미지](https://ifh.cc/g/C7GvoK.png)