---
title: JAVA 문법 (01) - 변수 Variable
author: yeahyun
date: 2024-03-11
categories:
  - Java
  - Grammar
tags:
  - Java
image: https://ifh.cc/g/NhyPJf.png
description:
  - 변수(Variable)는 데이터를 저장하는 공간이다. 변수는 특정 데이터 타입을 가지며, 이 데이터 타입에 따라 저장할 수 있는 데이터의 종류와 크기가 결정된다.
---
## 🔎 변수(Variable)
---
#### 01. 변수란?

>변수(Variable)는 데이터를 저장하는 공간이다.  
>변수는 특정 데이터 타입을 가지며, 이 데이터 타입에 따라 저장할 수 있는 데이터의 종류와 크기가 결정된다. 변수를 사용하면 데이터를 보다 쉽게 관리할 수 있고, 코드 내에서 값을 재사용하거나 변경할 수 있다.
{: .command-text}

<br>
#### 02. 왜 사용해야하나?
```java
public class Var1 {  
    public static void main(String[] args) {  
        System.out.println(10);  
        System.out.println(10);  
        System.out.println(10);  
    }  
}

//10
//10
//10
```

위의 코드는 숫자 10을 3번 출력시키는 코드이다. 만약 여기서 우리가 10 -> 20으로 출력하고 싶으면, 어떻게 해야할까?

```java
public class Var1 {  
    public static void main(String[] args) {  
        System.out.println(20);  
        System.out.println(20);  
        System.out.println(20);  
    }  
}

//10
//10
//10
```

답은 간단하다. 10을 모두 20으로 바꿔주면 된다.
하지만, 코드의 양이 방대하다고 가정해보면, 10을 20으로 수없이 많이 바꿔줘야 한다.
모든 프로그래밍 언어는 이런 문제를 해결하기 위해 **변수(variable)**라는 기능을 제공한다. 변수는 이름 그대로 변할 수 있다는 뜻이다.

<br>
#### 03. 변수 선언하기

```java
int a;
```

자바에서 변수를 선언하는 방법은
`타입 변수명 = 값;` 으로 선언할 수 있다.
위에 코드를 해석해보면 숫자 `정수타입(integer)인 a라는 그릇` 으로 해석할 수 있다.
<br>

```java
int c,d
```

한번에 여러 변수를 선언할 수도 있다.

<br>
#### 04. 변수 초기화

```java
int a;  
a = 1;
```

변수를 선언하고, 선언한 변수에 처음으로 값을 저장하는 것을 **변수 초기화** 라고 한다.
위의 코드는 a라는 변수를 선언하고, a에 초기값으로 정수 1의 값을 저장한것을 볼 수 있다.

<br>
#### 05. 변수를 초기화하지 않는다면?

```java
public class Var6 {
     public static void main(String[] args) {
		int a;
		System.out.println(a); //주석을 풀면 컴파일 에러 발생 
	}

}
```

컴퓨터에서 메모리는 여러 시스템이 함께 사용하는 공간이다.  
따라서 다양한 프로그램, 브라우저 등등의 시스템에 의해 값이 계속 저장된다.  
하지만 초기값을 주지 않은 변수는 해당 메모리 공간에 어떤 값이 있었는지 아무도 모른다.  
이로인해, **값을 초기화 하지 않으면 이상한 값이 출력**될 수 있는데, **이런 문제를 예방하기 위해 자바는 변수를 초기화 하도록 강제한다.**
