# ☕ Java Programming Study

## 📘 2장 - 자바의 기본 프로그래밍 29pg까지

#### 예시 2-1 자바프로그램의 기본 구조
```
/*
 *  소스 파일 : HomeStudy.java
 */
public class HomeStudy {

	public static int sum(int n, int m) { 
		return n + m;
	}
	
	// main() 메소드에서 실행 시작
	public static void main(String[] args) {
	int i = 20; // 지역 변수
	int s; // 지역 변수
	char a; // 지역 변수
	
	s = sum(i, 10); // sum 메소드 호출
	a = '?';
	System.out.println(a); // 문자 '?' 화면 출력
	System.out.println("Hello"); // "Hello" 문자열 화면 출력
	System.out.println(s); // 정수 s 값 화면 출력
	}

}
- 결과
?
Hello
30
```
### 예시 2-1 코드 설명
- 클래스 만들기
  - HomeStudy 이름의 클래스 선언
```
public class HomeStudy {
}
```
  - class 키워드로 클래스 선언
  - public 선언하면 다른 클래스에서 접근 가능 
  - 클래스 코드는 { } 내에 모두 작성
  - 클래스 안에 변수, 상수, 메소드 등 모든 프로그램 요소를 작성
  - 클래스 밖에 작성 ❌

- 주석문
  - // : 한 라인 주석
  - /**/ : 여러 라인 주석
 
- main() 메소드
  - 자바 프로그램은 main() 메소드에서부터 실행 시작
```
public static void main(String[] args) {
.... // eclipse에서 class 만들 때 체크박스 체크하면 자동으로 만들어짐
}
```
  - main()은 반드시 public, static, void 타입으로 선언
  - String[] args로 실행 인자를 전달 받음
  - 한 클래스에 2개의 main() 작성 ❌
  - 여러 클래스로 이루어지는 경우, 실행을 시작할 클래스에만 main()을 두면 됨

- 메소드
  - C/C++에서의 함수를 메소드로 지칭
```
public static int sum(int n, int m) { // 파라미터 n, m
   return n + n; // n과 m의 합 = return
}
```
  - 메소드의 이름은 개발자가 지정, 메소드의 개수에는 제한 ❌

- 메소드 호츌
  - sum() 메소드 호출
```
int i = 20;
s = sum(1, 10); // s : 30 return, sum(i, 10) : sum() 메소드 호출
```
  - sum() 호출 시 변수 i의 값과 정수 10을 전달
  - sum()의 n, m에 각각 20, 10 값 전달
  - sum()은 n과 m 값을 더한 30 return
  - 변수 s는 정수 30을 전달받음 

- 변수 선언
  - 프로그램 실행 동안 데이터를 저장하는 공간
  - 개발자가 이름을 붙이고 다음과 같이 선언
```
int i;
char a;
```
  - 메소드 내에 선언되어 사용되는 변수 : 지역변수(rocal variable)
  - 메소드 내에서만 사용, 메소드의 실행이 끝나면 소멸
  - 다음과 같이 선언하면 동시에 선언, 값 초기화 가능
```
int i = 20; // 변수 i의 선언과 동시에 20으로 초기화
```

- 문장
  - 모든 문장은 다음과 같이 ';'로 끝내야 함
```
int i = 20;
s = sum(i, 20);
```

- 화면 출력
  - 정수, 문자, 문자영 들 프로그램에서 사용하는 데이터를 화면에 출력하기 위해 System.out.println(), System.out.print() 이용
  - System.out.println() : 출력 후 다음 행으로 이동
  - System.out.print() : 다음 줄로 넘어 가지 않음
```
System.out.println("Hello") // "Hello" 문자열 출력
System.out.println(3); // 3 출력
System.out.println(2 * 5); // 10 출력
```

### 식별자(identifier)
- 식별자(identifier) : 클래스, 변수, 상수, 메소드 등에 붙이는 이름
- 식별자 이름 규칙
  - 특수 문자(%, *, &, @, ^ 등), 공백(tap, space 등)은 식별자로 사용 ❌
  - 특수 문자(_, $)만 사용 가능 : 잘 사용 하지 않음
  - 한글도 식별자로 사용 가능 : 잘 사용 하지 않음
  - if, while, class 등 자바 언의 키워드는 식별자로 사용 ❌
  - 식별자의 첫 번째 문자로 숫자는 사용 ❌
  - true, false, null은 자바의 키워드이므로 식별자로 사용 ❌
  - 대소문자 구별 : Test, test는 별개의 식별자
  - 길이 제한 ❌
```
- 🅾️ 식별자로 사용 가능한 예시
int name; 
char student_ID; // _ 사용 가능
void $func() { } // $ 사용 가능
class Monster3 { } // 숫자 사용 가능
int whatsYourNameMyNameIsKitae; // 길이 제한 ❌
int barChart; int barchart; // 대소문자 구분 : barChart, barchart는 다른 이름
int 가격; // 한글 식별자 사용 가능
```
```
- ❌ 식별자로 사용 불가능한 예시
int 3Chapter; // 첫 번째 문자로 숫자 사용 ❌
class if { } // 자바의 예약어 if 사용 ❌
char false; // 자바의 예약어 false 사용 ❌
void null() { } // 자바의 예약어 null 사용 ❌
class %calc { } // 특수 문자 % 사용 ❌
```

### 자바 키워드
- 
| 키워드 | 키워드 | 키워드 | 키워드 | 키워드 |
|--------|-------|-------|--------|---------|
| abstract | continue | float | native | strictfp | void |  
| assert | default | for | new | super | volatile |
| boolean | do | if | package | switch | while |  
| break | double | implements | private | synchronized | 
| byte | else | import | protected | this |  
| case | enum | instanceof | public | throw |
| catch | extends | int | return | throws |  
| char | final | interface | short | transient |
| class | finally | long | static | try |

### 좋은 이름 붙이는 언어 관습
- 기본 : 가독성 높은 이름
  - 목적을 나타내는 이름 붙이기 : s 보다 sum
  - 충분히 긴 이름으로 붙이기 : AVM 보다 AutoVendingMachine
- 자바 언어의 이름 붙이기 관습 : 카메(Camel) 표기
  - 전체적으로 소문자로 이름 붙이고
  - 여러 단어로 구성되는 이름은 각 단어의 첫 글자만 대문자
- 클래스 이름
  - 첫 번째 문자는 대문자로 시작
```
public class HelloWorld {}
class AutoVendingMachine {}
```
- 변수, 메소드 이름
  - 첫 번째 문자는 소문자로 시작
```
int myAge;
boolean isSingle;
public int getAge() {return 20};
```
- 상수 이름
  - 모든 문자를 대문자로 표시
  - final을 붙여야 값이 변하지 않은 상수, 안 붙이면 값이 변하는 변
```
final double PI = 3.141592; // PI = 3.141592;의 값은 바뀌지 않음
```

### 자바의 데이터 타입
- 자바에서 다룰 수 있는 데이터의 종류
  - 기본 타입 8개 + 래퍼런스 타입 1개 = 총 9개의 타입 데이터
```
- 기본 타입 8개
boolean
char
byte
short
int
long
float
double
```
```
- 레퍼런스 타입은 한 가지이지만 용도는 3가지
배열에 대한 레퍼런스
클래스(clasS)에 대한 레퍼런스
인터페이스(interface)에 대한 레퍼런스
```
- 래퍼런스 : C/C++의 포인터와 달리 실제 주소 값을 가지지 않음
```
- C
int a = 10;
int *p = &a; // 주소가 눈에 보임
printf("%p", p);
```
```
- Java
String a = "Hello"; // a에 내부적으로 주소를 가짐
System.out.println(a); 
```

### 자바의 기본 타입
- CPU나 운영체제에 따라 변하지 않음
  - 논리 타입 : boolean (1bit, true | false) → 자바 가상 기계에서는 처리하는 boolean의 실제 크기는 1bit가 아닐 수도 있음
  - 문자 타입 : char (2byte, Unicode)
  - 정수 타입 : byte (1byte, -128 ~ 127)
  - 정수 타입 : short (2byte, -32768 ~ 32767)
  - 정수 타입 : int (4byte, -2,147,483,648 ~ 2,147,483,647)
  - 정수 타입 : long (8byte, -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807)
  - 실수 타입 : float (4byte, -3.4E38 ~ 3.4E38)
  - 실수 타입 : double (8byte, -1.7E308 ~ 1.7E308)
- 
| 타입      | 용어    | 크기 |
|-----------|--------|-------|
| 논리 타입 | boolean | 1bit [] | 
| 문자 타입 | char    | 2byte □□ | 
| 정수 타입 | byte    | 1byte □ |
| 정수 타입 | short   | 2byte □□ |
| 정수 타입 | int     | 4byte □□□□ |
| 정수 타입 | long    | 8byte □□□□□□□□ |
| 실수 타입 | float   | 4byte □□□□ |
| 실수 타입 | double  | 8byte □□□□□□□□ |

### 문자열
- 문자열은 기본 타입이 아님
- JDK에서 제공하는 String클래스를 이용
  - 문자열 리터럴
```
String toolName = "JDK";
```
- + 연산
  - 문자열과 기본 타입이 실행되면
  - 기본 타입의 값이 문자열로 바뀌고 두 문자열이 연결된 새로운 문자열이 생성
  - 문자열이 섞인  + 기본 타입 → 문자열 연결 
```
toolName = toolName + 1.8 // "JDK1.8"
String a = "(" + 3 + ", " + 5 + ")" // "(3, 5)"
System.out.println(a); // (3, 5) 출력
System.out.println(toolName + "이 출시됨"); // "JDK1.8이 출시됨" 출력
```

### 변수와 선언
- 변수
  - 프로그램 실행 중에 값을 임시 저장하기 위한 공간
    - 변수 값은 프로그램 수행 중 변경될 수 있음
  - 데이터 타입에서 정한 크기의 메모리 할당
- 변수 선언
  - 변수의 타입 다음에 변수 이름을 적어 변수를 선언
```
int price; → [데이터 타입] [변수 이름]
| price | ← 7, 25 가능 ← 3.5(실수 저장 안됨)
```

### 변수 선언 사례
- 변수 선언 사례
```
int radius;
char c1, c2, c3; // 3개의 변수를 한 번에 선언함
```
- 변수 선언과 초기화
  - 선언과 동시에 초기값 지정
```
int radius = 10;
char c1 = 'a', c2 = 'b', c3 = 'c';
double weight = 75.56;
```
- 변수 읽기와 저장
```
radius = 10 * 5; // 변수 radius에 10 x 5의 결과 50저장
c1 = 'r'; // 변수 c1에 문자 'r'저장
weight = weight + 5.0; // 변수 weight의 값을 읽고 5.0을 더해 weight에 다시 저장
```

### 리터럴
- 리터럴 : 프로그램에 직접 표현한 값을 말함
  - 정수, 실수, 문자, 논리, 문자열 타입 모두 리터럴이 있음
```
34, 42.195, '%', true, "hello"
```

### 진법
- 숫자를 표현하는 방식
  -  2진수 → 0~1(2개)
```
컴퓨터가 사용하는 숫자
2진수 : 0, 1
(예시)
1011₂
1×2³ + 0×2² + 1×2¹ + 1×2⁰ → 기준이 2 
= 8 + 0 + 2 + 1
= 11 (10진수)
```
  -  8진수 → 0~7(8개)
```
8진수 : 0 1 2 3 4 5 6 7
(예시)
17₈
1×8¹ + 7×8⁰ → 기준이 8
= 8 + 7
= 15 (10진수)
```
  -  10진수 → 0~9(10개)
```
10진수 : 0 1 2 3 4 5 6 7 8 9
(예시)
123
1×10² + 2×10¹ + 3×10⁰ → 기준이 10
= 100 + 20 + 3
```
  -  16진수 → 0~15(16개)
```
16진수 : 0 1 2 3 4 5 6 7 8 9 A B C D E F
A = 10, B = 11, C = 12, D = 13, E = 14, F = 15
(예시) 
1A₁₆  
1×16¹ + 10×16⁰ → 기준이 16
= 16 + 10
= 26 (10진수)
``` 

#### 예시
```
2진수 ↔ 8진수
2진수 : 101 111 
8진수 :  5   7
```
```
2진수 ↔ 16진수
2진수 : 1111
16진수 : F
```

### 진법 자바에서 표현 방법
- 2진수 : 0b
```
int a = 0b1010; // 10
```
- 8진수 : 0
```
int b = 012; // 10
```
- 16진수 : 0x
```
int c = 0xA; // 10	
```
- 10진수는 아무 표시 없음
```
int d = 10; // 10
```

### 정수 리터럴
- 10진수, 8진수, 2진수, 16진수 리터럴
```
15 → 10진수 리터럴 15
015 → 0으로 시작하면 8진수, 10진수로 13
0x15 → 0x으로 시작하면 16진수, 10진수로 21
0b0101 → 0b로 시작하면 2진수, 10진수로 5
-----------------------------------------
int n = 15;
int m = 015;
int k = 0x15;
int b = 0b0101;
```
- long 타입으로 지정하려면 숫자 뒤에 L 또는 l을 붙임
```
long g = 24L; // 24L, 24l 동일
```

### 실수 리터럴
- 소수점 형태나 지수 형태로 표현 가능
```
12. 12.0 .1234 / 0.1234, 1234E-4
```
- 실수 리터럴은 double 타입으로 자동 처리, 변수와 함께 씀
```
double d = 0.1234; 
double f = 1234E-4; // 1234E-4 = 0.1234
```
- 숫자 뒤에 F 또는 f를 붙이면 float, D 또는 d를 붙이면 double 타입으로 강제 변환 가능
```
float f = 0.1234F; // f = 0.1234로 하면 컴파일 오류
double w = .1234D; // .1234D와 .1234는 동일 기본이 double형이라 D, d 안붙여도 됨
```

### 문자 리터럴
- 단일 인용부호('')로 문자를 표현
- \u 다음에 문자의 유니코드 값을 사용하여 표현
```
'W', 'A', '가', '*', '3', '글', \u0041
```
- 문자 리터럴을 변수와 함께 사용
```
char a = 'A';
char b = '글';
char c = \u0041; // 문자 'A'의 유니코드 값(0041) 사용
char d = \uae00; // 문자 '글'의 유니코드 값(ae00) 사용
```

### 특수문자 리터럴
- 백슬래시(\) 다음에 특수 기호를 붙여서 표현
- 
| 종류 | 의미 | 종류 | 의미 |
|------|------|------|-------|
| '\b' | 백스페이스 | '\r' | 캐리지 리턴 |
| '\t' | 탭 | '\"' | 큰따옴표 |
| '\n' | 줄바꿈 | '\'' | 작은따옴표 |
| '\f' | 폼피드 | '\\' | 백슬래시 |

### 유니코드(Unicode)
- 문자의 표현
  - 아스키(ASCII)코드 : 1byte
  - 유니코드(Unicode)
 
### 논리 리터럴과 boolean 타입
- 논리 리터럴은 2개뿐
  - true, false
  - boolean 타입 변수에 치환하거나 조건문에 이용
```
boolean a = true;
boolean b = 10 > 0; // 10>0은 참이므로 b 값은 true
boolean c = 1; // 타입 불일치 오류, C/C++에서는 가능
```

### null 리터럴
```
int n = null; // 기본 타입에 사용 불가
String str  = null;
```

### 문자열 리터럴(스트링 리터럴)
- ("")로 묶어 표현
  - "Good", "Morning", "자바", "3.19", "26", "a"
- 문자열 리터럴은 String 객체로 자동 처리
```
String str = "Good";
```

### 상수
- 상수 선언
  - final 키워드 사용
  - 선언 시 초기값 지정
  - 실행 중 값 변경 불가
```
final double PI = 3.141592;
| 상수 선언 | 데이터 타입 | 상수 이름 | = 초기화 |
```
#### 예제 2-2 : 변수, 리터럴, 상수 활용
```
// 상수 PI를 선언하고 원의 면적을 구하는 프로그램을 작성하시오.

public class CircleArea {

	public static void main(String[] args) {
		final double PI = 3.14; // 원주율을 상수로 선언
		
		double radius = 10.0; // 원의 반지름
		double circleArea = radius * radius * PI; // 원의 면적 계산
		
		// 원의 면적을 화면에 출력
		System.out.println("원의 면적 = " + circleArea);
	}

}
```

### 자동 타입 변환
- 자동 타입 변환 : 타입이 일치하지 않을 때, 컴파일러는 오류 대신 작은 타입을 큰 타입으로 자동 변환함
```
long m = 25; // 리터럴 25는 int 타입. 25가 long 타입으로 자동 변환
| 25 | [4byte = 32bit] → m | 0025 | [8byte = 64bit]
double d = 3.14 * 10; // 실수 연산을 하기 위해 10이 10.0으로 자동 변환
                      // 다른 피연산자가 3.14가 실수이기 때문
```

### 강제 타입 변환
- 강제 타입 변환 : 개발자가 강제로 타입 변환을 지시하는 경우
```
int n = 300;
byte b = n; // int > byte → 컴파일 오류. int 타입은 byte 타입으로 자동 변환 안됨
byte  b = (byte)n; // n을 byte 타입으로 강제 변환. b = 44
```
- int에 저장된 값 300은 byte타입 (0~255)의 범위보다 큼
- 강제 타입 변환을 하면 300 - 256 을 뺀 44가 출력
- 즉 44가 변수 b에 저장되어 데이터 손실이 발생함

```
double d = 1.9;
int n = (int)d; // 강제 타입 변환으로 n은 1이 됨
                // 0.9 데이터 손실
```
- 다음과 같이 실수를 정수로 강제 변환하면 소수점 이하의 손실이 발생함
- 강제 타입 변환을 캐스팅(casting)이라고도 부름

#### 예제 2-3 : 타입 변환
```
// 자동 타입 변환과 강제 타입 변환이 들어 있는 코드

public class TypeConversion {

	public static void main(String[] args) {
		byte b = 127; // byte 범위는 -128 ~ 127 그래서 127 저장 가능
		int i = 100; // int는 4바이트 정수형 그래서 100 저장 가능
		
		System.out.println(b+i); // byte, short, char는 보통 int로 자동 변환
		System.out.println(10/4); // 정수 나누기이므로 결과는 2
		System.out.println(10.0/4); // 4가 4.0으로 자동 변환, 실수 나누기이므로 결과는 2.5
		System.out.println((char)0x12340041); // char로 변환된 결과 0x0041로서 문자 'A' / 16진수 정수 리터럴
                                              // char 타입으로 강제 변환 / char은 2byte = 16bit, 16bit만 남김 = 0x0041
		System.out.println((byte)(b+i)); // b+i는 227, 16진수 0x53, 즉 -29
		System.out.println((int)2.9 + 1.8); // 3.8
		System.out.println((int)(2.9 + 1.8)); // 4
		System.out.println((int)2.9 + (int)1.8); // 3

	}

}
```
- System.out.println((byte)(b+i)); = -29 해설
```
(byte)(227) 2진수로 바꿔야됨 컴퓨터가 이해하기 위해
227 % 2 = 113 ... 1
113 % 2 = 56 ... 1
56 % 2 = 28 ... 0
28 % 2 = 14 ... 0
14 % 2 = 7 ... 0
7 % 2 = 3 ... 1
3 % 2 = 1 ... 1
1 % 2 = 0 ... 1
나머지 아래부터 위로 읽기 = 11100011
맨 앞이 1이면 음수 0이면 양수 = 11100011은  음수 -
값을 구하기위해선
1. 11100011 비트 반전 = 00011100
2. 00011100 + 1 = 00011101
3. 00011101 → 29
그래서 결과적으로 -29
```
- System.out.println((int)2.9 + 1.8); = 3.8 해설
```
(int)2.9 + 1.8
2.9를 정수형으로 강제 변환 = 2
2 + 1.8 = 3.8
그래서 결과적으로 3.8
```
- System.out.println((int)(2.9 + 1.8)); = 4 해설
```
(int)(2.9 + 1.8)
(int)4.7
4.7을 정수형으로 강제 변환  = 4
그래서 결과적으로 4
```
- System.out.println((int)2.9 + (int)1.8); = 3 해설
```
(int)2.9 + (int)1.8
2.9, 1.8 정수로 강제 변환
→ 2, 1
2 + 1 = 3
그래서 결과적으로 3
```

### 자바에서의 키 입력
- System.in
  - in = 키보드, 마우스
  - 키보드로부터 직접 읽는 자바의 표준 입력 스트림
  - 키 값은 바이트로 리턴
```
'a', '?', 'b' → System.in |0|1|1|1|0|1|0|0|1|0|1| → 자바 응용프로그램
```

##### ✍️ 작성자: 박지안
##### 🐧 실습 환경: Eclipse
##### 🗓️ 작업일: 2026-03-24
