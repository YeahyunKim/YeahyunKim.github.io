---
title: JAVA 문법 (5) - for, while, do-while 반복문
author: yeahyun
date: 2024-03-13
categories:
  - Java
  - Grammar
tags:
  - Java
image:
---
## 🔎 반복문이란
---

>코드를 반복적으로 실행하게 하는 제어문의 한 종류이다. 반복문의 종류는 크게 세가지가 있다.  
>• `for` 문  
>• `while`문  
>• `do-while` 문
{: .command-text}



<br>
<br>
## 🔎 for 문
---
```java
int num = 0;

for(int i = 0(초기화); i < 10(조건식); i++(증감식) {
	num += i;
}
	
System.out.println(num);
```

>• for문은 초기화, 조건식, 증감식으로 구성된 제어 구조  
>• 반복 횟수가 정해져 있는 경우에 사용  
>• 주어진 횟수만큼 반복을 수행하며, 반복 횟수를 명시적으로 알 수 있기 때문에 사용하기 간편
{: .command-text}

<br>
```java
int sum = 0;  
int endNum = 3;  
  
for (int i = 1; i <= endNum; i++) {  
    sum = sum + i;  
    System.out.println("i= " + i + " sum=" + sum);  
}

//i= 1 sum=1
//i= 2 sum=3
//i= 3 sum=6
```

>`endNum`및 또는 반복계수 `i` 값에 따라 몇번의 반복문을 돌릴지 설정할 수 있다.
{: .command-text}

<br>
<br>

## 🔎 while 문
---
```java
증감변수

while(조건식) {
	실행문1;
	증감식1;
}
```

>• while문은 주어진 조건식이 참인 동안 반복을 수행하는 제어 구조  
>• 반복 횟수가 정해져 있지 않고, 조건이 만족될 때까지 반복을 수행해야 할 때 사용  
>• 조건식이 처음부터 거짓이면 반복을 수행하지 않을 수 있음
{: .command-text}

<br>
```java
int count = 0;

while (count < 3) {  
    count = ++count;  
    System.out.println("현재 숫자는: " + count);  
}
// 현재 숫자는: 1
// 현재 숫자는: 2
// 현재 숫자는: 3
```

>`count`의 값을 while문 안에서 증감시켜주어, 원하는 구간까지 반복되도록 설정할 수 있다.  
{: .command-text}

<br>
<br>
## 🔎 do-while문
---

```java
do {
	실행문1;
} while (조건식);
```


>• do-while문은 while문과 유사하지만, 코드 블록을 실행한 후에 조건식을 평가  
>• **코드 블록을 최소한 한 번은 실행하고, 그 후에 조건식을 평가하여 반복 여부를 결정**  
>• 건식이 처음부터 거짓이더라도 코드 블록은 최소한 한 번은 실행되므로, 반복 실행을 보장할 때 사용
{: .command-text}


<br>

```java
int i = 1;  
  
do {  
    System.out.println("현재 숫자는: " + i);  
    i++;  
} while (i < 1);

// 현재 숫자는: 1
```

>위의 코드를 보면, 먼저 **do 영역에서 코드가 반드시 실행된다.** 따라서, i의 값이 1이므로,  
>`"현재 숫자는: 1"` 이라는 출력값을 볼 수 있다.  
>그 이후에 while영역에서 `i < 1` 의 조건이 거짓이기 때문에 반복문을 종료한다.
{: .command-text}