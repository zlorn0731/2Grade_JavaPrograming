# ☕ Java Programming Study

## 📘 1장 - 자바의 기본 프로그래밍

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
