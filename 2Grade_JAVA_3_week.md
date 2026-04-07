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

#### 예제 2-4 : Scanner를 이용한 키 입력 연습
```
package HS20260407;
package HS20260407;

import java.util.Scanner; // import문

public class ScannerTest {

	public static void main(String[] args) {
		System.out.println("이름, 도시, 나이, 체중, 독신 여부를 빈칸으로 분리하여 입력하세요");
		Scanner scanner = new Scanner(System.in); // 객체 생성
		
		String name = scanner.next(); // 문자열 읽기
		System.out.print("이름은" + name + ", ");
		
		String city = scanner.next(); // 문자열 읽기
		System.out.print("도시는" + city + ", ");
		
		int age = scanner.nextInt(); // 정수 읽기
		System.out.print("나이는" + age + "살, ");
		
		double weight = scanner.nextDouble(); // 실수 읽기
		System.out.print("체중은" + weight + "kg, ");
		
		boolean isSingle = scanner.nextBoolean(); // 논리값 읽기 true | false
		System.out.println("독신 여부는" + isSingle + "입니다.");
		
		scanner.close(); // scanner 객체 닫기
	}

}

- 결과
이름, 도시, 나이, 체중, 독신 여부를 빈칸으로 분리하여 입력하세요
Kim Seoul 20 65.1 true
이름은 Kim, 도시는 Seoul, 나이는 20살, 체중은 65.1kg, 독신 여부는 true입니다.
```

### 연산
- 연산 : 주어진 식을 계산하여 결과를 얻어내는 과정
```
a + 5 // 식
n > 23
a == n // a, n : 피연산자 | == : 연산자
```
- 
| 연산의 종류 | 연산자 | 연산의 종류 | 연산자 |
|------------|--------|-----------|----------|
| 증감 | ++, -- | 비트 | &, |, ^, ~ |
| 산술 | +, -, *, /, % | 논리 | &&, ||, !, ^ |
| 시프트 | >>, <<, >>> | 조건 | ? : |
| 비교 | >, <, >=, <=, ==, != | 대입 | =, *=, /=, +=, -=, &=, ^=, |=, <<=, >>=, >>>= |
```
연산자 우선순위

높음
⬇️ ++, --
⬇️ +, -, ++, --, ~, !
⬇️ *, /, %
⬇️ +, -
⬇️ <<, >>, >>>
⬇️ <>, <=, >=
⬇️ ==, !=
⬇️ & (비트 AND)
⬇️ ^ (비트 XOR)
⬇️ | (비트 OR)
⬇️ && (논리 AND)
⬇️ || (논리 OR)
⬇️ ? : (조건)
⬇️ =, +=, -=, *=, /=, %=, &=, ^=, |=, <<=, >>=, >>>=
낮음
```
- 같은 우선순위의 연산자
  - 왼쪽에서 오른쪽으로 처리
  - 예외) 오른쪽에서 왼쪽으로
    - 대입 연산자, --, ++, +, - (양수 음수 부호), !, 형 변환은 오른쪽에서 왼쪽으로 처리
- 괄호는 최우선순위
  - 괄호가 다시 괄호를 포함한 경우는 가장 안쪽의 괄호부터 먼저 처리

#### 산술 연산자 ( +, -, *, /, % )
- /와 %응용
```
10의 자리와 1의 자리 분리
69/10 = 6          ← 몫 6
69%10 = 9          ← 나머지 9

n이 홀수인지 판단
int r = n % 2;     // r이 1이면 n은 홀수, 0이면 짝수
```
- 
| 연산자 | 의미 | 예시 | 결과 |
|-------|------|-------|------|
| + | 더하기 | 25.5 + 3.6 | 29.1 |
| - | 빼기 | 3 - 5 | -2 |
| * | 곱하기 | 2.5 * 4.0 | 10.0 |
| / | 나누기 | 5 / 2 | 2 |
| % | 나머지 | 5 % 2 | 1 |

#### 예제 2-5 : /와 % 산술 연산
```
package HS20260407;

import java.util.Scanner;

public class ArithmeticOperator {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		
		System.out.print("정수를 입력하세요: ");
		int time = scanner.nextInt();
		int second = time % 60;
		int minute = (time / 60) % 60;
		int hour = (time / 60) / 60;
		
		System.out.print(time + "초는 ");
		System.out.print(hour + "시간, ");
		System.out.print(minute + "분, ");
		System.out.println(second + "초입니다.");
		
		scanner.close();
	}

}

- 결과
정수를 입력하세요:5000
5000초는 1시간, 23분, 20초입니다.
```

#### 증감 연산자 ( ++, -- )
- 1증가 혹은 감소 시키는 연산
```
   a = 1;               a = 1;
   b = ++a;             b = a++;
(a) 전위 연산자       (b) 후위 연산자
 ① a = 2              ① b = 1 
 ② b = 2              ② a = 2
```
- 
| 연산자 | 내용 | 연산자 | 내용 |
|-------|------|--------|------|
| a++ | a를 1 증가하고 증가 전의 값 반환 | ++a | a를 1 증가하고 증가된 값 반환 | 
| a-- | a를 1 감소하고 감소 전의 값 반환 | --a | a를 1 감소하고 감소된 값 반환 |

#### 대입 연산
- 연산의 오른쪽 결과는 왼쪽 변수에 대입
```
int a = 1, b = 3;
a = b; // b 값을 a에 대입하여 a = 3
a += b; // a = a + b의 연산이 이루어져, a = 6 b는 3 그대로
```
- 
| 대입 연산자 | 내용 | 대입 연산자 | 내용 |
|------------|------|------------|-------|
| a = b | b의 값을 a에 대입 | a &= b | a = a & b와 동일 |
| a += b | a = a + b와 동일 | a ^= b | a = a ^ b와 동일 |
| a -= b | a = a - b와 동일 | a |= b | a = a | b와 동일 |
| a *= b | a = a * b와 동일 | a <<= b | a = a << b와 동일 |
| a /= b | a = a / b와 동일 | a >>= b | a = a >> b와 동일 |
| a %= b | a = a % b와 동일 | a >>>= b | a = a >>> b와 동일 |

#### 예제 2-6 : 대입 연산자와 증감 연산자 사용
```
package HS20260407;

public class AssignmentInDecOperator {

	public static void main(String[] args) {
		int a = 3, b = 3, c = 3;
		
		a += 3;
		b *= 3;
		c %= 2;
		System.out.println("a=" + a + ", b=" + b + ", c=" + c);
		
		int d = 3;
		a = d++;
		System.out.println("a=" + a + ", d=" + d);
		a = ++d;
		System.out.println("a=" + a + ", d=" + d);
		a = d--;
		System.out.println("a=" + a + ", d=" + d);
		a = --d;
		System.out.println("a=" + a + ", d=" + d);
	}

}

- 결과
a=6, b=9, c=1
a=3, d=4
a=5, d=5
a=5, d=4
a=3, d=3
```

#### 비교 연산과 논리 연산
- 비교 연산
  - 두 피연산자를 비교하여 true 또는 false의 논리 값을 내는 연산
- 
| 연산자 | 내용 | 예제 | 결과 |
|-------|------|------|------|
| a < b | a가 b보다 작으면 true | 3 < 5 | true |
| a > b | a가 b보다 크면 true | 3 > 5 | false |
| a <= b | a가 b보다 작거나 같으면 true | 1 <= 0 | false | 
| a >= b | a가 b보다 크거나 같으면 true | 10 >= 10 | true |
| a == b | a가 b와 같으면 true | 1 == 3 | false |
| a != b | a가 b와 같지 않으면 true | 1 != 3 | true |

- 논리 연산
  - 논리 값으로 NOT, OR, AND, XOR 논리 연산 논리 값을 내는 연산
- 
| 연산자 | 내용 | 예제 | 결과 |
|-------|------|-----|-------|
| !a | a가 true이면 false, false이면 true | !(3<5) | false |
| a || b | a와 b의 OR연산 a와 b모두 false인 경우에만 false | (3>5) || (1==1) | true |
| a && b | a와 b의 AND연산 a와 b모두 true인 경우에만 true | (3<5) && ( 1==1) | true |
| a ^ b | a와 b의 XOR연산 a와 b가 서로 다를 때 true | (3>5)^(1==1) | true |

- 비교 연산과 논리 연산의 복합 사례
```
(age >= 20) && (age < 30) // 나이(int age)가 20대인 경우
(c >= 'A') && (c <= 'Z') // 문자(char c)가 대문자인 경우
(x >= 0) && (y >= 0) && (x <= 50) && (y <= 50) // (x, y)가 (0, 0)과 (50, 50)의 사각형 내에 있음

- 오류 : 20 <= age <= 30 // 오류
```

#### 예제 2-7 : 비교 연산자와 논리 연산자 사용하기
```
package HS20260407;

public class LogicalOperator {

	public static void main(String[] args) {
		System.out.println('a' > 'b');
		System.out.println(3 >= 2);
		System.out.println(-1 < 0);
		System.out.println(3.45 <= 2);
		System.out.println(3 == 2);
		System.out.println(3 != 2);
		System.out.println(!(3 != 2));
		
		System.out.println((3 > 2) && (3 > 4));
		System.out.println((3 != 2) || (-1 > 0));
		System.out.println((3 != 2) ^ (-1 > 0));
	}

}

- 결과
false
true
true
false
false
true
false
false
true
true
```

#### 조건 연산
- 조건 연산자 : 3개의 피연산자로 구성되어 삼항 연산자라고도 함
```
condition ? opr2 : opr3
```
```
int x = 5;
int y = 3;
int s = (x>y) ? 1 : 1; // x가 y보다 크기 때문에 1이 s에 대입
```
- if-else을 간결하게 표현할 수 있음
```
int x = 5;
int y = 3;

int s;
if(x > y)
   s = 1;
else
   s = -1;
```

#### 예제 2-8 : 조건 연산
```
package HS20260407;

public class TernaryOperator {

	public static void main(String[] args) {
		int a = 3, b = 5;
		
		System.out.println("두 수의 차는 " + ((a>b)?(a-b):(b-a)));
	}

}

- 결과
두 수의 차는 2
```

#### 비트 연산
```
byte x = 10;

   ----- 바이트 -----
x | 0 0 0 0 1 0 1 0 |
              ↑비트
```
##### 비트 논리 연산
- AND, OR, XOR, NOT 연산
```
(AND)
    01101010
&   11001101 
------------- 모두 1이므로 결과는 1 | 둘 중 하나라도 0이면 결과는 0
    01001000

(OR)
    01101010
|   11001101
------------- 모두 0이므로 결과는 0 | 둘 중 하나라도 1이면 결과는 1
    11101111

(XOR)
    01101010
^   11001101
------------- 두 비트가 같으므로 결과는 0 | 두 비트가 다르므로 결과는 1
    10100111

(NOT)
~   01101010
------------- 1은 0으로 변환 | 0은 1로 변환
    10010101
```
- 
| 연산자 | 별칭 | 내용 |
|-------|------|-------|
| a & b | AND | 두 비트 모두 1이면 1, 그렇지 않으면 0 |
| a | b | OR | 두 비트 모두 0이면 0, 그렇지 않으면 1 |
| a ^ b | XOR | 두 비트가 다르면 1, 같으면 0 |
| ~ a | NOT | 1을 0으로, 0을 1로 변환 |

##### 비트 시프트 연산
- 비트를 오른쪽이나 왼쪽으로 이동
- 
| 시프트 연산자 | 내용 |
|--------------|------|
| a >> b | a의 각 비트를 오른쪽으로 b번 시프트 함, 최상위 비트의 빈자리는 시프트 전의 최상위 비트로 다시 채움, 산술적 오른쪽 시프트라고 함 |
| a >>> b | a의 각 비트를 오른쪽으로 b번 시프트 함, 최상위 비트의 빈자리는 항상 0으로 채움, 논리적 오른쪽 시프트라고 함 |
| a << b | a의 각 비트를 왼쪽으로 b번 시프트 함, 최하위 비트의 빈자리는 항상 0으로 채움, 산술적 왼쪽 시프트라고 함 |
```
byte a = 5; // 5
byte b = (byte)(a << 2); // 20

                    ↓ 항상 0으로 채움
a  |  0 0 0 0 0 1 0 1
      ↙↙↙↙↙↙↙↙
      0 0 0 0 1 0 1 0  
      ↙↙↙↙↙↙↙↙
b  |  0 0 0 1 0 1 0 0
-----------------------------------------
byte a = 20; // 20
byte b = (byte)(a >>> 2); // 5

      ↓ 항상 0으로 채움
a  |  0 0 0 1 0 1 0 0
       ↘↘↘↘↘↘↘↘
      0 0 0 0 1 0 1 0
       ↘↘↘↘↘↘↘↘
b  |  0 0 0 0 0 1 0 1
-----------------------------------------
byte  a = 20; // 20
byte b = (byte)(a >> 2); // 5

      ↓ 최상위 비트로 채움
a  |  0 0 0 1 0 1 0 0
       ↘↘↘↘↘↘↘↘
      0 0 0 0 1 0 1 0
       ↘↘↘↘↘↘↘↘
b  |  0 0 0 0 0 1 0 1
-----------------------------------------
byte  a = (byte)0xf8; // -8
byte b = (byte)(a >> 2); // -2

      ↓ 최상위 비트로 채움
a  |  1 1 1 1 1 0 0 0
       ↘↘↘↘↘↘↘↘
      1 1 1 1 1 1 0 0
       ↘↘↘↘↘↘↘↘
b  |  1 1 1 1 1 1 1 0
```
#### 예제 2-9 : 비트 논리 연산과 비트 시프트 연산
```
package HS20260407;

public class BitOperator {

	public static void main(String[] args) {
		short a = (short)0x55ff;
		short b = (short)0x00ff;
		
		System.out.println("[비트 연산 결과]");
		System.out.printf("%04x\n", (short)(a & b));
		System.out.printf("%04x\n", (short)(a | b));
		System.out.printf("%04x\n", (short)(a ^ b));
		System.out.printf("%04x\n", (short)(~a));
		
		byte c = 20; // 0x14
		byte d = -8; // 0xf8
		
		System.out.println("[시프트 연산 결과]");
		System.out.println(c << 2);
		System.out.println(c >> 2);
		System.out.println(d >> 2);
		System.out.printf("%x\n", (d >>> 2));
		
	}

}

- 결과
[비트 연산 결과]
00ff
55ff
5500
aa00
[시프트 연산 결과]
80
5
-2
3ffffffe
```
#### 체크 문제
- 1. 다음 문장을 수행한 후 z 값은?
```
int x = 2, y = 10, z = 0;
z = x++*2+--y-5+x*(y%2);
```
```
풀이:
z = 4+9-5+x(y%2)
x = 3, y = 9
z = 4+9-5+3*1
  = 13-5+3
  = 11
```
- 2. 다음 문장을 실행하면 화면에 출력되는 값은?
```
System.out.println(8 >> 2);
System.out.println(-16 >> 2);
```
```
풀이:
8 = 00001000
>> 2 = 00000010 = 2
-16 = 10010000  ⇄ 01101111 +1 > 01110000
>> 2 = 11111100
10진수로 > 00000011 + 1 > 00000100 = 4
마이너스였으니까 - 붙이기 = -4

2
-4
```
- 3. 다음 문장을 실행하면 화면에 출력되는 값은?
```
int opr = 4;
System.out.println(opr++);
```
```
풀이:
후위 연산자
= 4
```

##### ✍️ 작성자: 박지안
##### 🐧 실습 환경: Eclipse
##### 🗓️ 작업일: 2026-04-07
