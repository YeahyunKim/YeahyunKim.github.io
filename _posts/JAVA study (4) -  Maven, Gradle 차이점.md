---
title: JAVA study (4) -  Maven, Gradle 차이점
author: yeahyun
date: 2024-02-26
categories:
  - Java
  - Study
tags:
  - Java
  - JavaSpring
image: https://ifh.cc/g/wvbwro.png
---
## 메이븐(Maven) 이란?
---
#### 01. 메이븐 정의

Maven은 주로 Java 개발에 사용되는 **프로젝트 관리 빌드 도구** 이다.  Apache Ant의 대안으로 만들어 졌으며, Apache Software Foundation에서 호스팅하는 Maven은 자카르타 프로젝트의 일부로 시작되었다고 한다.

<BR>
#### 02. 메이븐 특징

- 빌드 절차를 간소화
- 정형화된 빌드 시스템을 제공
- 프로젝트 정보를 제공
- Pom.xml 파일을 통해 프로젝트를 빌드
![이미지](https://t1.daumcdn.net/cfile/tistory/999BF0365A53402124)
<br>
#### 03. 메이븐의 LifeCycle

미리 정의하고 있는 빌드 순서를 라이프사이클이라고 한다.
각 빌드 단계를 phase라 하며 각 phase들은 서로 의존 단계를 가지고 있는데,
메이븐은 프로젝트 생성에 필요한 단계(phase)들을 Build LifeCycle 이라고 하고,
default, clean, site 세가지로 표준 정의한다.

![](https://t1.daumcdn.net/cfile/tistory/9975E4405A533FDF1A)

- clean : 빌드 시 생성되었던 산출물을 삭제
    1. pre-clean : clean 작업 전에 사전작업
    2. clean : 이전 빌드에서 생성된 모든 파일 삭제
    3. post-clean : 사후작업
- default : 프로젝트 배포절차, 패키지 타입별로 다르게 정의됌
    1. validate : 프로젝트 상태 점검, 빌드에 필요한 정보 존재유무 체크
    2. initialize : 빌드 상태를 초기화, 속성 설정, 작업 디렉터리 생성
    3. generate-sources : 컴파일에 필요한 소스 생성
    4. process-sources : 소스코드를 처리
    5. generate-resources : 패키지에 포함될 자원 생성
    6. compile : 프로젝트의 소스코드를 컴파일
    7. process-classes : 컴파일 후 후처리
    8. generate-test-source : 테스트를 위한 소스 코드를 생성
    9. process-test-source : 테스트 소스코드를 처리
    10. generate-test-resources : 테스팅을 위한 자원 생성
    11. process-test-resources : 테스트 대상 디렉터리에 자원을 복사하고 가공
    12. test-compile : 테스트 코드를 컴파일
    13. process-test-classes : 컴파일 후 후처리
    14. test : 단위 테스트 프레임워크를 이용해 테스트 수행
    15. prepare-package : 패키지 생성 전 사전작업
    16. package : 개발자가 선택한 war, jar 등의 패키징 수행
    17. pre-integration-test : 통합테스팅 전 사전작업
    18. integration-test : 통합테스트
    19. post-integration : 통합테스팅 후 사후작업
    20. verify : 패키지가 품질 기준에 적합한지 검사
    21. install : 패키지를 로컬 저장소에 설치
    22. deploy : 패키지를 원격 저장소에 배포
- site : 프로젝트 문서화 절차
    1. pre-site : 사전작업
    2. site : 사이트문서 생성
    3. post-site : 사후작업 및 배포 전 사전작업
    4. site-deploy : 생성된 문서를 웹 서버에 배포


<br>
<br>
## 그래들 (Gradle) 이란?
---

#### 01. 그래들의 정의

Gradle은 다국어 소프트웨어 개발을 위한 **빌드 자동화 도구** 이다. 컴파일과 패키징부터 테스트, 배포, 게시까지의 작업에서 개발 프로세스를 제어한다.

<br>

#### 02. 그래들의 특징

- 설정 주입 방식(Configuration Injection)을 사용
- 오픈소스 기반의 빌드 자동화 시스템으로 ***Groovy** 기반 DSL(Domain-Specific-Language)로 작성한다.  
    ***Groovy** : JVM에서 실행되는 스크립트 언어

![](https://blog.kakaocdn.net/dn/cGSVUn/btrwhTPuryR/0M8CsKOnjhKxbsek5cPIk1/img.png)

- src/main/java : 배포할 자바 소스코드 디렉토리
- src/main/resources : 배포한 설정 파일 디렉토리
- gradle/wrapper 디렉토리 : 내장 task wrapper. 개발자들이 직접 gradle을 설치하지 않아도 빌드가 가능하다.
- gradlew : 리눅스 또는 맥 OS 용 실행 쉘 스크립트 파일이다.
- gradlew.bat : 윈도우용 실행 배치 스크립트 파일이다.
- gradle-wrapper.jar : JAR 형식으로 압축된 wrapper파일이다. gradlew나 gradlew.bat 파일이 프로젝트 안에 설치되는 이 파일을 사용하여 gradle task를 실행한다.
- gradle-wrapper.properties : gradle wrapper 설정정보 파일이다. wrapper의 버전등을 확인할 수 있다.
- build.gradle : 프로젝트의 라이브러리 의존성, 플러그인, 라이브러리 저장소등을 설정하는 빌드 스크립트 파일이다.
- settings.gradle : 프로젝트의 구성 정보 파일. 멀티 프로젝트를 구성하여 프로젝트를 모듈화할 경우, 하위 프로젝트의 구성을 설정할 수 있다.
