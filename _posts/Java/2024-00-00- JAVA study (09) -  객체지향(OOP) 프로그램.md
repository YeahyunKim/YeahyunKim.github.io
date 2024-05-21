---
title: JAVA study (09) - 객체지향(OOP) 프로그램
author: yeahyun
date: 2024-05-20
categories:
  - Java
  - Study
tags:
  - Java
image: https://ifh.cc/g/NhyPJf.png
description:
  - 절차지향과 객체지향의 차이점
---
## 🔎 객체지향 프로그래밍(Object Oriented Programming)
---
>#### 객체지향이란?

>**객체지향**은 **실제 세계를 모델링**
 하여 소프트웨어를 개발하는 방법이다. 프로그램을 독립적인 객체들의 모임으로 파악하고, 이 **객체들 간의 상호작용을 통해 데이터를 처리**하는 방식이다.
{: .command-text}
<br>
<br>
>#### 객체지향의 특징

##### **1. 추상화(Abstraction)**

>• **정의 : 복잡한 현실 세계를 단순화하여 필요한 부분만을 프로그램에 반영**    
>• 예시 : 차량을 객체로 모델링할 때, 엔진, 바퀴 등의 필수 요소만을 포함시키고, 차량의 색상이나 브랜드는 선택적으로 추가할 수 있음. 이렇게 하여 복잡한 차량이라는 개념을 단순화하여 프로그램 내에서 다룰 수 있음  
{: .command-text}

>아래의 사진을 보면, 자동차는 `Engine`과 `Wheel`이 있어야 작동한다는 공통점을 가진다. `현대`, `기아` 모두 자동차에 해당되며, 공통적인 특징(엔진, 바퀴)들을 추상화 집합안에 모아두고 이를 활용한다고 생각하면 된다. 그럼 `현대`와 `기아`같은 다른 자동차 브랜드가 추상화를 통해 다른 곳의 코드를 수정할 필요없이 추가로 만들 부분만 새로 생성해주면 된다.
{: .command-text}

![이미지](https://ifh.cc/g/3xTdsz.png)


```java
public class Car {
    // 필수 요소
    private Engine engine;
    private Wheel[] wheels;
    private SteeringWheel steeringWheel;

    // 선택적 요소
    private String color;
    private String brand;

    // 생성자 - 필수 요소만을 받아 초기화
    public Car(Engine engine, Wheel[] wheels) {
        this.engine = engine;
        this.wheels = wheels;
        this.steeringWheel = steeringWheel;
    }

    // 선택적 요소 설정 메소드
    public void setColor(String color) {
        this.color = color;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }
}

```
<br><br>
##### 2. 캡슐화(Encapsulation)

>• **정의 : 객체의 데이터와 메소드를 하나로 묶고, 외부로부터 데이터를 보호 및 직접적인 접근을 제한**  
>• 예시 : 은행 계좌 객체에서 잔액(balance)은 외부에서 직접 접근할 수 없도록 private으로 설정하고,  
>   입금(deposit)과 출금(withdraw) 같은 메소드를 통해서만 잔약을 변경  
{: .command-text}

>아래 예시 코드를 보면, `balance`는 `private`으로 설정되어 **외부에서 직접 접근할 수 없다.**   
>대신에 `deposit` 과 `withdraw` 메소드를 통해서만 `balance`를 변경할 수 있다.
{: .command-text}

```java
public class BankAccount {
    private double balance; // 잔액은 외부에서 직접 접근할 수 없도록 private으로 설정

    // 생성자를 통해 초기 잔액을 설정
    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    // 입금 메소드: 잔액에 금액을 더함
    public void deposit(double amount) {
        balance += amount;
    }

    // 출금 메소드: 잔액에서 금액을 뺌. 잔액이 부족하면 출금하지 않음
    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            System.out.println("Insufficient funds");
        }
    }

    // 잔액 조회 메소드: 외부에서 잔액을 조회할 수 있도록 public 메소드 제공
    public double getBalance() {
        return balance;
    }

    // 메인 메소드: 은행 계좌 객체를 생성하고 입금, 출금 후 잔액을 출력
    public static void main(String[] args) {
        BankAccount account = new BankAccount(1000.0);
        System.out.println("Initial Balance: " + account.getBalance());
        account.deposit(500.0);
        System.out.println("Balance after deposit: " + account.getBalance());
        account.withdraw(200.0);
        System.out.println("Balance after withdrawal: " + account.getBalance());
    }
}
```
<br>
> 이렇듯, 캡슐화는 **클래스 안에 서로 연관 있는 속성과 기능들을 하나의 캡슐(capsule)로 만들어서, 외부로부터 데이터를 보호하는 것**을 뜻한다.
{: .prompt-info }


<br>