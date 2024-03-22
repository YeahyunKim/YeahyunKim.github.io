---
title: JAVA study (7) - String 리터럴, String 객체
author: yeahyun
date: 2024-03-12
categories:
  - Java
  - Study
tags:
  - Java
  - JavaSpring
image: https://ifh.cc/g/NhyPJf.png
description:
  - String Literal 과 new String()은 메모리 저장의 차이가 있다.
---
## 🔎 문자열 생성
---

Java에서 문자열을 생성하는 과정은 크게 2가지 방법이 있다.
- **String literal**
- **new String()**
두개는 어떤 차이를 가지고 있을까?
<br>

#### 01. String Literal

```java
String str1 = "Hello";
String str2 = "Hello";
```

>String Literal은 문자열을 생성하는 가장 간단하고 일반적이 방법이다. 이 방식은 문자열을 큰 따옴표(" ") 로 둘러싸서 표현한다.   
>String Literal 방식으로 문자열을 생성하면, JAVA Heap 메모리 영역의 문자열 상수 풀(String Constant Pool) 영역에 값이 저장이 된다.
{: .command-text}

<br>
#### 02. new String()

```java
String str3 = new String("Hello");
```

>new String() 방식으로 문자열을 생성하면, 매번 새로운 String 객체가 생성된다. 즉, 문자열이 저장된 메모리 주소가 다르게 된다. 따라서 동일한 문자열을 가리키는 변수들도 서로 다른 메모리 주소를 참조하게 된다.
{: .command-text}


<br>
<br>
## 🔎 메모리 저장의 차이
---

```java
String str1 = "Hello"; // 리터럴
String str2 = "Hello"; // 리터럴
String str3 = new String("Hello"); //객체
```

위의 코드처럼, `str1`, `str2` 는 리터럴 방식으로 문자열을 생성했고, `str3`은 객체 방식으로 문자열을 생성했다.

<br>
![이미지](https://ifh.cc/g/C37H0N.png)

1. `str1`으로 인해 JAVA HEAP안의 String Constant pool 영역에 `"Hello"` 가 생성된다.
2. JVM이 String Constant Pool에 `"Hello"`가 존재함을 확인하고, `str2`는 새로운 값을 메모리에 할당하지 않고, `str1`의 주소를 참조한다.
3. `str3`은 객체이기 때문에 JAVA HEAP에 새로운 메모리를 할당하여 값을 저장한다.
<br>
<br>


>**String Constant Pool 란?**   
>JVM은 String Constant Pool을 사용하여 문자열 리터럴을 관리한다. 그 이유는 동일한 문자열 리터럴을 새로운 메모리에 생성하지 않고, 하나의 메모리에 값을 생성하고, 그 주소를 참조하게 만들어 메모리를 절약할 수 있고, 컴파일러가 코드를 최적화하는데 큰 도움을 준다.
{: .prompt-info}