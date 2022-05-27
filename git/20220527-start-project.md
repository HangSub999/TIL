나는 지금까지 next()와 nextLine()의 차이는 단순히 한 줄을 전부 입력받고 싶을 때(한 문장을 입력한다던지)는 nextLine()을 사용하고 한 단어씩 입력하고자 할 때는 next()를 사용한다 정도의 가볍게 알고있었다.

하지만 약간의 차이점은 존재했고 주의사항을 확실하게 짚고 넘어가고자 한다.



next(), nextLine()는 Scanner 클래스의 메소드이다. 공통점은 둘다 문자열로 반환을 시켜준다는 점이고 차이점은 개행문자를 무시하냐 안하냐의 차이라고 할 수 있다.






메소드 참고





1. 입출력시 주의사항

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
import java.util.Scanner;

public class Test {
public static void main(String[] args) {
Scanner input = new Scanner(System.in);

        int num;
        String str;
        System.out.println("num입력");
        num = input.nextInt();
 
        System.out.println("str입력");
        str = input.nextLine();
 
        System.out.println("num : " + num);
        System.out.println("str : " + str);
        input.close();
    }
}


s

출처 : https://sleepyeyes.tistory.com/22
원래 원했던 입력은 숫자1번, 문자1번 이었을 것이지만, 숫자1번 입력하면 바로 자동으로 출력이 된다.



그 이유가 무엇일까?
next()는 개행문자를 무시하고 입력을 받고 nextLine은 한줄 단위로 입력을 받기 때문에 개행문자로 포함한다.

좀 더 직관적으로 설명하자면 위 처럼 5를 입력하고 Enter를 쳤다면 버퍼에 5\n이 존재한다. 이 때 nextInt()가 버퍼의 내용을 가져올 때 분리자를 제외하고 가져오기 때문에 5만 가져오게 된다. 그러면 버퍼에 \t가 남아있는데 nextLine()은 공백문자, 개행문자인 분리자를 포함시키기 때문에 \t만 가져오고 프로그램이 종료되는 것이다.





1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
import java.util.Scanner;

public class Test {
public static void main(String[] args) {
Scanner input = new Scanner(System.in);

        int num;
        String str;
        System.out.println("num입력");
        num = input.nextInt();
 
        System.out.println("str입력");
        str = input.next();
 
        System.out.println("num : " + num);
        System.out.println("str : " + str);
        input.close();
    }
}



출처 : https://sleepyeyes.tistory.com/22
위와 같이 nextLine()을 next()로 바꾸어 주는 것도 하나의 방법이다.









입력과 버퍼의 관한 정리


우선 우리가 키보드를 통해 키입력을 받으면 입력받은 내용이 버퍼라는 기억공간에 저장이 된다.

​

또한 콘솔에서 아무 키만 입력된다고해서 입력이 되는것이 아니라 마지막에 엔터키를 눌러야 지금까지 눌렀던

​

내용이 버퍼에 전달되어 저장이 된다.

​

먼저 키보드로 120<엔터> 라고 입력했다고 가정하자. 참고로 엔터에 해당하는 코드 문자는 \r\n 이다.

​

그럼 버퍼에는 120<엔터>라고 들어갈 것이다.

​

입력은 nextInt() 메서드가 실행된이후 버퍼에 내용이 있는지 확인하게 된다. 처음이니 버퍼에 내용은 없다.

​

따라서 키보드로부터 사용자의 입력을 기다리는 상태가 되고, 위에 가정한대로 입력을 받게 된다.

​

그리고 버퍼에서 공백,탭문자,개행문자(엔터)를 구분으로 해서 하나의 단어를 가져오게 된다.

​

버퍼에서는 120까지를 가져오게 됩니다. 그리고 버퍼에는 <엔터> 만 남는다.

​

만약 이 뒤에 또다시 nextInt() 메서드가 실행된다면?

​

버퍼를 확인해서 비어있는지 살펴봐야한다. 비어있지는 않지만 개행문자만 있으므로 건너띄고 내용이 없으므로

​

사용자로부터 입력을 받게 됩니다.

​

200<엔터>

​

그럼 위에서 실행된 nextInt()는 200이라는 값만 가지고 가게 되고 <엔터> 문자는 남게 된다.

​

다음번에 nextLine()이 아닌 메서드가 실행되는 경우 엔터 코드는 무시하고 다음 문자를 찾게 되니깐 상관이 없지만,

​

이상태에서 nextLine()메서드를 실행하게 된다면 문제가 약간 생긴다.

​

nextLine()을 실행하려는 이유는 한줄의 입력내용을 받기 위함 이다.

​

여기서 한줄이라고 함은 처음부터 개행문자(엔터)까지의 문자열을 의미합니다.



한마디로 nextLine()은 분리자도 다 읽어올 수 있고, next(), nextInt()는 분리자는 제외하고 읽어온다.

​

즉, 가<엔터> or 가나다 라마<엔터>

​

어떤식으로 입력이 되었든 <엔터> 까지 문자열을 모두 가져오게 되고. 그럼 nextLine()을 실행한 후에는 아무런 값이 남지 않게 된다.

​

여기에서 nextLine()은 개행문자를 가져와서 버려지게 되고 개행문자 이전 문자열만 반환하게 되고, 이렇게 nextInt()등을



쓰고 난뒤에 nextLine()을 쓰게되면 위와 같은 현상을 직면하게 되므로,

​

int num = sc.nextInt();

sc.nextLine();

String str = sc.nextLine();

​

이런식으로 중간에 남은 코드를 정리하기 위하여 nextLine();을 실행해주면 된다.



반환문자는 필요없으므로 메서드만 호출하게 되고 그리고 새로 nextLine()을 실행해서 한줄을 받아오게 된다.

​

다른 방법으로는 nextInt(); 대신 Integer.parseInt(sc.nextLine());

​

이렇게 아예 한줄, 즉 개행문자까지 가져온뒤에(어차피 버려지므로) 정수형으로 반환하는 것이다.