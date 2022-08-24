---
title: "Mac에서 zulu(OpenJDK 17) 설치 및 IntelliJ설정"
last_modified_at: 2022-08-23T16:14:36-05:00
categories: 
    -Java, IntelliJ
---

> ## Open JDK 설치환경

* Mac OS
* HomeBrew ([설치방법 링크](https://velog.io/@funnykyeon/Homebrew-%EC%84%A4%EC%B9%98))

> ## JDK란 무엇일까요?

JDK(Java Development kit) - Java 애플릿 및 응용 프로그램을 작성하려면 이 JDK 같은 개발 키트가 필요하다. JDK는 JRE(Java Runtime Environment)와 Java 컴파일러, JVM(Java Virtual Machine)을 포함하고 있는 소프트웨어 패키지이다.

> ## Oracle JDK 와 OpenJDK 중 무엇을 택해야할까요?

Java 애플리케이션을 실행하기 위해서는 JVM이 필요하고 컴파일하기 위해서는 JDK가 필요하다.
일반적으로 JDK를 설치하면 JVM(Hotspot이라고도 표현, Java 기술의 핵심)도 함께 설치된다.

JDK는 2개 버전으로 나뉜다. 하나는 폐쇄적인 상업 코드 기반(유료)의 Oracle JDK이고 하나는 오픈 소스 기반의 OpenJDK이다.

둘 간의 큰 차이?
Oracle JDK에 존재하고 OpenJDK에는 없는 대표적 기능으로 글꼴 라이브러리와 Java Web Start가 있다. 사용자의 웹 브라우저에서 자바 애플릿을 실행하려면 필요한 기능이다. 서버 애플리케이션 개발에는 쓰이지 않는 기능들이다.

위 설명과 같이 큰차이가 없다면 굳이 Oracle JDK를 써야할 이유는 없는거 같다.

> ## Open JDK 설치

우선 zulu를 설치합니다. 
[zulu 다운로드 링크](https://www.azul.com/downloads/?package=jdk#download-openjdk)

zulu를 사용하여 OpenJDK를 설치할것이며 zulu는 100% 오픈 소스이며 무료로 다운로드 할 수 있습니다.
설치전 우선 brew 업데이트를 진행한다.
```
$ brew update && brew upgrade
```

zulu를 검색하게 되면 다음 사진과 같은 결과가 나온다.
```
$ brew search zulu
```
![](https://images.velog.io/images/funnykyeon/post/ea4c0781-96f3-4732-97d7-2f5281245de3/image.png)만약 각 버전이 나오지 않고 zulu만 나온다면 다음 명령어를 실행하면 나오게 된다. 
```
$ brew tap homebrew/cask-versions
```
<br>

자바 8과 10을 사용하기 때문에 zulu와 zulu8을 설치하도록 하겠다. 자바8을 원하지 않는 분은 zulu만 설치하면 된다.
```
$ brew install --cask zulu zulu17
```
설치를 마친후 자바 버전을 확인해보면 JDK18로 설치되어 있는것을 확인할 수 있다.
```
$ java -version
```
![](https://images.velog.io/images/funnykyeon/post/04f5b831-524d-4578-8622-63fc2558f82e/image.png)