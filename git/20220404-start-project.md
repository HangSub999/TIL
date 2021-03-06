## JAVA 백엔드 첫 시간

- JDK(Java Development Kit)
    - 자바 가상머신(JVM), 자바 런타임 환경(JRE)과 함께 자바 프로그래밍에 사용되는 3대 핵심 기술 패기지 가운데 하나이다.
    - 자바 프로그램을 생성할 수 있게 해준다.
    - 자바 기반 소프트 웨어를 개발하기 위한 도구
- JRE(Java Runtime Environment)
    - 자바 코드를 실행하기 위한 도구들로 구성된 패키지 이다.
- BIN 폴더에는 java 명령어들이 들어있다.
- 톰캣이란? 웹 서버에서 요청을 받으려면 필요한 도구
- h2란? db관리도구중 하나이다
- java 특징
    - 유지보수가 편하다.
    - 다형성 = 상속 + 오버라이딩 + 형변환
- 변수
    - 데이터를 저장할 수 있는 메모리 공간을 의미
    - 저장된 값은 변경될 수 있다.
- 변수의 선언과 규칙
    - 변수의 선언
        - 변수의 선언과 동시에 초기화 하는 방법
        
        ```java
        int num = 3;
        ```
        
    - 변수의 규칙
        - 하나 이상의 글자로 이루어저야 함
        - 첫 번째 글자는 문자 이거나 ‘$’,’_’이어야 함
        - 두번째 이후의 글자는 숫자, 문자, ‘$’, ‘_’ 이어야 함
        - '$', '_' 이외의 특수문자 사용 불가능
        - 길이 제한 없음
        - 예약어(키워드) 는 식별자로 사용할 수 없음
- 변수와 데이터 타입
    - 논리형  — Boolean
        - true와 false중 하나를 값으로 갖으며 조건식과 논리적 계산에 사용
    - 문자형 —- char
        - 문자를 정하는데 사용됨, 변수에 하나의 문자만 저장 가능
    - 정수형 —- short,byte,int,long
        - 정수를 저장하는데 사용되며 주로 int가 사용됨
    - 실수형 —- float, double
        - 실수를 저장하는데 사용, 주로 double 이 사용됨
- 변수 초기화
    - 초기화를 할때는 변수를 선언 하고 바로 뒤에 ‘=’ 대입 연산자를 사용해서 변수에 데이터를 집어 넣었다.
    - 명시적 초기화
    
    ```java
    int num = 999;
    /* 선언 후 바로 값을 집어넣는 것을 명시적 
    초기화 라고 한다.*/
    ```
    
- 연산자
    - 산술 연산자
        - +, -, %, /
    - 증감 연산자
        - ++,—
    - 비교 연산자
        - <=,>=,>,<,==
    - 논리 연산자
        - !,&&,||
    - 대입 연산자
        - =
    - 조건 연산자
        - a? b:c
