---
title: JAVA study (08) - Array 배열을 print 했을때 주소값이 나오는 이유
author: yeahyun
date: 2024-03-19
categories:
  - Java
  - Study
tags:
  - Java
image: https://ifh.cc/g/NhyPJf.png
description:
  - 참조값에 대한 기본적인 이해
---
## 🔎 배열을 출력했을때 메모리 주소가 나오는 이유
---

```java
int[] arrayValue = new int[5] //배열 생성
System.out.println(arrayValue) // [I@a09ee92
```

>위에는 `[1, 2, 3, 4, 5]` 의 값을 가지고있는 배열을 생성하였다.  
>그리고 해당 변수를 출력해보면 메모리 주소값이 출력이 되는데, `[I@a09ee92` 이는 왜이럴까?
{: .command-text}

<br>
<br>

#### 01. 배열 참조값 보관

```java
int[] arrayValue = new int[1, 2, 3, 4, 5] //배열 생성
System.out.println(arrayValue) // [I@a09ee92
```

>`int[] students` 변수는 `new int[5]` 로 생성한 배열의 참조값을 가지고 있다.
{: .command-text}

>1. `new int[5]` 로 배열을 생성하면 배열의 크기만큼 매모리를 확보한다.  
>2. 배열을 생성하고 나면 자바는 메모리 어딘가에 있는 이 배열에 접근할 수 있는 참조값(주소)`[I@a09ee92` 를 반환한다.  
>3. 앞서 선언한 배열 변수인 `int[] students` 에 생성된 배열의 참조값`[I@a09ee92`을 보관한다.  
>4. `int[] students`의 변수를 통해, [1, 2, 3, 4, 5]의 배열에 접근할 수 있다.
{: .command-text}

<br><br>
#### 02. 간단하게 풀어보기

```java
int[] arrayValue = new int[5]; //1. 배열 생성  
int[] students = [I@a09ee92; //2. new int[5]의 결과로 [I@a09ee92 참조값 반환
arrayValue = [I@a09ee92 //3. 최종 결과
```


>이는 메모리의 STACK 과 HEAP에 관련이 있다.  
>이 문제는 추후에 정리하여 글을 올리도록 하겠다.
{: .prompt-tip}