---
title: "String, StringBuilder, StringBuffer 차이점과 장단점"
date: 2022-08-20
last_modified_at: 2022-08-20
toc: true
toc_sticky: true
categories: 
  - Java
tags: 
  - [Java]
---
StringBuffer와 StringBuilder


![](https://velog.velcdn.com/images/funnykyeon/post/e2376ae5-d552-46e0-acdb-94b8d199e546/image.png)

우선 String, StringBuffer, StringBuilder 모두 문자열을 저장하고, 관리하는 클래스입니다.

> #  String

먼저 String과 다른 클래스(StringBuffer, StringBuilder)의 차이점은 두 문자열 클래스의 아주 기본적인 차이는 String은 불변, StringBuffer는 가변이 있습니다.



String은 문자열을 대표하는 것으로 문자열을 조작하는 경우 유용하게 사용할 수 있습니다. 문자열, 숫자, char 등은 concat할때는 StringBuffer, StringBuilder를 사용할 수 있습니다. 단, 복잡한 경우 의미가 있고, 단순한 경우에는 굳이 StringBuffer, StringBuilder를 쓰지 않고 +연산자를 활용해 직접 합지면 됩니다.



String 객체는 한번 생성되면 할당된 메모리 공간이 변하지 않습니다. + 연산자 또는 concat 메서드를 통해 기존에 생성된 String 클래스 객체 문자열에 다른 문자열을 붙여도 기존 문자열에 새로운 문자열을 붙이는 것이 아니라,


새로운 String 객체를 만든 후, 새 String 객체에 연결된 문자열을 저장하고, 그 객체를 참조하도록 합니다. (즉, String 클래스 객체는 Heap 메모리 영역(가비지 컬렉션이 동작하는 영역)에 생성. 한번 생성된 객체의 내부 내용을 변화시킬 수 없습니다. 기존 객체가 제거되면 Java의 가비지 컬렉션이 회수합니다.)



String 객체는 이러한 이유로 문자열 연산이 많은 경우, 그 성능이 좋지 않습니다.


하지만, 불변한 객체는 간단하게 사용가능하고, 동기화에 대해 신경쓰지 않아도 되기때문에(Thread-safe),  내부 데이터를 자유롭게 공유 가능합니다.

> # StringBuffer와 StringBuilder



StringBuffer/StringBuilder는 String과 다르게 동작합니다.

문자열 연산 등으로 기존 객체의 공간이 부족하게 되는 경우,


기존의 버퍼 크기를 늘리며 유연하게 동작합니다. StringBuffer와 StringBuilder 클래스가 제공하는 메서드는 서로 동일합니다.



**두 클래스의 차이점은? 동기화 여부입니다.**

- StringBuffer는 각 메서드별로 Synchronized Keyword가 존재하여, 멀티스레드 환경에서도 동기화를 지원.
- 반면, StringBuilder는 동기화를 보장하지 않음.



그렇기때문에 멀티스레드 환경이라면 값 동기화 보장을 위해 StringBuffer를 사용하고,


단일스레드 환경이라면 StringBuilder를 사용하는 것이 좋습니다. 단일 스레드환경에서 StringBuffer를 사용한다고 문제가 되는 것은 아니지만, 동기화 관련 처리로 인해 StringBuilder에 비해 성능이 좋지 않습니다.



<span style='background-color: red'> String은 짧은 문자열을 더할 경우 사용합니다. </span>

<span style='background-color: red'> StringBuffer는 스레드에 안전한 프로그램이 필요할 때나, 개발 중인 시스템의 부분이 스레드에 안전한지 모를 경우 사용하면 좋습니다. </span>


<span style='background-color: red'> StringBuilder는 스레드에 안전한지 여부가 전혀 관계 없는 프로그램을 개발할 때 사용하면 좋습니다. </span>




JDK 1.5버전 이전에서는 문자열연산(+, concat)을 할때에는 조합된 문자열을 새로운 메모리에 할당하여 참조함으로 인해서 성능상의 이슈가 있었습니다. 그러나 JDK1.5 버전 이후에는 컴파일 단계에서 String 객체를 사용하더라도 StringBuilder로 컴파일 되도록 변경되었습니다. 그리하여 JDK 1.5 이후 버전에서는 String 클래스를 활용해도 StringBuilder와 성능상으로 차이가 없어졌습니다. <span style='background-color: blue'> 하지만 반복 루프를 사용해서 문자열을 더할 때에는 객체를 계속 추가한다는 사실에는 변함이 없습니다.</span> 그러므로 String 클래스를 쓰는 대신, 스레드와 관련이 있으면 StringBuffer를, 스레드 안전 여부와 상관이 없으면 StringBuilder를 사용하는 것을 권장합니다.



단순히 성능만 놓고 본다면 연산이 많은 경우, <span style='background-color: blue'>StringBuilder > StringBuffer >>> String</span> 입니다.




  
