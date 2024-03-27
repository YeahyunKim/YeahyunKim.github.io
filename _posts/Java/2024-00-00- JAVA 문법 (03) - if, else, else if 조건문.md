---
title: JAVA 문법 (03) - if, else, else if 조건문
author: yeahyun
date: 2024-03-13
categories:
  - Java
  - Grammar
tags:
  - Java
image: https://ifh.cc/g/NhyPJf.png
description:
  - 특정 조건에 따라 코드의 실행의 흐름을 제어하는 것이다.
---
## 🔎 조건문 이란
---

>개발자가 작성한 코드를 **특정 조건에 따라 코드의 실행의 흐름을 제어**하는 것이다. 조건문은 크게 아래와 같이 나뉜다.  
>• `if` 문  
>	- `else if`  
>	- `else`   
>• `switch` 문
{: .command-text}


<br>
<br>
## 🔎 if / else / else if
---
#### 01. if문

```java
if (조건식) {
	실행문1;
	실행문2;
}
```

>조건식이 `true` 일경우 중괄호 안에있는 실행문을 실행시킨다.
{: .command-text}

<br>
```java
int age = 20;

if (age >= 20) { //true
	System.out.println("성인입니다") //실행
}
if (age =< 20) { //false
	System.out.println("미성년자입니다") //실행안됨
}

// 성인입니다
```

>`age`가 20살 이상일 경우, `"성인입니다"` 가 출력이 되고, 20살 미만일 경우, `"미성년자입니다"` 가 출력되는것을 볼 수 있다. 하지만 이렇게 된 경우에는 같은 조건(나이)아래 조건문이 두번실행 되므로, 좋은 방법이 아니다.
{: .command-text}

<br>
#### 02. else문

```java
if (조건식) { 
	실행문1;
	실행문2;
} else { //if문의 조건식이 거짓일 때 실행
	실행문3;
}
```

>`else`문은 위의 **`if`문의 조건이 모두 거짓일때 실행된다.**
{: .command-text}

<br>

```java
int age = 18;

if (age >= 20) { //false
	System.out.println("성인입니다") //실행
} else { //true
	System.out.println("미성년자입니다") //실행안됨
}

// 성인입니다
```

>나이가 20살 이상이 아니라면 전부 `"미성년자"`가 출력된다.
{: .command-text}

<br>
#### 03. else if 문

```java
if (조건식1) { // false
	실행문1;
	실행문2;
} else if (조건식2) { // false
	실행문3;
	실행문4;
} else if (조건식3) { // true
	실행문5; //실행
	실행문6; //실행
} else { 
	실행문7;
}
```

>else if문의`조건식3` 이 `true` 일경우 `실행문5`, `실행문6`를 실행하고, 나머지 아래의 코드들은 실행되지 않는다.
{: .command-text}

<br>
#### 04. if문 여러개와 else if 문의 차이

그렇다면, if문이 여러개인 경우와 else if을 활용하여 만든 조건식의 차이는 무엇이 있을까?  
이는 **조건문이 실행되는 방식과, 출력하려는 값과, 주어진 조건의 개수에 따라 활용도가 다르다.**

##### 1) if문이 여러개일 경우 (불필요한 조건 검사)

```java
int age = 14;

if(age <= 7) { //~7: 미취학 
	System.out.println("미취학");
}
if(age >= 8 && age <= 13) { //8~13: 초등학생
	System.out.println("초등학생");
}
if(age >= 14 && age <= 16) { //14~16: 중학생
	System.out.println("중학생");
}
if(age >= 17 && age <= 19) { //17~19: 고등학생
	System.out.println("고등학생");
}
if (age >= 20) { //20~: 성인
	System.out.println("성인");
}
// 중학생
```

>**위의 코드는 불필요한 조건 검사가 이루어 진다.**  
>만약 나이가 5살이라면 미취학이 이미 출력되어야 하지만, 나머지 `if`문을 통한 검사도 모두 실행해야 한다.
{: .command-text}

>**코드의 효율성에서도 좋지 않다.**  
>나이가 9살인 초등학생 이라면, 미취학을 체크하는 조건인 `age <= 7`을 통해 나이가 이미 8살이 넘는다는 것을 알 수 있다. 하지만, 두번째 조건문에서 확인할 수 있듯이, `age >= 8`, `age <= 13`이란 조건문이 실행되고, 앞전에 이미 8살을 넘는다는 조건과 포함하여 **중복체크 한것을 볼 수 있다.**
{: .command-text}


<br> 
##### 2) else if 문의 효율성

```java
int age = 14;

if (age <= 7){  
    System.out.println("미취학");  
} else if (age <= 13) {  // 위에서 이미 나이가 7살 이상이라는 조건을 검사했기 때문
    System.out.println("초등학생");  
} else if (age <= 16) {  
    System.out.println("중학생");  
} else if (age <= 19) {  
    System.out.println("고등학생");  
} else {  
    System.out.println("성인");  
}
```

>**위의 코드는 앞전에서 검사한 조건을 토대로 이어서 else if문이 실행된다**  
>`age <= 7` 의 조건이 거짓이면, 그다음 조건에는 이미 나이가 7살 이상이라는 데이터를 가지고 있다.  
>따라서, 지금과 같은 상황에서는 **else if 문을 사용하는것이 더 유리하다.**
{: .command-text}


<br>
#### 05. 상황에 따라 다르게 쓰이는 if문과 else if문

>**상황**  
>온라인 쇼핑몰의 할인 시스템을 개발해야 한다. 한 사용자가 어떤 상품을 구매할 때, 다양한 할인 조건에 따라 총 할인 금액이 달라질 수 있다. 각각의 할인 조건은 다음과 같다.   
>	• 조건 1 : 아이템 가격이 10000원 이상일 때, 1000원 할인  
>	• 조건 2 : 나이가 10살 이하일 때 1000원 추가 할인  
>위의 상황에서는 **한 사용자가 동시에 여러 할인을 받을 수 있다는 점** 이다.
{: .command-text}

<br>
##### 1) 여러 할인을 받아야 하기 때문에, if문을 여러번 사용

```java
int price = 10000;  
int age = 10;  
int discount = 0;  
  
if (price >= 10000) {  
    discount = discount + 1000;  
    System.out.println("10000원 이상 구매, 1000원 할인");  
}  
if (age <= 10) {  
    discount = discount + 1000;  
    System.out.println("어린이 1000원 할인");  
}  
  
System.out.println("총 할인 금액: " + discount + "원");
// 총 할인 금액: 2000원
```

>위의 코드에서는 고객이 1만원 이상을 구매했고, 나이도 10살 이하라 2번의 할인을 받아야하므로,
>조건을 두번 나누어 주었다. 그럼 우리가 원했던 할인 시스템의 값이 출력되는것을 볼 수 있다.  
>출력 : `총 할인 금액: 2000원`
{: .command-text}

<br>
##### 2) 위와 같은 상황에 else if문을 사용하면..

```java
int price = 10000;  
int age = 10;  
int discount = 0;  
  
if (price >= 10000) {  // 1. 실행되면
    discount = discount + 1000;  
    System.out.println("10000원 이상 구매, 1000원 할인");  
} else if (age <= 10) {  // 2. 실행이 안됨
    discount = discount + 1000;  
    System.out.println("어린이 1000원 할인");  
} else {  
    System.out.println("할인 없음");  
}  

System.out.println("총 할인 금액: " + discount + "원");
//총 할인 금액: 1000원
```

>else if문을 사용하게 된다면, 첫번째 조건문이 실행된 경우, 두번째의 조건문은 실행이 되지 않기 때문에, 우리가 원했던 할인 시스템 값인 2000원이 아닌, 1000원이 출력되는 것을 볼 수 있다.  
>출력 : `총 할인 금액: 1000원`
{: .command-text}



<br>
<br>
## 🔎 정리
---
>조건문도 상황에 따라 if문을 여러개 쓸지, else if문을 사용할지 등 고려해야할 부분이 많다.
>코드를 막 적는게 중요한게 아닌, 상황에 맞에 코드를 어떻게 작성해야할지를 심중히 고민해봐야 좋은 코드가 될 것이다.
{: .prompt-tip}