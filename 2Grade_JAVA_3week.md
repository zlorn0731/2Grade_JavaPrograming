# ☕ Java Programming Study
## 📘 2장 - 자바의 기본 프로그래밍 pg29 ~ 2장 끝까지

### Scanner 클래스
- System.in에게 키를 읽게 하고, 읽은 바이트를 문자, 정수, 실수, 불린, 문자열 등 다양한 타입으로 변환하여 리턴
  - java.util.Scanner 클래스
- 객체 생성
```
import java.util.Scanner; // import문 필요 | Ctrl + Shift + O
...
Scanner a = new Scanner(System.in); // Scanner 객체 생성

java.util = 패키지명
a = heap에 저장 address는 a에 저장 // stack : 크기가 정해짐 | heap : 크기가 안정해짐
System.in = 매개변수
```
- 키보드로 친 것들은 1Byte
```
키보드 → System.in → 0 1 1 1 0 1 0 0 1 0 1 → scanner → 'a', 3.5, "Hello" → 자바 응용프로그램
1Byte → 바이트 표준 입력 스트림 → 바이트 스트림 → byte를 int, double...으로 바꿔주는 것이 Scanner → Java
```
- System.in에게 키를 읽게 하고, 원하는 타입으로 변환하여 리턴

- Scanner에서 키 입력 받기
  - Scanner 클래스는 사용자가 입력하는 키 값을 공백 문자를 기준으로 분리하여 토큰 단위로 끊어 읽음
    - (' ', '\t', '\n')
```
사용자의 키 입력 | Kim  Seoul  20  65.1  true |

- Kim, Seoul, 20, 65.1, true : 토큰
```

#### 예제 2-7 : Scanner를 이용한 키 입력
- 사용자가 키를 입력하였을 때, Scanner 클래스의 메소드를 사용하여 사용자가 입력한 문자열, 정수 , 실수 등을 읽는 코드
```
Scanner scanner = new Scanner(System.in);

String name = scanner.next(); // "Kim"
String city = scanner.next(); // "Seoul"
int age = scanner.nextInt(); // 20
double weight = scanner.nextDouble(); // 65.1
boolean isSingle = scanner.nextBoolean(); // true
```
- 
| 메소드 | 설명 |
|-------|-------|
| String next() | 다음 토큰을 문자열로 리턴 |
| byte nextByte() | 다음 토큰을 Byte타입으로 리턴 |
| short nextShort() | 다음 토큰을 Short타입으로 리턴 |
| int nextInt() | 다음 토큰을 Int타입으로 리턴 |
| long nextLomg() | 다음 토큰을 Long타입으로 리턴 |
| float nextFloat() | 다음 토큰을 Flost타입으로 리턴 |
| double nextDouble() | 다음 토큰을 Double타입으로 리턴 |
| boolean nextBoolean() | 다음 토큰을 Boolean타입으로 리턴 |
| String nextLine() | '\n'을 포함하는 한 라인을 읽고, '\n'을 버린 나머지 문자열 리턴 |
| void close() |  Scanner 사용 종료 |
| boolean hasNext() | 현재 입력된 토큰이 있으면 true, 아니면 입력 때까지 무한정 대기, 새로운 입력이 들어올 때 true 리턴, ctrl + z 키가 입력되면 입력 끝으로 false 리턴 |
