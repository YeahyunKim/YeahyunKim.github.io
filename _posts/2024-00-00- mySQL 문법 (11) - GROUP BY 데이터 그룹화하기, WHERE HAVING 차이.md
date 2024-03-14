---
title: mySQL 문법 (11) - GROUP BY 데이터 그룹화하기, WHERE HAVING 차이
author: yeahyun
date: 2024-03-12
categories:
  - mySQL
  - Grammarㅤ
tags:
  - mySQL
image: https://ifh.cc/g/DMV0va.png
---
## 💡GROUP BY
---
#### 01. GROUP BY

>The `GROUP BY` statement groups rows that have the same values into summary rows, like "find the number of customers in each country". <br/>
>The `GROUP BY` statement is often used with aggregate functions (`COUNT()`, `MAX()`, `MIN()`, `SUM()`, `AVG()`) to group the result-set by one or more columns.
{: .command-text}

`GROUP BY` 는 유형별로 개수를 알고 싶을때 사용한다.

#### 02. WHERE과 HAVING

>`WHERE`는 그룹화 하기 전의 조건   
>`HAVING`는 그룹화 후 의 조건
{: .prompt-danger}


<br>
<br>
## 💡문법 Syntax
---
#### 01. 특정 컬럼을 그룹화

```sql
SELECT 컬럼1 FROM 테이블 GROUP BY 그룹화할 컬럼;
```

```sql
SELECT restaurant_name, COUNT(*) 
FROM food_orders 
GROUP BY restaurant_name;
```

>• 조건 1 : 없음<br/>
>• 해석 : 음식 주문 테이블에서 레스토랑 별로 몇개의 주문이 있었는지 조회해줘
{: .command-text}

![이미지](https://ifh.cc/g/C9HVJM.png)

<br>
<br>
##### * GROUP BY를 하지 않으면?

```sql
SELECT restaurant_name, COUNT(*) 
FROM food_orders;
```

>• GROUP BY를 하지 않았을 경우, 2번째 컬럼의 연산때문에 **데이터상 첫번째로 등록되어있는 레스토랑 이름이 나오게 되고, 전체 음식주문 개수가 나오게 된다.**
{: .command-text}

![이미지](https://ifh.cc/g/1r3Qwh.png)

<br>
<br>
#### 02. 조건 처리 후, 컬럼 그룹화

```sql
SELECT 컬럼1 FROM 테이블 WHERE 조건식1 GROUP BY 그룹화할 컬럼;
```

```sql
SELECT restaurant_name, cuisine_type 
FROM food_orders 
WHERE cuisine_type = 'Korean' 
GROUP BY 1;
```

>• 조건 1 : cuisine_type = 'Korean' <br/>
>• 해석 : 음식 주문 테이블에서 한식을 판매중인 레스토랑 리스트를 보여줘.
{: .command-text}

![이미지](https://ifh.cc/g/O37BO8.png)

<br>
<br>
#### 03. 컬럼 그룹화 후, 조건 처리

```sql
SELECT 컬럼1 FROM 테이블 GROUP BY 그룹화할 컬럼 HAVING 조건식1;
```

```sql
SELECT restaurant_name, AVG(price) 
FROM food_orders 
group by 1
HAVING AVG(price) > 15000
```

>• 조건 1 : AVG(price) > 15000<br/>
>• 해석 : 음식 주문 테이블에서 레스토랑별 판매한 음식의 평균 값이 15000원 이상인 데이터를 보여줘
{: .command-text}

![이미지](https://ifh.cc/g/wjRg4k.png)


<br>
<br>

#### 04. 조건 처리 후, 그룹화 후, 조건처리

```sql
SELECT 컬럼1 FROM 테이블 WHERE 조건식1 GROUP BY 그룹화할 컬럼1 HAVING 조건식2;
```

```sql
SELECT restaurant_name, AVG(price)  
FROM food_orders  
where cuisine_type = 'korean'  
group by 1  
HAVING AVG(price) > 12000
```

>• 조건 1 : AVG(price) > 15000 <br/>
>• 조건 2 : where cuisine_type = 'korean'<br/>
>• 해석 : 음식 주문 테이블에서 한식을 판매하는 레스토랑별 판매한 음식의 평균 값이 12000원 이상인 데이터를 보여줘
{: .command-text}

![이미지](https://ifh.cc/g/3zMGDC.png)


<br>
<br>
## 💡WHERE과 HAVING 헷갈리지 말자
---
>두개가 모두 조건을 걸어주어서 헷갈려 하는 경우가 많다. 하지만 위에서 말했듯이,<br/>
>**WHERE은 테이블 생성 전에 걸어주는 조건,**<br/>
>**HAVING은 테이블 생성 후에 걸어주는 조건**<br/>
>으로 생각하면 쉽다.
{: .command-text}

```sql
SELECT restaurant_name, AVG(price) 
FROM food_orders
group by 1;
```

>위의 코드에 WHERE과 HAVING을 예시를 들어보겠다.<br/>
>해석 : 음식 주문 테이블에서 레스토랑 이름과, 평균 판매 금액을 레스토랑별로 보여줘
{: .command-text}

<br>
<br>
#### 01. 그룹하기 전 WHERE을 사용했을 때

```sql
SELECT restaurant_name, AVG(price) 
FROM food_orders
WHERE AVG(price) > 12000
GROUP BY 1;
```

>**[HY000][1111] Invalid use of group function**
{: .prompt-danger}

>**결과는 Error**<br/>
>그 이유는, Query의 실행 순서에 따라 작업의 우선순위에 차이가 있기 때문이다.   <br/>
>  1) food_orders 테이블에서 `FROM food_orders`<br/>
>  2) AVG(price) > 12000 인 데이터들 중 `WHERE AVG(price) > 12000`<br/>
>  3) restaurant_name컬럼 기준으로 그룹한 `GROUP BY 1;`<br/>
>  4) restaurant_name, AVG(price)를 가져와줘 `SELECT restaurant_name, AVG(price)`<br/>  
>여기서 보면, `3)`에 테이블을 한번 GROUP BY를 통해 만들어 내는데, 테이블이 만들어지기도 전에 AVG(price) 라는 연산을 진행하여 생기는 오류이다.
{: .command-text}

<br>
<br>
#### 02. 그룹한 후HAVING을 사용했을 때

```sql
SELECT restaurant_name, AVG(price) 
FROM food_orders
GROUP BY 1
HAVING AVG(price) > 12000
```


>**결과는 정상실행**<br/>
>Query의 실행 순서는 아래와 같다.<br/>
>  1) food_orders 테이블에서 `FROM food_orders`<br/>
>  2) restaurant_name컬럼 기준으로 그룹하는데  `GROUP BY 1;<br/>`
>  3) AVG(price) > 12000 인 데이터들을만 `HAVING AVG(price) > 12000<br/>`
>  4) restaurant_name, AVG(price)를 가져와줘 `SELECT restaurant_name, AVG(price)`<br/>   
>여기서 보면, `2)`에 테이블을 한번 GROUP BY를 통해 만들어 내고 난 후에 해당 테이블에서 AVG(price) > 12000 이라는 조건을 걸기 때문에 에러가 나지 않는다.
{: .command-text}

![이미지](https://ifh.cc/g/A4jwnA.png)