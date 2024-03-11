---
title: JAVA Install (1) - MacOS 에 JAVA 17설치하기
author: yeahyun
date: 2024-02-25
categories:
  - Java
  - Installㅤ
tags:
  - Java
image: https://ifh.cc/g/wvbwro.png
---
## MacOS에 JAVA 11설치하기

---
#### 01. 터미널을 실행하여 자바 설치 여부 및 버전 확인

터미널(terminal)을 열어 `java --version` 이라 입력후 엔터를 치면 나의 맥북에 Java 설치 유무 및 버전 체크가 가능하다.
![이미지](https://ifh.cc/g/PKNZKO.png)

>아직까지 자바가 설치되지 않았다고 나와있다.
{: .command-text}

<BR>
#### 02. oracle의 java downloads 사이트 접속

[다운로드 사이트](https://www.oracle.com/kr/java/technologies/downloads/#jdk21-mac)에 접속해서, `MacOS` 운영체제를 선택해주고, 내가 사용하는 맥북은 ARM 기반이므로,  `ARM64 DMG Installer` 를 다운로드 받았다. 본인에게 적절한 파일을 찾아 다운로드 해도 된다.

![이미지](https://ifh.cc/g/SYhcvY.png)
>인텔의 경우, x64 파일을 다운로드 받으면 된다.
{: .prompt-tip}

<BR>
#### 03. 자바 설치

자기가 설치할 파일 경로를 잘 설정하고, 계속 다음을 눌러 설치완료한다.

![이미지](https://ifh.cc/g/A2hVmK.png)

<br>
#### 04. 자바 설치 확인
다시 터미널로 가서, `java --version`을 입력하여 자바가 잘 설치 되었는지 확인한다.

![이미지](https://ifh.cc/g/SRQ7pT.png)


<br>
#### 05. 환경변수 설정

간단하게 Java의 경로가 어디있는지 확인할 수 있는 환경변수를 설정하겠다.
먼저, 본인이 설치한 Java의 경로를 터미널로 열어준다. 만약, 본인이 설정한 경로를 모르겠다 하면,
`cd /Library/Java/JavaVirtualMachines/jdk-21.jdk/Contents/Home` 를 터미널에 입력하자.

>다운로드 받은 파일이 다를경우, 경로 중간의 [jdk-21.jdk] 의 폴더명이 다를 수있다.
>그럴경우, Library 부터 차근차근 폴더를 타고 올라가는걸 추천한다.
{: .prompt-danger }

1) 터미널에 `vi ~/.zshrc`를 입력해 환경설정창을 열어준다.

2) `i` 키를 눌러 INSERT 모드로 전환한다.

3) 아래 세개를 기입한다. (이미지 참고)   
- `export JAVA_HOME=/Library/Java/JavaVirtualMachines/zulu-11.jdk/Contents/Home/bin`  
- `export CLASSPATH=/Library/Java/JavaVirtualMachines/zulu-11.jdk/Contents/Home/lib`  
- `export PATH=${PATH}:$JAVA_HOME/bin`**

![이미지](https://ifh.cc/g/CM6osA.jpg)

4) ESC를 누르고 `:wq` 를 눌러 저장하고 INSERT 모드를 종료한다.

5) `source ~/.zshrc` 입력 (변경된 내용 저장)


<br>
#### 06. 환경변수 설정 확인
터미널에 `echo $JAVA_HOME` 와 `java -version` 를 입력해보면, 현재 저장되어있는 자바 경로와 버전이 나타나는 걸 볼 수 있다.

![이미지](https://ifh.cc/g/a47V5a.png)