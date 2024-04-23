---
title: JAVA study (11) - Static 변수와 메모리 구조
author: yeahyun
date: 2024-04-23
categories:
  - Java
  - Study
tags:
  - Java
image: 
description:
  - static 변수와 instance 변수의 차이점, 그리고 메모리 구조의 차이점에 대해 공부합니다.
---
## 🔎 Static 변수
---
>#### Static 변수란?

>**static** 변수는 클래스 수준에서 선언할 수 있고, 클래스의 모든 인스턴스에서 공유된다. 즉, 하나의 static 변수가 모든 객체에서 사용된다.
{: .command-text}
<br>
<br>

이게 도대체 무슨말인가.. 바로 코드를 작성해서 알아보았다.

<br>
<br>

>#### Static 변수 예시

```java
public class Counter {
    // static 변수 선언
    public static int staticCount = 0;

    // 변수 선언
    public int count = 0;

    public Counter() {
        staticCount++; // static 변수 count 증가
        count++; // 일반 변수 count2 증가
    }
```

>먼저, 차이를 한눈에 알아보기 위해 `static`으로 선언한 변수 `count` 와 `일반 변수` `count2`를 만들었다.  
>`Counter` 라는 메서드를 해당 메서드가 호출될 때. 마다 `count`. 와. `count2`의. 값을 증가 시켜주었다.
{: .command-text}

<br>
```java
public class Counter {  
    public static int staticCount = 0;  
  
    public int count = 0;  
  
    public Counter() {  
        staticCount++;
        count++;
    }  
  
    public static void main(String[] args) {  
        Counter c1 = new Counter();  
		System.out.println("staticCount: " + Counter.staticCount);  
		System.out.println("count: " + c1.count);  
		  
		Counter c2 = new Counter();  
		System.out.println("staticCount: " + Counter.staticCount);  
		System.out.println("count: " + c2.count);
    }  
}
```

>이후 메인 메서드 안에 `c1`, `c2` 객체를 생성해 주는데, 여기서 `c1` 과 `c2` 는 다른 객체이고 메모리 주소도 완벽하게 다르기 때문에 `count`의 값이 각각 `1` 이여야 한다. 출력해본 결과값을 확인해 보자.
{: .command-text}

<br>

```java
public class Counter {  
    public static int staticCount = 0;  
  
    public int count = 0;  
  
    public Counter() {  
        staticCount++;
        count++;
    }  
  
    public static void main(String[] args) {  
        Counter c1 = new Counter();  
		System.out.println("staticCount: " + Counter.staticCount);  
		System.out.println("count: " + c1.count);
		// staticCount: 1
        // count: 1
		  
		Counter c2 = new Counter();  
		System.out.println("staticCount: " + Counter.staticCount);  
		System.out.println("count: " + c2.count);
		// staticCount: 2
		// count: 1
    }  
}
```

>출력값을 확인해보면, `c1` 과 `c2`객체의 `count` 값은 동일하게 `1` 이 나왔지만,  
>**`c1` 과 `c2`객체의 `staticCount` 값은 각각 `1` 과 `2`가 나왔다.**
>왜 이렇게 출력될까?
{: .command-text}

<br>
<br>

>#### 메모리 구조 차이

![image](https://ifh.cc/g/m3LS11.png)
>먼저, 인스턴스 변수의 경우, **객체를 생성할 때 마다 `Counter` 인스턴스는 새로 만들어 지고, 그 인스턴스에 포함된 `count`변수도 새로 만들어 진다.** 여기서 이 인스턴스는 `메모리 heap`dㅕ영역에 따로 저장이 된다. 즉, `c1` 과 `c2`의 `count`는 전혀 다른 변수라는 말이 된다.
{: .command-text}


<br>
<br>
![image](https://ifh.cc/g/bVXMB3.png)
>static 변수는 메모리의 `method` 영역에 값이 저장된다. 그리고 `heap`에 `c1`과 `c2` 객체는 `staticCount`의 값을 `method` 영역의 하나의 값으로 공유받는다.  
>따라서 `c1.staticCount` 와 `c2.staticCount` 는 동일한 `2`의 값이 출력되는 것을 볼 수 있다.
{: .command-text}

<br>
<br>
그렇다면 이 static 변수를 활용하면 어떤 이점을 얻게 될 수 있고, 주의할점은 있을까?

<br>
<br>
>#### static 변수의 특징

>• **메모리 효율성** : Static 변수는 클래스 수준에서 선언되므로 메모리를 효율적으로 사용할 수 있고, 모든 객체가 하나의 static 변수를 공유하기 때문에 메모리 사용량이 줄어든다.  
><br>
>• **초기화** : Static 변수는  **클래스가 로드될 때 자동으로 초기화 된다.** 이때 기본값으로 초기화 되고, 필요에 따라서 명시적으로 초기화할 수 있다.  
><br>
>• **공유** : Static 변수는 모든 인스턴스에서 공유된다. 따라서 한 객체에서 변경한 static 변수의 값은 다른 객체에서도 반영된다.
><br>
>• **접근성** : Static 변수는 객체 생성 없이도 접근할 수 있다. **클래스 이름으로 직접 접근할 수 있다.**
{: .command-text}

<br>

>static 변수는 프로그램 종료 시까지 메모리에 존재하므로, 메모리 누수가 발생할 수 있다.
{: .prompt-danger}

