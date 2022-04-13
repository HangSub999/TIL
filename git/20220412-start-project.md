## JAVA 백엔드 다섯번째 시간 22-04-12

- 다형성,추상 메서드,클래스,인터페이스,try catch,finally,throws
    - **다형성**
        - 하나의 객체가 여러 가지 타입을 가질 수 있는 것을 의미합니다. 부모클래스 타입의 참조 변수로 자식 클래스 타입의 인스턴스를 참조할 수 있도록 하여 구현하고 있습니다.
        - **참조 변수의 다형성**
            - 참조 변수가 사용할 수 있는 멤버의 개수가 실제 인스턴스의 맴버 개수보다 같거나 적어야 참조할 수 있다.
                
                ```java
                class Parent { ... }
                
                class Child extends Parent { ... }
                
                ...
                
                Parent pa = new Parent(); // 허용
                
                Child ch = new Child();   // 허용
                
                Parent pc = new Child();  // 허용
                
                Child cp = new Parent();  // 오류 발생.
                ```
                
        - **참조 변수의 타입 변환**
            1. 서로 상속 관계에 있는 클래스 사이에만 타입 변환을 할 수 있다.
            2. 자식 클래스 타입에서 부모 클래스 타입으로의 타입 변환은 생략할 수 있다.
            3. 마지만 부모 클래스 타입에서 자식 클래스 타입으로의 타입 변환은 반드시 명시해야 합니다.
                
                ```java
                class Parent { ... }
                
                class Child extends Parent { ... }
                
                class Brother extends Parent { ... }
                
                ...
                
                Parent pa01 = null;
                
                Child ch = new Child();
                
                Parent pa02 = new Parent();
                
                Brother br = null;
                
                 
                
                pa01 = ch;          // pa01 = (Parent)ch; 와 같으며, 타입 변환을 생략할 수 있음.
                
                br = (Brother)pa02; // 타입 변환을 생략할 수 없음.
                
                br = (Brother)ch;   // 직접적인 상속 관계가 아니므로, 오류 발생.
                ```
                
        - **instanceof 연산자**
            - 참조 변수가 참조하고 있는 인스턴스의 실제 타입을 확인할때 사용한다.
                
                ```java
                class Parent { }
                
                class Child extends Parent { }
                
                class Brother extends Parent { }
                
                 
                
                public class Polymorphism01 {
                
                    public static void main(String[] args) {
                
                        Parent p = new Parent();
                
                        System.out.println(p instanceof Object); // true
                
                        System.out.println(p instanceof Parent); // true
                
                        System.out.println(p instanceof Child);  // false
                
                        System.out.println();
                
                 
                
                        Parent c = new Child();
                
                        System.out.println(c instanceof Object); // true
                
                        System.out.println(c instanceof Parent); // true
                
                        System.out.println(c instanceof Child);  // true
                
                    }
                
                }
                ```
                
    - **추상메서드, 클래스**
        - 자식 클래스에서 반드시 오버라이딩해야만 사용할 수 있는 메소드를 의미합니다.
        - 자바에서 추상 메소드를 선언하여 사용하는 목적은 추상 메소드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메소드를 구현하도록 하기 위함입니다.
        - 이러한 추상 메소드는 선언부만이 존재하며, 구현부는 작성되어 있지 않습니다.바로 이 작성되어 있지 않은 구현부를 자식 클래스에서 오버라이딩하여 사용하는 것입니다.
        - 문법
        
        ```java
        abstract 반환타입 메소드이름();
        ```
        
    - **인터페이스**
        - **인터페이스란?**
            - 자바는 클래스를 통한 다중 상속을 지원하지 않는다.하지만 다중 상속의 이점을 버릴 수는 없기에 자바에서는 인터페이스 라는것을 통해 다중 상속을 지원하고 있습니다.
            - 인터페이스란 다른 클래스를 작성할때 기본이 되는 틀을 제공하면서,다른 클래스 사이의 중간 매개 역할까지 담당하는 일종의 추상 클래스를 의미합니다.
            - 인터페이스는 오로지 추상 메소드와 상수만을 포함할 수 있습니다.
        - **인터페이스의 선언**
            
            ```java
            접근제어자 interface 인터페이스이름 {
            
                public static final 타입 상수이름 = 값;
            
                ...
            
                public abstract 메소드이름(매개변수목록);
            
                ...
            
            }
            ```
            
            - 단, 클래스와는 달리 인터페이스의 모든 필드는 public static final이어야 하며, 모든 메소드는 public abstract이어야 합니다.이 부분은 모든 인터페이스에 공통으로 적용되는 부분이므로 이 제어자는 생략할 수 있습니다.이렇게 생략된 제어자는 컴파일 시 자바 컴파일러가 자동으로 추가해 줍니다.
        - **인터페이스의 구현**
            - 인터페이스는 추상 클래스와 마찬가지로 자신이 직접 인스턴스를 생성할 수는 없습니다. 따라서 인터페이스가 포함하고 있는 추상 메소드를 구현해 줄 클래스를 작성 해야만 합니다.
            - 인터페이스를 사용한 다중 상속
            
            ```java
            interface Animal { public abstract void cry(); }
            
            interface Pet { public abstract void play(); }
            
             
            
            class Cat implements Animal, Pet {
            
                public void cry() {
            
                    System.out.println("냐옹냐옹!");
            
                }
            
                public void play() {
            
                    System.out.println("쥐 잡기 놀이하자~!");
            
                }
            
            }
            
             
            
            class Dog implements Animal, Pet {
            
                public void cry() {
            
                    System.out.println("멍멍!");
            
                }
            
                public void play() {
            
                    System.out.println("산책가자~!");
            
                }
            
            }
            
             
            
            public class Polymorphism04 {
            
                public static void main(String[] args) {
            
                    Cat c = new Cat();
            
                    Dog d = new Dog();
            
             
            
                    c.cry();
            
                    c.play();
            
                    d.cry();
            
                    d.play();
            
                }
            
            }
            ```
            
        - **인터페이스의 장점**
            
            1. 대규모 프로젝트 개발 시 일관되고 정형화된 개발을 위한 표준화가 가능합니다.
            
            2. 클래스의 작성과 인터페이스의 구현을 동시에 진행할 수 있으므로, 개발 시간을 단축할 수 있습니다.
            
            3. 클래스와 클래스 간의 관계를 인터페이스로 연결하면, 클래스마다 독립적인 프로그래밍이 가능합니다.
            
    - **try catch finally**
        - 자바에서는 프로그램이 실행되는 도중 발생하는 예외를 처리하기 위해 try/catch/finally 문을 사용할 수 있습니다.
        - 문법
        
        ```java
        try {
        
            예외를 처리하길 원하는 실행 코드;
        
        } catch (e1) {
        
            e1 예외가 발생할 경우에 실행될 코드;
        
        } catch (e2) {
        
            e2 예외가 발생할 경우에 실행될 코드;
        
        }
        
        ...
        
        finally {
        
            예외 발생 여부와 상관없이 무조건 실행될 코드;
        
        }
        ```
        
        1. try 블록 : 기본적으로 맨 먼저 실행되는 코드로 여기에서 발생한 예외는 catch 블록에서 처리됩니다.
        2. catch 블록 : try 블록에서 발생한 예외 코드나 예외 객체를 인수로 전달받아 그 처리를 담당합니다.
        3. finally 블록 : 이 블록은 try 블록에서 예외가 발생하건 안 하건 맨 마지막에 무조건 실행됩니다.
    - **throw**
        - 예외를 강제로 발생시키는것,코드를 작성하는 프로그래머가 강제로 예외를 발생시키는 것입니다.
        - throw new 발생시킬 예외;
        
        ```java
        package test;
         
        public class java30 {
         
            public static void main(String[] args) {
                
                try {
                    throw new Exception(); // 강제로 Exception 객체를 생성하였습니다.
                } catch (Exception e) {
                    System.out.println("예외를 강제로 발생했습니다.");
                }
                
            }
            
        }
        ```
        
    - **throws**
        - 예외를 처리하는것은 동일하나 예외를 상위쪽으로 미루어 처리를 하는것 입니다.
        - throws를 사용하여 호출한쪽에서 처리를 하고 throws 구문에 발생할만한 예외를 적어 인계자에게도 시간낭비를 줄여줄 수 있다.
        - 만들어진 메소드 throws 발생할 예외{}
        
        ```java
        public class java30 {
         
            public static void main(String[] args) {
                
                Test test = new Test();
                
                try {
                    test.test("1", "ㄱ"); // 숫자를 넘겨주어야 하지만 숫자와 문자를 넘겨준다.
                } catch (NumberFormatException e) {
                    System.out.println("입력하신 값은 숫자가 아닙니다..."); //NumberFormatException 발생시 실행시킴
                }    
            }
            
        }
         
        class Test {
            
            public void test(String a, String b) throws NumberFormatException{
                int sum = Integer.parseInt(a) + Integer.parseInt(b); // 문자로 받은 a와 b의 문자를 숫자로 변환하여 더한다. (하지만 문자를 받을시 형변환과정에서 NumberFormatException 이 발생한다.)
                System.out.println("문자로 입력받은 " +a+ "," +b+ "의 합은 " + sum + "입니다."); // 문자로 받은 숫자 2개의 합을 출력한다.
            }
            
        }
        ```
