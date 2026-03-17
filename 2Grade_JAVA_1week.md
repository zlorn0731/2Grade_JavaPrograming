☕ 자바 프로그래밍 1장
# 자바의 특징(1)
## ★ 객체지향 : 상속, 다형성, 캡슐화
- 클래스로 캡슐화 
- 클래스로 캡슐화
- 클래스 내에 변수, 메소드를 구현해야 함.
-- (CLASS (변수, 메소드)) --> 함수를 메소드로 칭함.

## 소스(.java)와 클래스(.class) 파일
- 하나의 소스 파일에 여러 클래스 작성 가능.
★ public 클래스는 하나만 가능
-- 소스 파일의 이름과 public으로 선언된 클래스 이름은 동일해야 함.

## 컴파일된 클래스 파일(.class)에는 클래스는 하나만 존재.
- 클래스마다 별도 클래스 파일(.class) 생성.

### (예시)
A.java
```
public class A {
// code
}
class B {
// code
}
class C {
// code
}
```
### 위 코드와 같이 class 작성이 있으면 (.class)파일 여러개 생김.
### 컴파일은 자동으로 되는 것이 자바의 장점 중 하나.

# 자바의 특징(2)
- 멀티스레드
- 자바는 운영체제의 도움 없이 자체적으로 멀티스레드 지원. // 반면 C/C++ 등에서는 멀티스레드 운영체제 API를 호출.
-- 멀티스레드란? : 하나의 프로그램에서 여러 작업을 동시 처리 가능.

☕ 자바 프로그래밍 2장

# 예제 2-1 자바프로그래밍의 기본 구조
```
/*
 * 소스 파일 : Hello.java
 */
public class Hello20230844 { // main class 이름
	public static int sum(int n, int m) {
		return n + m;
	}

// main() 메소드에서 실행 시작
public static void main(String[] args) { 
	int i = 20;
	int s;
	char a;
	
	s = sum(i, 10);
	a = '?';
	System.out.println(a);
	System.out.println("Hello");
	System.out.println(s);
    }
}
```
##결과
```
?
Hello
30
```

## 예제 2-1 코드 설명
### 클래스 만들기
--- Hello20230844 이름의 클래스 선언
```
public class Hello20230844 {
}
```
--- class 키워드로 클래스 선언
--- public 선언하면 다른 클래스에서 접근 가능
--- 클래스 코드는 {} 내에 모두 작성

### 주석문
--- // 한 라인 주석
--- /* 여러 행 주석 */

### main() 메소드
--- 자바 프로그램은 main()에서 실행 시작
```
public static void main(String[] args) {
}
```
### public static void으로 선언
### String[] args로 실행 인자를 전달 받음
### eclipse 꿀팁 : class 만들 때 체크박스 체크 시 자동으로 만들어짐 

### 메소드
--- C/C++에서의 함수를 메소드로 지칭
```
public static int sum(int n, int m) {
     //code
}
```
--- 클래스 바깥에 작성할 수 없음

### 메소드 호출
--- sum() 메소드 호출
```
int i = 20;
s = sum(i, 10);
```
--- sum() 호출 시 변수 i의 값과 정수 10을 전달
--- sum()의 n, m에 각각 20, 10 값 전달
--- sum()은 n과 m 값을 더한 30 리턴
--- 변수 s는 정수 30을 전달받음

### 변수 선언
--- 변수 타입과 변수 이름 선언
```
int i = 20;
char a;
```
--- 메소드 내에서 선언된 변수는 지역 변수
---- 지역 변수는 메소드 실행이 끝나면 자동 소멸

### 문장
--- ;로 한 문장의 끝을 인식.
```
int i = 20;
s = sum(i, 20);
```

### 화면 출력
--- 표준 출력 스트림에 메시지 출력.
```
System.out.println("Hello"); // "Hello" 화면 출력
```
--- 표준 출력 스트림 System.out의 println() 메소드 호출.
--- println()은 여러 타입의 데이터 출력 가능.
--- println()은 출력 후 다음 행으로 커서 이동.

## 식별자(identifier)
--- 식별자란? : 클래스, 변수(상수), 메소드 등에 붙이는 이름.
--- 식별자의 원칙
```
특수문자, 공백, 탭은 식별자로 사용 불가능.
'_', '$'는 사용 가능 // 첫 번째 문자로 사용 가능하나 잘 사용 하지 않음.
유니코드 문자 사용 가능, 한글 사용 가능.
키워드는 사용 불가능.
첫 번째 문자로 숫자는 사용불가.
boolean 리터널(true, false)와 null 리터널(null) 사용 불가
길이 제한 없음
대소문자 구별 // Test, test는 별개의 식별자
```
## 자바 키워드
```
abstract | continue | float      | native    | strictfp     | void     |  
assert   | default  | for        | new       | super        | volatile | 
boolean  | do       | if         | package   | switch       | while    |
break    | double   | implements | private   | synchronized |
byte     | else     | import     | protected | this         |
case     | enum     | instanceof | public    | throw        |
catch    | extends  | int        | return    | throws       |
char     | final    | interface  | short     | transient    |
class    | finally  | long       | static    | try          |
```

### 좋은 이름 붙이는 언어 관습
-- 기본 : 가독성 높은 이름
--- 목적을 나타내는 이름 붙이기 : S 보다 SUM.
--- 충분히 긴 이름으로 붙이기 : AVM 보다 AutoVendingMachine.

### 자바 언어의 이름 붙이는 관습 : 카멜(Camel) 표기법. ex) AutoVendingMachine

### 클래스 이름
--- 첫 번째 문자는 대문자로 시작
```
public class HelloWorld {}
class AutoVendingMachine [}
```

### 변수, 메소드 이름
--- 첫 번째 문자는 소문자로 시작
```
int myAge;
boolean isSingle;
public int getAge() {}
```

-- 상수 이름
--- 모든 문자를 대문자로 표시
```
final static double PI = 3.14;
```

####✍️작성자: 박지안  
####🐧실습 환경: eclipse 
####🗓️ 작업일: 2026-03-17
