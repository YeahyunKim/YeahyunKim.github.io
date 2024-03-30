---
title: JavaSpring 플러그인 (01) - thymeleaf
author: yeahyun
date: 2024-02-27
categories:
  - JavaSpring
  - Pluginㅤ
tags:
  - JavaSpring
  - Plugin_
image: https://ifh.cc/g/wvbwro.png
description:
  - html 동적 렌더링 하기
---
## thymeleaf - HTML 동적 렌더링
---
#### thymeleaf(타임리프)

타임리프는 백엔드 서버에서 Html을 동적으로 렌더링  **Java Template Engine** 이다.
해당 플러그인의 주요 목적은 유지 관리가 수월한 템플릿을 작성하도록 지원해주고, 타임리프의 핵심 기능인 Natural Template 을 통해 제공해주는데, 서버 사이드 렌더링을 하는데 필요한 데이터 값이 없더라도, 프로토 타입으로서의 역할을 해줄 수 있는 걸 말한다.

**이 특징이 기존 Java Template Engine 중의 하나인 Jsp 와 가장 다른 점인데 Jsp 는 화면을 보기 위해선 서버의 도움이 필요하다. 그치만 Thymeleaf 는 서버의 도움없이 프로토 타입 형태로도 뷰를 볼 수 있다.**

그렇기 때문에 Thymeleaf 를 사용한다면 디자인팀과 개발팀 사이에 생길 수 있는 커뮤니케이션 비용을 줄여줄 수 있다.

<br>

#### 01. thymeleaf 가 제공해주는 Template 6가지

- HTML
- CSS
- Javascript
- TEXT
- Raw
- XML

<br>

#### 02. Thymeleaf 라이브러리 추가

`bulid.gradle` 파일에서 의존성 라이브러리를 추가해준다.

```java
dependencies {  
    implementation 'org.springframework.boot:spring-boot-starter-thymeleaf'
    implementation 'org.springframework.boot:spring-boot-starter-web'  
    testImplementation 'org.springframework.boot:spring-boot-starter-test'  
}
```

<br>
#### 03. Thymeleaf 기본 경로

타임리프는 기본적으로 templates 폴더(root) 안에 있는 파일들을 기준으로 타임리프의 기능을 실행시켜주기 때문에,  **templates** 폴더가 없을경우 생성해 주어야하고, 테스트를 위해 폴더 안에 **hello.html** 파일도 생성해 주었다.

**프로젝트 디렉터리(root) > src > main > resources > templates**
![이미지](https://ifh.cc/g/dmbCMF.png)


<br>

