---
title: "class,instance,method"
last_modified_at: 2022-08-22T14:34:36-05:00
categories: 
    Java
---

## 클래스, 인스턴스, 메소드

- 1) 클래스(Class)란?
    - **클래스**는 표현하고자 하는 대상의 공통 속성을 한 군데에 정의해 놓은 것이라고 할 수 있다. 즉, 클래스는 객체의 속성을 정의해 놓은것
    - 또한 클래스 내부의 정보를 **멤버 변수**라라고 한다

![](https://velog.velcdn.com/cloudflare/funnykyeon/490e2662-271d-4cd6-94de-8be964fe56e3/image.png)

   - 여기 붕어빵 틀이 있다! 붕어빵 틀은 붕어빵을 만드는데 이용이 됨. 클래스랑 인스턴스도 이와 마찬가지로 생각하면 된다. 붕어빵을 만드는 틀이 곧 **클래스**가 되며 붕어빵 틀로부터 만들어진 붕어빵이 곧 **인스턴스**가 되는 것!

- **인스턴스(Instance)**란?
   - 어떠한 클래스로부터 만들어진 객체를 그 클래스의 **인스턴스**라고 한다.
                      
- **인스턴스 - Phone, Main 클래스**  

  ```java
  class Phone {
      String model;
      String color;
      int price;
  }

  public class Main {
      public static void main(String[] args) {
          Phone galaxy = new Phone(); 
          galaxy.model = "Galaxy10";
          galaxy.color = "Black";
          galaxy.price = 100;
          iphone.model = "iPhoneX";
          iphone.color = "Black";
          iphone.price = 200;


          System.out.println("철수는 이번에 " + galaxy.model + galaxy.color + " + 색상을 " + galaxy.price + "만원에 샀다.");
          System.out.println("영희는 이번에 " + iphone.model + iphone.color + " + 색상을 " + iphone.price + "만원에 샀다.");
      }
  }
  ```    
- Phone라는 클래스에는 핸드폰의 모델, 색깔, 가격에 대한 정보가 담겨져 있다. 이를 활용하여 model, color, price라는 같은 속성을 가진 galaxy, iphone으로 각기 다른 인스턴스를 만들었다.
<aside>
👉 인스턴스의 멤버변수에 접근할 때는 `[생성된 인스턴스.멤버변수]` 의 형식을 사용하면 된다.
</aside>
        


- 2) 메소드(method)
    - 자! 생성자를 설명하기 이전에 메소드에 대해서 이야기하도록 하겠다. **메소드**는 어떠한 **작업을 수행하는 코드를 하나로 묶어 놓은 것**이라고 생각하면 된다.
    - 메소드가 필요한 이유
        1. 재사용성
        - 메소드를 만들어 놓으면 이후 반복적으로 재사용이 가능하다. 물론, 다른 프로그램에서도 사용이 가능하다.
        2. 중복된 코드 제거
        - 프로그램을 작성하다보면 같은 코드가 여러번 반복되어 작성되곤 한다. 이럴 때, 메소드를 활용하면 중복된 부분을 없애므로 보다 효율적인 코드가 된다.
        3. 프로그램 구조화
        - 구조화에 대해서는 아래 예시를 보면서 이해를 할 수 있다.
        
        ```java
        int[] heights = new int[5]; // 키가 들어가 있는 배열
        
        initHeight(heights); // 1. 키에 대한 초기화
        sortHeight(heights); // 2. 키를 오름차순으로 정렬
        printHeight(heights); // 3. 정렬된 키를 출력
        ```
        
        - 보다시피 코드가 어떠한 작업을 하느냐에 따라 구분이 되어 구조화가 된 것을 확인할 수 있다. 엄청나게 긴 코드를 작성할 때 이러한 방식을 통해 보다 쉽게 수정 및 관리를 할 수 있다.
        - 메소드를 만들 때는 메소드 안에서 동작하는 내용을 잘 표현할 수 있도록 이름을 잘 지어주면, 메소드 안을 들여다 보지 않고도 한 눈에 코드를 읽어내려갈 수 있어서 좋다. 이것을 readability가 좋다고 표현한다. 이 readability의 기본 품질을 위해서 Java로 메소드를 만들 때 지켜줘야 하는 기본 약속은 다음 두 가지가 있다.
            1. 동사로 시작해야한다.
            2. [camel case](https://en.wikipedia.org/wiki/Camel_case)로 작성해야한다. (첫 단어는 소문자로, 이후 단어의 구분에 따라서 첫 글자만 대문자인 단어가 이어집니다. 중간에 띄어쓰기나 특수문자는 들어가지 않는다.)
        
    - 메소드 선언과 구현
        - 메소드의 역할과 필요한 이유를 알게되었다면, 어떻게 구현을 하는지 알아야한다.
        - 메소드는 다음의 형식으로 정의할 수 있습니다.
        
        ```
        반환타입 메소드이름 (타입 변수명,타입 변수명, ...){ 
            수행되어야 할 코드
        }
        ```
        
        - 메소드이름은 이름일것이며 수행되어야 할 코드는 수행코드이지만 반환타입이 무엇이지?라는 생각을 할수 있다. 메소드는 **return문**을 통해 수행의 결과를 반환하게 된다. 이때, 결과의 자료형을 결정하는 부분이 **반환 타입**이다.
        
        ```java
        int add(int x, int y) {
            int result = x + y;
            return result;
        }
        ```
        
        - 메소드의 반환타입은 int이며 이는 반환되어지는 변수인 result와 일치하여야 한다.
        
        <aside>
        👉 반환타입중 void는 '아무 것도 없음'을 의미한다. 예시로, 메소드내에서 출력을 할 경우 사용할 수 있다.
        
        </aside>
            ```
            
        
        [**CalScoreTest.java]**
        
        ```java
        class Calculation {
            int add(int x, int y) {
                int result = x + y;
                return result;
            }// 두 값을 더한 결과
        
            int subtract(int x, int y) {
                int result = x - y;
                return result;
            }// 두 값을 뺀 결과 
        }
        
        public class Main {
            public static void main(String[] args) {
                Calculation calculation = new Calculation();
                int addResult = calculation.add(100, 90);
                int subResult = calculation.subtract(90, 70);
        
                System.out.println("두 개를 더한 값은 " + addResult);
                System.out.println("두 개를 뺀 값은 " + subResult);
            }
        }
        ```
        
<aside>
        
👉 add 메소드와 subtract 메소드 모두 x와 y변수가 중복되어 사용된 것을 확인할 수 있다. 하지만, 메소드내의 변수는 **지역변수** 로써 메소드 내부에서만 사용할 수 있는 변수이다. 즉, 서로 다른 메소드라면 같은 이름의 **지역변수**를 선언하여 사용해도 된다.
        
</aside>
