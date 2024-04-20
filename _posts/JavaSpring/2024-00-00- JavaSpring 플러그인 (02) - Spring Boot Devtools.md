---
title: JavaSpring 플러그인 (02) - Spring Boot Devtools
author: yeahyun
date: 2024-02-27
categories:
  - JavaSpring
  - Pluginㅤ
tags:
  - Java
  - JavaSpring
image: https://ifh.cc/g/wvbwro.png
description:
  - 로컬서버를 자동으로 재가동 시켜주기
---
## Spring Boot Devtools - 서버 자동 재가동
---
>#### Spring Boot Devtools

소스의 변경이 일어날 때마다 스프링부트의 로컬 서버를 매번 재실행 해줘야하는 번거로움이 있었다..

- 소스 변경
- 로컬 서버 재실행
- 웹사이트 새로고침

하지만, Spring Boot Devtools 를 사용하면 소스의 변경이 일어났을때 **서버를 재시작하지 않아도, 서버가 자동으로 재가동** 시켜주는 매우 편리한 플러그인이다.

<BR>
>#### 01. build.gradle에 플러그인 추가

아래의 코드를 `build.gradle` 파일에 추가해준다.
```java
dependencies {  
    developmentOnly 'org.springframework.boot:spring-boot-devtools'
}
```

<br>
>#### 02. Intellij 세팅 변경 (Compiler)

`Settings -> Build, Execution, Deployment -> Compiler`

인텔리제이의 세팅에서 위의 경로로 이동하여, `Build project automatically` 를 체크(active) 한다.
![이미지](https://ifh.cc/g/fQ5wgJ.png)

<BR>

>#### 03. Intellij 세팅 변경 (Advanced Settings)

`Settings -> Advanced Settings`

인텔리제이의 세팅에서 위의 경로로 이동하여,   
`Allow auto-make to start even if developed application is currently running.`
을 체크(active) 한다.
![이미지](https://ifh.cc/g/m1LPoj.png)

<br>
>#### 04. application.properties파일에 설정 추가

- Html Reload 를 위한 코드

```java
spring.thymeleaf.cache=false spring.thymeleaf.prefix=file:src/main/resources/templates/
```
<br>
- CSS, Js Reload 를 위한 코드

```java
spring.resources.static-locations=file:src/main/resources/static/
```


<br>

>#### 05. Chrome 확장자 추가 (LiveReload)

크롬에서 [LiveReload](https://chromewebstore.google.com/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei) 라는 확장자 프로그램을 설치한다.
![이미지](https://ifh.cc/g/8K7kWp.png)


>#### 06. 마무리하기

설치가 완료되면, 인텔리제이에서 html 및 소스코드를 수정했을때 정상적으로 서버가 자동으로 재실행 되어 서버를 수동으로 재가동 시킬 필요가 없어진다. 개발을 할 때 시간을 줄여주는 아주 고마운 플러그인이였다. 