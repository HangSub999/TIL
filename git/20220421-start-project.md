## JAVA  4주차

- **java의 패키지들**
    - **java.lang 패키지**
        - JAVA 프로그래밍에 필요한 가장 기본적인 클래스들이 모여있는 패키지이다. import구문으로 호출해야 사용할 수 있는 다른 패키지들과는 달리 lang패키지는 import구문 없이도 자동으로 프로그램에 포함된다.
            1. String클래스
            2. StringBuffer클래스와StringBuilder클래스
            3. Math클래스
            4. Wrapper클래스
        - hashCode()메소드
        - equals()메소드
    - **java.util 패키지**
        - **java.util.Random 클래스**
            - Random클래스는 난수를 생성하는 클래스로 객체를 생성하여 사용한다.

            ```java
            public class RandomTest{ public static void main(String[] args){ 
            Random random = new Random(); 
            System.out.println( random.nextInt() ); // 1,700,703,373 (-2,147,483,648 ~ 2,147,483,647 사이의 값) 
            System.out.println( random.nextInt(10) ); // 2.3279967568276427 (0 ~ 9 사이의 값) 
            System.out.println( random.nextInt(10) + 1 ); // 2 (1 ~ 10 사이의 값) 
            System.out.println( random.nextInt(10) * (-1) ); // -7 ( -9 ~ 0 사이의 값) 
            System.out.println( random.nextBoolean() ); // true (true or false) } }
            
            ```

            - Math 와 달리 Random  클래스만의 장점이라 볼수있는건 객체를 재활용하여 지속적으로 사용가능 하다는 점이다.
        - **java.util.Arrays 클래스**
            - Arrays 클래스는 항목 정렬,항목 검색, 항목 비교 와 같은 메소드들을 제공한다. 모든 메소드는 static(정적) 메소드 이므로 Arrays클래스로 바로 사용이 가능 하다.
        - **java.util.StrigTokenizer 클래스**
            - BufferedReader클래스의 메서드로 입력을 읽어들이면 라인 단위로 읽어들일 수 밖에 없다.
            - 컴마로 구분되는 문자열을 분리한다던가 특정 문자에 따라 문자열을 나누고 싶을때에 StrigTokenizer를 이용할 수 있다.

                ```java
                StringTokenizer st = new StringTokenizer(문자열);
                StringTokenizer st = new StringTokenizer(문자열,구분자);
                StringTokenizer st = new StringTokenizer(문자열,구분자,true,false);
                >>>구분자를 기준으로 문자열을 분리할때 구분자도 토큰으로 포함할지(true) 포함하지
                	않을지(false) 디폴트는 false
                ```

            - nextToken(String delim) - delim 기준으로 다음 토큰을 반환
            - hasMoreTokens() - 남아잇는 토큰이 있다면 true,없다면 false 리턴
            - countTokens() - 총 토큰의 개수를 리턴
        - **java.util.Date 와 java.util.Calendar 클래스**
            - 자바에서 시간과 날짜를 제공하는 Class는 크게 Date,Calendar,Time 총 3가지로 볼 수 있다.
              Date,Calendar는 java.util 패키지에 포함되어있던 아이들이고 LocalTime,LocalDate,LocalDateTime은 java.time패키지 안에 각각 존재한다.
            - 과거에 사용하던 Date,Calendar 클래스에 문제가 너무 많아서 사용이 지양되고 있고,
              새롭게 만들어진 java.time 패키지에 LocalTime,LocalDate,LocalDateTime 를 사용하는 추세이다.
        - **자바의 컬렉션**
            - 컬렉션이란?(Collection)
                - 집합을 의미하는데 자바의 컬렉션은 그 대상이 바로 객체이다. 즉 자바의 컬렉션이란 객체들을 모아놓고 제어,관리, 하기 위해 필요한 객체들을 모아놓은 객체들(클래스,인터페이스)을 의미한다.
            - 집합의 종류


                | 구분 | 형태 | 예시 | 컬렉션 객체 |
                | --- | --- | --- | --- |
                | 1 | 사물이 순서를 가지면서 일렬로 늘어선 모양 | 버스를 기다리는 승객의 대기 줄 | List |
                | 2 | 순서 없이 뭉쳐 있는 모양 | 과자 봉투 안의 내용물 | Set |
                | 3 | 사물을 넣고 뺄 수 있는 원통형
                - 한쪽이 막혀있는 경우 : LIFO
                - 한쪽이 막혀 있지 않은 경우: FIFO | LIFO- 밑이 막혀있는 상자
                FIFO- 일방통행 터널 | Queue |
                | 4 | 각각의 사물이 이름표를 달고 모여있는 집합 | Label이 붙은 상태로 진열된 상품 | Map |
            - **Collection 프레임웍의 구성**
                1. 인터페이스 : 컬렉션 객체에게 반드시 필요한 기능을 정의한 객체 즉 컬렉션 객체 다울 수 있는 메서드를 정의해 놓은 객체
                2. 클래스 : 인터페이스나 클래스를 상속받아 컬렉션으로서 갖추어야 할 기능을 실제적으로 구현한 객체
                3. 기타 도움 객체 : 순차적 접근 방법을 제공하는 등, 컬렉션 활용성을 높여주는 객체
                    
                    예)lterator,Enumeration
                    
            - **java.util.List 컬렉션 클래스**
                - 특징
                    1. 요소의 저장 순서가 유지됩니다.
                    2. 같은 요소의 중복 저장을 허용합니다.
                - 대표적인 List컬렉션 클래스에 속하는 클래스
                    - ArrayList<E> 클래스
                        - ArrayList 클래스는 배열을 이용하기 때문에 인덱스를 이용해 배열 요소에 빠르게 접근할 수 있습니다.하지만 배열은 크기를 변경할 수 없는 인스턴스이므로, 크기를 늘리기 위해서는 새로운 배열을 생성하고 기존의 요소들을 옮겨야 하는 복잡한 과정을 거쳐야 합니다.물론 이 과정은 자동으로 수행되지만, 요소의 추가 및 삭제 작업에 걸리는 시간이 매우 길어지는 단점을 가지게 됩니다.
                        - ArrayList메소드를 이용한 예제
                            
                            ```java
                            ArrayList<Integer> arrList = new ArrayList<Integer>();
                            
                             
                            
                            // add() 메소드를 이용한 요소의 저장
                            
                            arrList.add(40);
                            
                            arrList.add(20);
                            
                            arrList.add(30);
                            
                            arrList.add(10);
                            
                             
                            
                            // for 문과 get() 메소드를 이용한 요소의 출력
                            
                            for (int i = 0; i < arrList.size(); i++) {
                            
                                System.out.print(arrList.get(i) + " ");
                            
                            }
                            
                             
                            
                            // remove() 메소드를 이용한 요소의 제거
                            
                            arrList.remove(1);
                            
                             
                            
                            // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
                            
                            for (int e : arrList) {
                            
                                System.out.print(e + " ");
                            
                            }
                            
                             
                            
                            // Collections.sort() 메소드를 이용한 요소의 정렬
                            
                            Collections.sort(arrList);
                            
                             
                            
                            // iterator() 메소드와 get() 메소드를 이용한 요소의 출력
                            
                            Iterator<Integer> iter = arrList.iterator();
                            
                            while (iter.hasNext()) {
                            
                                System.out.print(iter.next() + " ");
                            
                            }
                            
                             
                            
                            // set() 메소드를 이용한 요소의 변경
                            
                            arrList.set(0, 20);
                            
                             
                            
                            for (int e : arrList) {
                            
                                System.out.print(e + " ");
                            
                            }
                            
                             
                            
                            // size() 메소드를 이용한 요소의 총 개수
                            
                            System.out.println("리스트의 크기 : " + arrList.size());
                            
                            //실행 결과
                            40 20 30 10 
                            
                            40 30 10
                            
                            10 30 40 
                            
                            20 30 40
                            
                            리스트의 크기 : 3
                            ```
                            
                    - LinkedList<E> 클래스
                        - LinkedList 클래스는 ArrayList 클래스가 배열을 이용하여 요소를 저장함으로써 발생하는 단점을 극복하기 위해 고안되었습니다.JDK 1.2부터 제공된 LinkedList 클래스는 내부적으로 연결 리스트(linked list)를 이용하여 요소를 저장합니다.배열은 저장된 요소가 순차적으로 저장됩니다.하지만 연결 리스트는 저장된 요소가 비순차적으로 분포되며, 이러한 요소들 사이를 링크(link)로 연결하여 구성합니다.다음 요소를 가리키는 참조만을 가지는 연결 리스트를 단일 연결 리스트(singly linked list)라고 합니다.
                        - 단일 연결 리스트
                            
                            ![스크린샷 2022-04-21 오후 9.54.18.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bda90bf9-4613-45a9-b1f0-ab29b50ba2f4/스크린샷_2022-04-21_오후_9.54.18.png)
                            
                            이러한 단일 연결 리스트는 요소의 저장과 삭제 작업이 다음 요소를 가리키는 참조만 변경하면 되므로, 아주 빠르게 처리 될 수 있습니다. 하지만 단일 연결 리스트는 현재 요소에서 이전 요소로 접근하기가 매우 어렵습니다. 따라서 이전 요소를 가리키는 참조도 가지는 이중 연결 리스트가 좀 더 많이 사용됩니다.
                            
                        - 이중 연결 리스트(doubly linked list)
                            
                            ![스크린샷 2022-04-21 오후 10.00.46.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be51dc34-428c-4b09-ba8c-30712537a0d8/스크린샷_2022-04-21_오후_10.00.46.png)
                            
                            LinkedList 클래스도 위와 같은 이중 연결 리스트를 내부적으로 구현한 것입니다.
                            
                            또한, LinkedList 클래스 역시 List 인터페이스를 구현하므로, ArrayList 클래스와 사용할 수 있는 메소드가 거의 같습니다.
                            
                        - LinkedList 메소드를 이용한 예제
                            
                            ```java
                            LinkedList<String> lnkList = new LinkedList<String>();
                            
                             
                            
                            // add() 메소드를 이용한 요소의 저장
                            
                            lnkList.add("넷");
                            
                            lnkList.add("둘");
                            
                            lnkList.add("셋");
                            
                            lnkList.add("하나");
                            
                             
                            
                            // for 문과 get() 메소드를 이용한 요소의 출력
                            
                            for (int i = 0; i < lnkList.size(); i++) {
                            
                                System.out.print(lnkList.get(i) + " ");
                            
                            }
                            
                             
                            
                            // remove() 메소드를 이용한 요소의 제거
                            
                            lnkList.remove(1);
                            
                             
                            
                            // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
                            
                            for (String e : lnkList) {
                            
                                System.out.print(e + " ");
                            
                            }
                            
                             
                            
                            // set() 메소드를 이용한 요소의 변경
                            
                            lnkList.set(2, "둘");
                            
                             
                            
                            for (String e : lnkList) {
                            
                                System.out.print(e + " ");
                            
                            }
                            
                             
                            
                            // size() 메소드를 이용한 요소의 총 개수
                            
                            System.out.println("리스트의 크기 : " + lnkList.size());
                            
                            //실행 결과
                            넷 둘 셋 하나
                            
                            넷 셋 하나
                            
                            넷 셋 둘
                            
                            리스트의 크기 : 3
                            ```
                            
                    - Vector<E> 클래스
                        - 현재에는 기존 코드와의 호환성을 위해서만 남아있으므로,Vector 클래스 보다는 ArrayList 클래스를 사용하는 것이 좋습니다.
                    - Stack<E> 클래스
                        - Stack 클래스는 List 컬렉션 클래스의 Vector 클래스를 상속받아, 전형적인 스택 메모리 구조의 클래스를 제공합니다.
                            
                            스택 메모리 구조는 선형 메모리 공간에 데이터를 저장하면서 후입선출(LIFO)의 시멘틱을 따르는 자료 구조입니다.
                            
                            즉, 가장 나중에 저장된(push) 데이터가 가장 먼저 인출(pop)되는 구조입니다.
                            
                        - Stack<Integer> st = new Stack<Integer>();
                            
                            ![스크린샷 2022-04-22 오전 12.07.00.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7f55af3-5b20-458d-9a73-bf7797c88ed6/스크린샷_2022-04-22_오전_12.07.00.png)
                            
                            - Stack 클래스는 스택 메모리 구조를 표현하기 위해,Vector 클래스의 메소드를 5개만 상속받아 사용합니다.
                                
                                ![스크린샷 2022-04-22 오전 12.08.38.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a1c0e56f-313e-482d-b877-15887a4c334b/스크린샷_2022-04-22_오전_12.08.38.png)
                                
                            - 더욱 복잡하고 빠른 스택을 구현하고 싶다면 Deque 인터페이스를 구현한 ArrayDeque 클래스를 사용하면 됩니다.
                                
                                ```java
                                Deque<Integer> st = new ArrayDeque<Integer>();
                                ```
                                
                            - Stack 메소드를 이용하여 스택 메모리 구조를 구현한 예제
                                
                                ```java
                                Stack<Integer> st = new Stack<Integer>(); // 스택의 생성
                                
                                //Deque<Integer> st = new ArrayDeque<Integer>();
                                
                                 
                                
                                // push() 메소드를 이용한 요소의 저장
                                
                                st.push(4);
                                
                                st.push(2);
                                
                                st.push(3);
                                
                                st.push(1);
                                
                                 
                                
                                // peek() 메소드를 이용한 요소의 반환
                                
                                System.out.println(st.peek());
                                
                                System.out.println(st);
                                
                                 
                                
                                // pop() 메소드를 이용한 요소의 반환 및 제거
                                
                                System.out.println(st.pop());
                                
                                System.out.println(st);
                                
                                 
                                
                                // search() 메소드를 이용한 요소의 위치 검색
                                
                                System.out.println(st.search(4));
                                
                                System.out.println(st.search(3));
                                
                                //실행 결과
                                1
                                [4, 2, 3, 1]
                                1
                                [4, 2, 3]
                                3
                                1
                                ```
                                
                                - ArrayDeque 클래스는 Stack 클래스와는 달리 search()메소드는 지원하지 않습니다.
                    - Queue<E> 인터페이스
                        - 클래스로 구현된 스택과는 달리 자바에서 큐 메모리 구조는 별도의 인터페이스 형태로 제공됩니다.
                            
                            이러한 Queue 인터페이스를 상속받는 하위 인터페이스는 다음과 같습니다.
                            
                            1. Deque<E>
                            2. BlockingDeque<E>
                            3. BlockingQueue<E>
                            4. TransferQueue<E>
                            
                            따라서 Queue 인터페이스를 직간접적으로 구현한 클래스는 상당히 많습니다.
                            
                            그중에서도 Deque 인터페이스를 구현한 LinkedList 클래스가 큐 메모리 구조를 구현하는 데 가장 많이 사용됩니다.
                            
                            큐 메모리 구조는 선형 메모리 공간에 데이터를 저장하면서 선입선출(FIFO)의 시멘틱을 따르는 자료 구조입니다.
                            
                            즉, 가장 먼저 저장된(push) 데이터가 가장 먼저 인출(pop)되는 구조입니다.
                            
                        - LinkedList<String>qu = new LinkedList<String>();
                            
                            ![스크린샷 2022-04-22 오전 12.25.14.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9c7ff8a1-aee2-41fe-9e34-d692a1129d82/스크린샷_2022-04-22_오전_12.25.14.png)
                            
                        - Queue 인터페이스는 큐 메모리 구조를 표현하기 위해, 다음과 같은 Collection 인터페이스 메소드만을 상속받아 사용합니다.
                            
                            ![스크린샷 2022-04-22 오전 12.27.31.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4fc92853-1ecf-42a1-9ffc-3ac9db1186c0/스크린샷_2022-04-22_오전_12.27.31.png)
                            
                        - 더욱 복잡하고 빠른 큐를 구현하고 싶다면 Deque 인터페이스를 구현한 ArrayDeque 클래스를 사용하면 됩니다.
                            
                            ```java
                            Deque<Integer> qu = new ArrayDeque<Integer>();
                            ```
                            
                        - LinkedList메소드를 이용하여 큐 메모리 구조를 구현한 예제입니다.
                            
                            ```java
                            LinkedList<String> qu = new LinkedList<String>(); // 큐의 생성
                            
                            //Deque<String> qu = new ArrayDeque<String>();
                            
                             
                            
                            // add() 메소드를 이용한 요소의 저장
                            
                            qu.add("넷");
                            
                            qu.add("둘");
                            
                            qu.add("셋");
                            
                            qu.add("하나");
                            
                             
                            
                            // peek() 메소드를 이용한 요소의 반환
                            
                            System.out.println(qu.peek());
                            
                            System.out.println(qu);
                            
                             
                            
                            // poll() 메소드를 이용한 요소의 반환 및 제거
                            
                            System.out.println(qu.poll());
                            
                            System.out.println(qu);
                            
                             
                            
                            // remove() 메소드를 이용한 요소의 제거
                            
                            qu.remove("하나");
                            
                            System.out.println(qu);
                            
                            //실행 결과
                            넷
                            [넷, 둘, 셋, 하나]
                            넷
                            [둘, 셋, 하나]
                            [둘, 셋]
                            ```
                            
            - **java.util.Set 컬렉션**
                - 특징
                    1. 요소의 저장 순서를 유지하지 않습니다.
                    2. 같은 요소의 중복저장을 허용하지 않습니다.
                - 대표적인 Set컬렉션 클래스에 속하는 클래스는 다음과 같습니다.
                    - HashSet<E>클래스
                        - HashSet 클래스는 Set 컬렉션 클래스에서 가장 많이 사용되는 클래스 중 하나입니다.JDK 1.2부터 제공된 HashSet 클래스는 해시 알고리즘(hash algorithm)을 사용하여 검색 속도가 매우 빠릅니다.이러한 HashSet 클래스는 내부적으로 HashMap 인스턴스를 이용하여 요소를 저장합니다.
                        HashSet 클래스는 Set 인터페이스를 구현하므로, 요소를 순서에 상관없이 저장하고 중복된 값은 저장하지 않습니다.만약 요소의 저장 순서를 유지해야 한다면 JDK 1.4부터 제공하는 LinkedHashSet 클래스를 사용하면 됩니다.
                        - HashSet 메소드를 이용하여 집합을 생성하고 조작하는 예제
                            
                            ```java
                            HashSet<String> hs01 = new HashSet<String>();
                            
                            HashSet<String> hs02 = new HashSet<String>();
                            
                             
                            
                            // add() 메소드를 이용한 요소의 저장
                            
                            hs01.add("홍길동");
                            
                            hs01.add("이순신");
                            
                            System.out.println(hs01.add("임꺽정"));
                            
                            System.out.println(hs01.add("임꺽정")); // 중복된 요소의 저장
                            
                             
                            
                            // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
                            
                            for (String e : hs01) {
                            
                                System.out.print(e + " ");
                            
                            }
                            
                             
                            
                            // add() 메소드를 이용한 요소의 저장
                            
                            hs02.add("임꺽정");
                            
                            hs02.add("홍길동");
                            
                            hs02.add("이순신");
                            
                             
                            
                            // iterator() 메소드를 이용한 요소의 출력
                            
                            Iterator<String> iter02 = hs02.iterator();
                            
                            while (iter02.hasNext()) {
                            
                                System.out.print(iter02.next() + " ");
                            
                            }
                            
                             
                            
                            // size() 메소드를 이용한 요소의 총 개수
                            
                            System.out.println("집합의 크기 : " + hs02.size());
                            
                            //실행 결과
                            true
                            false
                            홍길동 이순신 임꺽정
                            홍길동 이순신 임꺽정
                            집합의 크기 : 3
                            ```
                            
                        - HashSet에 이미 존재하는 요소인지를 파악하기 위한 내부적 과정
                            
                            1. 해당 요소에서 hashCode() 메소드를 호출하여 반환된 해시값으로 검색할 범위를 결정합니다.
                            
                            2. 해당 범위 내의 요소들을 equals() 메소드로 비교합니다.
                            
                            따라서 HashSet에서 add()메소드를 사용하여 중복없이 새로운 요소를 추가하기 위해서는 hashCode()와 equals()메소드를 상황에 맞게 오버라이딩 해야 합니다.
                            
                            - 사용자가 정의한 Animal 클래스의 인스턴스를 HashSet에 저장하기 위해 hashCode()와 equals() 메소드를 오버라이딩한 예제입니다.
                                
                                ```java
                                class Animal {
                                
                                    String species;
                                
                                    String habitat;
                                
                                 
                                
                                    Animal(String species, String habitat) {
                                
                                    this.species = species;
                                
                                    this.habitat = habitat;
                                
                                }
                                
                                 
                                
                                public int hashCode() { return (species + habitat).hashCode(); }
                                
                                    public boolean equals(Object obj) {
                                
                                        if(obj instanceof Animal) {
                                
                                            Animal temp = (Animal)obj;
                                
                                            return species.equals(temp.species) && habitat.equals(temp.habitat);
                                
                                        } else {
                                
                                            return false;
                                
                                        }
                                
                                    }
                                
                                }
                                
                                 
                                
                                public class Set02 {
                                
                                    public static void main(String[] args) {
                                
                                        HashSet<Animal> hs = new HashSet<Animal>();
                                
                                 
                                
                                        hs.add(new Animal("고양이", "육지"));
                                
                                        hs.add(new Animal("고양이", "육지"));
                                
                                        hs.add(new Animal("고양이", "육지"));
                                
                                 
                                
                                        System.out.println(hs.size());
                                
                                    }
                                
                                }
                                
                                //실행 결과
                                1
                                ```
                                
                                - add() 메소드를 통해 같은 값을 가지는 Animal 인스턴스를 여러 번 저장하지만, size() 메소드를 통해 살펴본 HashSet 요소의 총 개수는 1개만 저장되었음을 확인할 수 있습니다.
                        - 해시 알고리즘
                            - 해시 알고리즘(hash algorithm)이란 해시 함수(hash function)를 사용하여 데이터를 해시 테이블(hash table)에 저장하고, 다시 그것을 검색하는 알고리즘입니다.
                            
                            ![스크린샷 2022-04-22 오전 12.59.31.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6387e4df-35aa-4b96-a82d-27650ce25cba/스크린샷_2022-04-22_오전_12.59.31.png)
                            
                            - 자바에서 해시 알고리즘을 이용한 자료 구조는 위의 그림과 같이 배열과 연결 리스트로 구현됩니다.
                                
                                저장할 데이터의 키값을 해시 함수에 넣어 반환되는 값으로 배열의 인덱스를 구합니다.
                                
                                그리고서 해당 인덱스에 저장된 연결 리스트에 데이터를 저장하게 됩니다.
                                
                                예를 들어, 정수형 데이터를 길이가 10인 배열에 저장한다고 한다면 1,000,002를 검색하는 방법은 다음과 같을 수 있습니다.
                                
                                1,000,002를 10으로 나눈 나머지가 2이므로 배열의 세 번째 요소에 연결된 연결 리스트에서 검색을 시작합니다.
                                
                                매우 간략화한 예제이지만 이렇게 해시 알고리즘을 이용하면 매우 빠르게 검색 작업을 수행할 수 있습니다.
                                
                    - TreeSet<E> 클래스
                        - TreeSet 클래스는 데이터가 정렬된 상태로 저장되는 이진 검색 트리(binary search tree)의 형태로 요소를 저장합니다.
                            
                            이진 검색 트리는 데이터를 추가하거나 제거하는 등의 기본 동작 시간이 매우 빠릅니다.
                            
                            JDK 1.2부터 제공되는 TreeSet 클래스는 NavigableSet 인터페이스를 기존의 이진 검색 트리의 성능을 향상시킨 레드-블랙 트리(Red-Black tree)로 구현합니다.
                            
                            TreeSet 클래스는 Set 인터페이스를 구현하므로, 요소를 순서에 상관없이 저장하고 중복된 값은 저장하지 않습니다.
                            
                        - 여러 TreeSet메소드를 이용하여 집합을 생성하고 조작하는 예제입니다.
                            
                            ```java
                            TreeSet<Integer> ts = new TreeSet<Integer>();
                            
                             
                            
                            // add() 메소드를 이용한 요소의 저장
                            
                            ts.add(30);
                            
                            ts.add(40);
                            
                            ts.add(20);
                            
                            ts.add(10);
                            
                             
                            
                            // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
                            
                            for (int e : ts) {
                            
                                System.out.print(e + " ");
                            
                            }
                            
                             
                            
                            // remove() 메소드를 이용한 요소의 제거
                            
                            ts.remove(40);
                            
                             
                            
                            // iterator() 메소드를 이용한 요소의 출력
                            
                            Iterator<Integer> iter = ts.iterator();
                            
                            while (iter.hasNext()) {
                            
                                System.out.print(iter.next() + " ");
                            
                            }
                            
                             
                            
                            // size() 메소드를 이용한 요소의 총 개수
                            
                            System.out.println("이진 검색 트리의 크기 : " + ts.size());
                            
                             
                            
                            // subSet() 메소드를 이용한 부분 집합의 출력
                            
                            ① System.out.println(ts.subSet(10, 20));
                            
                            ② System.out.println(ts.subSet(10, true, 20, true));
                            //실행 결과
                            10 20 30 40 
                            10 20 30 
                            이진 검색 트리의 크기 : 3
                            [10]
                            [10, 20]
                            ```
                            
                            - 위의 예제처럼 TreeSet 인스턴스에 저장되는 요소들은 모두 정렬된 상태로 저장됩니다.
                                
                                또한, 위의 예제에서 사용된 subSet() 메소드는 TreeSet 인스턴스에 저장되는 요소가 모두 정렬된 상태이기에 동작이 가능한 해당 트리의 부분 집합만을 보여주는 메소드입니다.
                                
                            - ①번 라인에서 사용된 subSet() 메소드는 첫 번째 매개변수로 전달된 값에 해당하는 요소부터 시작하여 두 번째 매개변수로 전달된 값에 해당하는 요소의 바로 직전 요소까지를 반환합니다.
                                
                                ②번 라인에서 사용된 subSet() 메소드는 두 번째와 네 번째 매개변수로 각각 첫 번째와 세 번째 매개변수로 전달된 값에 해당하는 요소를 포함할 것인지 아닌지를 명시할 수 있습니다.
                                
                                즉, ②번 라인에서 네 번째 매개변수를 false로 변경하면 20을 포함하지 않게 되므로, ①번 라인과 같은 결과를 출력할 것입니다.
                                
                        - Set 인터페이스 메소드
                            - Set 인터페이스는 Collection 인터페이스를 상속받으므로, Collection 인터페이스에서 정의한 메소드도 모두 사용할 수 있습니다.
                                - Set 인터페이스에서 제공하는 주요 메소드는 다음과 같습니다.
                                    
                                    ![스크린샷 2022-04-22 오전 1.11.11.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8c1a074f-1374-4a9e-9184-8253d822a18a/스크린샷_2022-04-22_오전_1.11.11.png)
                                    
            - **java.util.Map 컬렉션**
                - Map 인터페이스는 Collection 인터페이스와는 다른 저장 방식을 가집니다.
                    
                    Map 인터페이스를 구현한 Map 컬렉션 클래스들은 키와 값을 하나의 쌍으로 저장하는 방식(key-value 방식)을 사용합니다.
                    
                    여기서 키(key)란 실질적인 값(value)을 찾기 위한 이름의 역할을 합니다.
                    
                    Map 인터페이스를 구현한 모든 Map 컬렉션 클래스는 다음과 같은 특징을 가집니다.
                    
                    1. 요소의 저장 순서를 유지하지 않습니다.
                    2. 키는 중복을 허용하지 않지만, 값의 중복은 허용합니다.
                - 대표적인 Map 컬렉션 클래스에 속하는 클래스는 다음과 같습니다.
                    - HashMap<K, V> 클래스
                        - HashMap 클래스는 Map 컬렉션 클래스에서 가장 많이 사용되는 클래스 중 하나입니다.
                            
                            JDK 1.2부터 제공된 HashMap 클래스는 해시 알고리즘(hash algorithm)을 사용하여 검색 속도가 매우 빠릅니다.
                            
                            HashMap 클래스는 Map 인터페이스를 구현하므로, 중복된 키로는 값을 저장할 수 없습니다.
                            
                            하지만 같은 값을 다른 키로 저장하는 것은 가능합니다.
                            
                        - 여러 HashMap 메소드를 이용하여 맵을 생성하고 조작하는 예제
                            
                            ```java
                            HashMap<String, Integer> hm = new HashMap<String, Integer>();
                            
                             
                            
                            // put() 메소드를 이용한 요소의 저장
                            
                            hm.put("삼십", 30);
                            
                            hm.put("십", 10);
                            
                            hm.put("사십", 40);
                            
                            hm.put("이십", 20);
                            
                             
                            
                            // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
                            
                            System.out.println("맵에 저장된 키들의 집합 : " + hm.keySet());
                            
                            for (String key : hm.keySet()) {
                            
                                System.out.println(String.format("키 : %s, 값 : %s", key, hm.get(key)));
                            
                            }
                            
                             
                            
                            // remove() 메소드를 이용한 요소의 제거
                            
                            hm.remove("사십");
                            
                             
                            
                            // iterator() 메소드와 get() 메소드를 이용한 요소의 출력
                            
                            Iterator<String> keys = hm.keySet().iterator();
                            
                            while (keys.hasNext()) {
                            
                                String key = keys.next();
                            
                                System.out.println(String.format("키 : %s, 값 : %s", key, hm.get(key)));
                            
                            }
                            
                             
                            
                            // replace() 메소드를 이용한 요소의 수정
                            
                            hm.replace("이십", 200);
                            
                             
                            
                            for (String key : hm.keySet()) {
                            
                                System.out.println(String.format("키 : %s, 값 : %s", key, hm.get(key)));
                            
                            }
                            
                             
                            
                            // size() 메소드를 이용한 요소의 총 개수
                            
                            System.out.println("맵의 크기 : " + hm.size());
                            //실행 결과
                            맵에 저장된 키들의 집합 : [이십, 삼십, 사십, 십]
                            
                            키 : 이십, 값 : 20
                            
                            키 : 삼십, 값 : 30
                            
                            키 : 사십, 값 : 40
                            
                            키 : 십, 값 : 10
                            
                             
                            
                            키 : 이십, 값 : 20
                            
                            키 : 삼십, 값 : 30
                            
                            키 : 십, 값 : 10
                            
                             
                            
                            키 : 이십, 값 : 200
                            
                            키 : 삼십, 값 : 30
                            
                            키 : 십, 값 : 10
                            
                             
                            
                            맵의 크기 : 3
                            ```
                            
                    - HashMap<K, V> 메소드
                        
                        ![스크린샷 2022-04-22 오전 1.34.01.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cde451c9-1ebc-489a-a31e-df9a53bc82bd/스크린샷_2022-04-22_오전_1.34.01.png)
                        
                    - Hashtable<K, V>클래스
                        - Hashtable 클래스는 JDK 1.0부터 사용해 온 HashMap 클래스와 같은 동작을 하는 클래스입니다.
                            
                            현재의 Hashtable 클래스는 HashMap 클래스와 마찬가지로 Map 인터페이스를 상속받습니다.
                            
                            따라서 Hashtable 클래스에서 사용할 수 있는 메소드는 HashMap 클래스에서 사용할 수 있는 메소드와 거의 같습니다.
                            
                            하지만 현재에는 기존 코드와의 호환성을 위해서만 남아있으므로, Hashtable 클래스보다는 HashMap 클래스를 사용하는 것이 좋습니다.
                            
                    - TreeMap<K, V>클래스
                        - TreeMap 클래스는 키와 값을 한 쌍으로 하는 데이터를 이진 검색 트리(binary search tree)의 형태로 저장합니다.
                            
                            이진 검색 트리는 데이터를 추가하거나 제거하는 등의 기본 동작 시간이 매우 빠릅니다.
                            
                            JDK 1.2부터 제공된 TreeMap 클래스는 NavigableMap 인터페이스를 기존의 이진 검색 트리의 성능을 향상시킨 레드-블랙 트리(Red-Black tree)로 구현합니다.
                            
                            TreeMap 클래스는 Map 인터페이스를 구현하므로, 중복된 키로는 값을 저장할 수 없습니다.
                            
                            하지만 같은 값을 다른 키로 저장하는 것은 가능합니다.
                            
                        - **여러 TreeMap 메소드를 이용하여 맵을 생성하고 조작하는 예제**
                            
                            ```java
                            TreeMap<Integer, String> tm = new TreeMap<Integer, String>();
                            
                             
                            
                            // put() 메소드를 이용한 요소의 저장
                            
                            tm.put(30, "삼십");
                            
                            tm.put(10, "십");
                            
                            tm.put(40, "사십");
                            
                            tm.put(20, "이십");
                            
                             
                            
                            // Enhanced for 문과 get() 메소드를 이용한 요소의 출력
                            
                            System.out.println("맵에 저장된 키들의 집합 : " + tm.keySet());
                            
                            for (Integer key : tm.keySet()) {
                            
                                System.out.println(String.format("키 : %s, 값 : %s", key, tm.get(key)));
                            
                            }
                            
                             
                            
                            // remove() 메소드를 이용한 요소의 제거
                            
                            tm.remove(40);
                            
                             
                            
                            // iterator() 메소드와 get() 메소드를 이용한 요소의 출력
                            
                            Iterator<Integer> keys = tm.keySet().iterator();
                            
                            while (keys.hasNext()) {
                            
                                Integer key = keys.next();
                            
                                System.out.println(String.format("키 : %s, 값 : %s", key, tm.get(key)));
                            
                            }
                            
                             
                            
                            // replace() 메소드를 이용한 요소의 수정
                            
                            tm.replace(20, "twenty");
                            
                             
                            
                            for (Integer key : tm.keySet()) {
                            
                                System.out.println(String.format("키 : %s, 값 : %s", key, tm.get(key)));
                            
                            }
                            
                             
                            
                            // size() 메소드를 이용한 요소의 총 개수
                            
                            System.out.println("맵의 크기 : " + tm.size());
                            
                            //실행결과
                            맵에 저장된 키들의 집합 : [10, 20, 30, 40]
                            
                            키 : 10, 값 : 십
                            
                            키 : 20, 값 : 이십
                            
                            키 : 30, 값 : 삼십
                            
                            키 : 40, 값 : 사십
                            
                             
                            
                            키 : 10, 값 : 십
                            
                            키 : 20, 값 : 이십
                            
                            키 : 30, 값 : 삼십
                            
                             
                            
                            키 : 10, 값 : 십
                            
                            키 : 20, 값 : twenty
                            
                            키 : 30, 값 : 삼십
                            
                             
                            
                            맵의 크기 : 3
                            ```
                            
                    - TreeMap<K, V> 메소드
                        
                        
                        | 메소드 | 설명 |
                        | --- | --- |
                        | Map.Entry<K, V> ceilingEntry(K key) | 해당 맵에서 전달된 키와 같거나, 전달된 키보다 큰 키 중에서 가장 작은 키와 그에 대응하는 값의 엔트리를 반환함. 만약 해당하는 키가 없으면 null을 반환함. |
                        | K ceilingKey(K key) | 해당 맵에서 전달된 키와 같거나, 전달된 키보다 큰 키 중에서 가장 작은 키를 반환함.
                        만약 해당하는 키가 없으면 null을 반환함. |
                        | void clear() | 해당 맵(map)의 모든 매핑(mapping)을 제거함. |
                        | boolean containsKey(Object key) | 해당 맵이 전달된 키를 포함하고 있는지를 확인함. |
                        | boolean containsValue(Object value) | 해당 맵이 전달된 값에 해당하는 하나 이상의 키를 포함하고 있는지를 확인함. |
                        | NavigableMap<K, V> descendingMap() | 해당 맵에 포함된 모든 매핑을 역순으로 반환함. |
                        | Set<Map.Entry<K, V>> entrySet() | 해당 맵에 포함된 모든 매핑을 Set 객체로 반환함. |
                        | Map.Entry<K, V> firstEntry() | 해당 맵에서 현재 가장 작은(첫 번째) 키와 그에 대응하는 값의 엔트리를 반환함. |
                        | K firstKey() | 해당 맵에서 현재 가장 작은(첫 번째) 키를 반환함. |
                        | Map.Entry<K, V> floorEntry(K key) | 해당 맵에서 전달된 키와 같거나, 전달된 키보다 작은 키 중에서 가장 큰 키와 그에 대응하는 값의 엔트리를 반환함. 만약 해당하는 키가 없으면 null을 반환함. |
                        | K floorKey(K key) | 해당 맵에서 전달된 키와 같거나, 전달된 키보다 작은 키 중에서 가장 큰 키를 반환함.
                        만약 해당하는 키가 없으면 null을 반환함. |
                        | V get(Object key) | 해당 맵에서 전달된 키에 대응하는 값을 반환함.
                        만약 해당 맵이 전달된 키를 포함한 매핑을 포함하고 있지 않으면 null을 반환함. |
                        | SortedMap<K, V> headMap(K toKey) | 해당 맵에서 전달된 키보다 작은 키로 구성된 부분만을 반환함. |
                        | Map.Entry<K, V> higherEntry(K key) | 해당 맵에서 전달된 키보다 작은 키 중에서 가장 큰 키와 그에 대응하는 값의 엔트리를 반환함. 만약 해당하는 키가 없으면 null을 반환함. |
                        | K higherKey(K key) | 해당 맵에서 전달된 키보다 작은 키 중에서 가장 큰 키를 반환함.
                        만약 해당하는 키가 없으면 null을 반환함. |
                        | Set<K> keySet() | 해당 맵에 포함되어 있는 모든 키로 만들어진 Set 객체를 반환함. |
                        | Map.Entry<K, V> lastEntry() | 해당 맵에서 현재 가장 큰(마지막) 키와 그에 대응하는 값의 엔트리를 반환함. |
                        | K lastKey() | 해당 맵에서 현재 가장 큰(마지막) 키를 반환함. |
                        | Map.Entry<K, V> lowerEntry(K key) | 해당 맵에서 전달된 키보다 큰 키 중에서 가장 작은 키와 그에 대응하는 값의 엔트리를 반환함. 만약 해당하는 키가 없으면 null을 반환함. |
                        | K lowerKey(K key) | 해당 맵에서 전달된 키보다 큰 키 중에서 가장 작은 키를 반환함.
                        만약 해당하는 키가 없으면 null을 반환함. |
                        | Map.Entry<K, V> pollFirstEntry() | 해당 맵에서 현재 가장 작은(첫 번째) 키와 그에 대응하는 값의 엔트리를 반환하고, 해당 엔트리를 맵에서 제거함. |
                        | Map.Entry<K, V> pollLastEntry() | 해당 맵에서 현재 가장 큰(마지막) 키와 그에 대응하는 값의 엔트리를 반환하고, 해당 엔트리를 맵에서 제거함. |
                        | V put(K key, V value) | 해당 맵에 전달된 키에 대응하는 값으로 특정 값을 매핑함. |
                        | V remove(Object key) | 해당 맵에서 전달된 키에 대응하는 매핑을 제거함. |
                        | boolean remove(K key, V value) | 해당 맵에서 특정 값에 대응하는 특정 키의 매핑을 제거함. |
                        | V replace(K key, V value) | 해당 맵에서 전달된 키에 대응하는 값을 특정 값으로 대체함. |
                        | boolean replace(K key, V oldValue, V newValue) | 해당 맵에서 특정 값에 대응하는 전달된 키의 값을 새로운 값으로 대체함. |
                        | int size() | 해당 맵의 매핑의 총 개수를 반환함. |
                        | SortedMap<K, V> subMap(K fromKey, K toKey) | 해당 맵에서 fromKey부터 toKey까지로 구성된 부분만을 반환함.
                        이때 fromKey는 포함되나, toKey는 포함되지 않음. |
                        | SortedMap<K, V> tailMap(K fromKey) | 해당 맵에서 fromKey와 같거나, fromKey보다 큰 키로 구성된 부분만을 반환함. |
            
        
    - [java.io](http://java.io) 패키지
        
        
    - java.sql 패키지
        - DBMS
        - SQL