# ☕ Java Programming Study

## 📘 1장 - 자바의 특징

### ⭐ 객체지향 프로그래밍 (OOP)
- 상속, 다형성, 캡슐화
- 클래스를 통해 캡슐화
- 클래스 내부에 변수와 메소드 구현
- 구조  
  👉 `Class = (변수 + 메소드)`

---

### 📂 소스(.java) vs 클래스(.class)
- 하나의 `.java` 파일에 여러 클래스 작성 가능
- ❗ **public 클래스는 단 하나만 가능**
- ❗ 파일 이름 = public 클래스 이름

---

### 💡 컴파일 결과
- 각 클래스마다 `.class` 파일 생성됨

#### 예시
```java
public class A {
    // code
}
class B {
    // code
}
class C {
    // code
}

👉 결과

A.class

B.class

C.class

⚡ 자바의 특징 - 멀티스레드

하나의 프로그램에서 여러 작업 동시 처리 가능

자바는 자체적으로 멀티스레드 지원

(C/C++은 OS API 필요)

📘 2장 - 자바 기본 구조
🧩 예제 코드
/*
 * 소스 파일 : Hello.java
 */
public class Hello20230844 {

    public static int sum(int n, int m) {
        return n + m;
    }

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
✅ 실행 결과
?
Hello
30
🔍 코드 핵심 정리
📌 클래스

class 키워드로 선언

{} 내부에 코드 작성

public → 다른 클래스에서 접근 가능

📌 main() 메소드

프로그램 시작 지점

public static void main(String[] args)
📌 메소드

C/C++의 함수와 동일 개념

클래스 내부에만 작성 가능

public static int sum(int n, int m)
📌 메소드 호출
int i = 20;
s = sum(i, 10);

👉 결과: 30

📌 변수
int i = 20;
char a;

메소드 내부 변수 = 지역 변수

❗ 메소드 종료 시 자동 소멸

📌 출력
System.out.println("Hello");

출력 후 줄바꿈

🧠 식별자 (Identifier)

👉 클래스, 변수, 메소드 이름

✔ 규칙

특수문자 사용 불가 (_, $ 제외)

숫자로 시작 불가

키워드 사용 불가

대소문자 구분

한글 사용 가능 (권장 X)

🔑 자바 키워드
abstract, continue, float, native, strictfp, void  
assert, default, for, new, super, volatile  
boolean, do, if, package, switch, while  
break, double, implements, private, synchronized  
byte, else, import, protected, this  
case, enum, instanceof, public, throw  
catch, extends, int, return, throws  
char, final, interface, short, transient  
class, finally, long, static, try
✨ 네이밍 규칙 (Camel Case)
📌 클래스
HelloWorld
AutoVendingMachine
📌 변수 / 메소드
int myAge;
boolean isSingle;

public int getAge() {}
📌 상수
final static double PI = 3.14;
🚀 핵심 한 줄 정리

자바는 객체지향 기반 언어

모든 코드는 클래스 안에 작성

프로그램은 main()에서 시작

메소드 = 함수

지역 변수는 실행 끝나면 소멸

📝 Info

✍️ 작성자: 박지안
🐧 실습 환경: Eclipse
🗓️ 작업일: 2026-03-17
