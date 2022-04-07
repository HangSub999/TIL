## JAVA 백엔드 세,네번째 시간 22-04-06,07

- 객체,클래스,인스턴스,접근제어,메소드,get,set메소드,오버로딩,생성자
    - **객체**
        - 객체는 세상에 존재하는 모든 것들을 말한다.
        - 객체지향 프로그래밍(OOP)란?
            - 객제를 정의 및 기능을 구현하고 객체 간의 협력을 구현한다.
            유지보수가 편리하다는 장점이 있다.
    - **클래스**
        - 객체를 코드로 구현한 것이다. 설계도 라고 생각하면 이해가 쉽다.
        - **맴버 변수**
            - 객체가 가지는속성을 변수로 표현한 것이다.
                
                ```java
                public int studentID; //학번
                public String studentName;  //학생 이름
                public String address; // 주소
                ```
                
    - **인스턴스**
        - 설계도를 바탕으로 소프트웨어 세계에 구현된 구체적인 실체 즉, 객체를 소프트웨어에 실체화 하면 그것을 ‘인스턴스’ 라고 부른다. 실체화된 인스턴스는 메모리에 할당 된다.
    - **접근제어**
        - 접근제어자를 사용하여 변수나 메소드의 사용 권한을 설정할 수 있다.
        자주 사용되는 것은 **private 과 public 이다.**
        - **private**
            - 접근제어자가 private으로 설정되었다면 변수,메소드는 해당 클래스에서만 접근이 가능하다.
        - **default**
            - 접근 제어자를 별도로 설정하지 않으면 접근 제어자가 없는 변수,메소드는 default 접근 제어자가 되어 해당 패키지 내에서만 접근이 가능하다.
        - **protected**
            - 동일 패키지의 클래스 또는 해당 클래스를 상속받은 다른 패키지의 클래스에서만 접근이 가능하다.
        - **public**
            - 어떤 클래스라도 접근이 가능하다.
    - **메소드**
        - 매개변수(parameter) 는 메소드에 입렵으로 전달된 값을 받는 변수를 의미
        - 인수(arguments)는 메소드를 호출할때 전달하는 입력값을 의미한다.
        - returm값이 없는 메소드
            
            ```java
            public class Sample {
                void sum(int a, int b) {
                    System.out.println(a+"과 "+b+"의 합은 "+(a+b)+"입니다.");
                }
            
                public static void main(String[] args) {
                    Sample sample = new Sample();
                    sample.sum(3, 4);
                }
            }
            ```
            
            - System.out.println 문은 메소드 내에서 사용되어지는 문장일뿐이다. 돌려주는 값은 당연히 없다. 돌려주는 값은 return 명령어로만 가능하다.
        - return 문만을 써서 메소드를 빠져나가는 이 방법은 리턴자료형이 void 인 메소드만 해당 된다.
        - 객체를 메소드의 입력으로 넘기고 메소드가 객체의 속성값(객체변수 값)을 변경한다면 메소드 수행 이후에도 객체는 변경된 속성값을 유지한다. 이러한 차이가 나는 이유는 메소드에 전달하는 입력 자료형의 형태 때문인데 메소드에 값을 전달하느냐 아니면 객체를 전달하느냐에 따라 차이가 난다.
    - **Getter,Setter 메소드**
        - **Setter**
            - 객체 지향 프로그래밍에서는 메소드를 통해 데이터를 변경하는 방법을 선호한다.
            데이터는 외부에서 접근하지 않도록 막고,메소드는 공개해서 외부에서 메소드를 통해 데이터에 접근하도록 유도한다.
                - 이유: 메소드는 매개값을 검증해서 유효한 값만 데이터로 저장할 수 있기 때문이다.
            - 
            
            ```java
            void setSpeed(double speed) {   //Setter
                if(speed < 0) {
                    this.speed = 0;     // 매개값이 음수라면, 필드에 0으로 저장하고 메소드 실행 종료
                    return;
                } else {
                    this.speed = speed;
                }
            }
            ```
            
        - **Getter**
            - **외부에서 객체의 데이터를 읽을 때도 메소드를 사용**하는 것이 좋다.
                
                객체 외부에서 객체 필드값을 사용하기 부적절한 경우가 있다.
                
                이런 경우 메소드로 필드값을 가공 후, 외부로 전달한다.
                
            
            ```java
            double getSpeed() {
                double km = speed * 1.6;  // 필드 값인 마일(speed)를 km 단위로 환산 후 외부로 리턴
                return km;
            }
            ```
            
            - 클래스를 선언할 때 가능하다면 필드를 private 로 선언해서 외부로부터 보호하고필드에 대한 Setter / Getter 메소드를 작성해서 필드값을 안전하게 변경 / 사용하는 것이 좋다.
    - **메소드 오버로딩**
        - 이미 sleep이라는 메소드가 있지만 동일한 이름의 sleep메소드를 또 생성할 수 있다. 단, 메소드의 입력항목이 다를 경우만 가능하다. 새로 만든 sleep메소드는 입력항목으로 hour라는 int 자료형이 추가되었다.
            
            이렇듯 입력항목이 다른 경우 동일한 이름의 메소드를 만들 수 있는데 이를 **메소드 오버로딩(method overloading)**이라고 부른다.
            
            ```java
            class Animal {
                String name;
            
                void setName(String name) {
                    this.name = name;
                }
            }
            
            class Dog extends Animal {
                void sleep() {
                    System.out.println(this.name + " zzz");
                }
            }
            
            class HouseDog extends Dog {
                void sleep() {
                    System.out.println(this.name + " zzz in house");
                }
            
                void sleep(int hour) {
                    System.out.println(this.name + " zzz in house for " + hour + " hours");
                }
            }
            
            public class Sample {
                public static void main(String[] args) {
                    HouseDog houseDog = new HouseDog();
                    houseDog.setName("happy");
                    houseDog.sleep();  // happy zzz in house 출력
                    houseDog.sleep(3);  // happy zzz in house for 3 hours 출력
                }
            }
            ```
            
    - **생성자**
        - 생성자의 규칙
            1. 클래스명과 메소드명이 동일하다.
            2. 리턴타입을 정의하지 않는다.
            3. 생성자는 객체가 생성될 때 호출된다.
        - **기본 생성자**
            - 생성자의 입력 항목이 없고 생성자 내부에 아무 내용이 없는 위와 같은 생성자를 디폴트 생성자라고 부른다.
            - 만약 클래스에 생성자가 하나도 없다면 컴파일러는 자동으로 위와같은 디폴트 생성자를 추가한다. 하지만 사용자가 작성한 생성자가 하나라도 구현되어 있다면 컴파일러는 디폴트 생성자를 추가하지 않는다.
        - **생성자 오버로딩**
            - 하나의 클래스에 여러개의 입력항목이 다른 생성자를 만들 수 있다.
            - 입력 항목이 다른 생성자를 여러 개 만들 수 있는데 이런 것을 **생성자 오버로딩(Overloading)**
             이라고 한다.
