## JAVA 백엔드 다섯번째 시간 22-04 -11

- static,상속,오버라이딩,final,객체의 타입 변환
    - **static**
        - 어떤 객체던지 동일한 값을 사용할때 항상 값이 변하지 않는 경우에 static 을 사용하면 메모리의 이점을 얻을 수 있다.
        - 공유의 개념이다. static으로 설정을 하면 같은 곳의 메모리 주소만 바라보기 때문에 static 변수의 값을 공유하게 되는것이다.
        - **static 변수**
            
            ```java
            class Counter  {
                static int count = 0;
                Counter() {
                    count++;  // count는 더이상 객체변수가 아니므로 this를 제거하는 것이 좋다.
                    System.out.println(count);  // this 제거
                }
            }
            
            public class Sample {
                public static void main(String[] args) {
                    Counter c1 = new Counter();
                    Counter c2 = new Counter();
            				//출력 : 1 , 2 
            								 
                }
            }
            ```
            
            - 보통 변수의 static 키워드는 프로그래밍시 메모리의 효율보다는 공유의 목적으로 훨씬 더 많이 사용한다.
        - **static 메소드**
            
            ```java
            class Counter  {
                static int count = 0;
                Counter() {
                    count++;
                    System.out.println(count);
                }
            
                public static int getCount() {
                    return count;
                }
            }
            
            public class Sample {
                public static void main(String[] args) {
                    Counter c1 = new Counter();
                    Counter c2 = new Counter();
            
                    System.out.println(Counter.getCount());  // 스태틱 메서드는 클래스를 이용하여 호출
                }
            }
            ```
            
    - **상속,상속 접근제한,상속 생성자**
        - 자식 클래스가 부모 클래스의 기능을 그대로 물려받을 수 있는 상속 기능이 있다.
            
            ```java
            class Animal {
                String name;
            
                void setName(String name) {
                    this.name = name;
                }
            }
            
            class Dog extends Animal {
            }
            
            public class Sample {
                public static void main(String[] args) {
                    Dog dog = new Dog();
                    dog.setName("poppy");
                    System.out.println(dog.name);  // poppy 출력
                }
            }
            ```
            
        - 클래스 상속을 위해서는 extends 라는 키워드를 사용한다.
        - **IS-A 관계**
            
            Dog 클래스는 Animal 클래스를 상속했다. 즉, Dog는 Animal의 하위 개념이라고 할 수 있다. 이런 경우 Dog는 Animal에 포함되기 때문에 "개는 동물이다"라고 표현할 수 있다.
            
            자바는 이러한 관계를 `IS-A` 관계라고 표현한다. 즉 "Dog `is a` Animal" 과 같이 말할 수 있는 관계를 IS-A 관계라고 한다. 이렇게 IS-A 관계(상속관계)에 있을 때 자식 클래스의 객체는 부모 클래스의 자료형인 것처럼 사용할 수 있다.
            
            즉, 다음과 같은 코딩이 가능하다.
            
            ```java
            Animal dog =new Dog();  // Dog is a Animal
            
            ```
            
            > ※ 다만 여기서 한 가지 주의해야 할 점이 있다. Dog객체를 Animal 자료형으로 사용할 경우에는 Dog 클래스에만 존재하는 sleep 메소드를 사용할 수 없다는 점이다. 이런 경우에는 Animal 클래스에 구현된 setName 메소드만 사용이 가능하다.
            > 
    - **오버라이딩**
        - 부모의 메소드를 자식이 물려받은 후 재정의 하는 작업을 의미한다.
        - super는 부모를 가리키는 키워드 이다.
    - **final**
        - 최종적이란 뜻을 가지고 있습니다. final 필드는 초기값이 저장되면 최종적인 값이 되어 프로그램 실행 도중 수정을 할 수 없습니다.
            
            ```java
            final int number = 1;
            ```
            
    - **객체의 타입변환**
        - **묵시적 형변환**
            - 형변환 연산자를 사용하지 않아도 자동으로 이루어지는 경우 = 자동 형변환
            - ex) 4btye의 int형 데이터를 8byte double 형으로 변환
        - **명시적 형변환**
            - 더 작은 범위를 나타내는 데이터 타입으로 변환되는 경우 = 축소 형변환
            - ex) 8byte의 double형 데이터를 4byte int 형으로 변환
            
        - **객체 형변환**
            - 객체 참조변수의 경우에도 형변환이 이루어짐
            - 객체 참조변수들 간의 대입 규칙  [ 부모클래스(leftObjRef) = 자식클래스(rightObjRef) ]
                - 왼쪽 항과 오른쪽 항의 객체 유형이 서로 다른 경우 두 유형이 서로 상속 관계에 있음
                - 왼쪽 객체가 오른쪽 객체의 상위 클래스인 경우에만 묵시적 형변환 발생
                - 자식 클래스에서 부모 클래스 유형으로 할당하는 것은 가능하지만, 반대의 경우 명시적 형변환을 사용해야 함 단, 할당되는 인스턴스 유형에 따라 실행 오류 발생
            
            -> 내부 특정 클래스 형이 다른 클래스 형으로 변환될 수 있는지 여부를 수시로 판단해야 함
            
            -> instanceof 연산자를 활용 (생성된 객체가 class와 관계있는  type으로 만들어졌는지 확인)
