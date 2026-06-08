# ☕ Java Programming Study
## 📘 4장 - 클래스, 객체

### 세상 모든 것이 객체
- 실세계 객체의 특징
  - 객체마다 고유한 특성(State)와 행동(Behavior)를 가짐
  - 다른 객체들과 정보를 주고 받는 등, 상호작용하면서 존재
- 컴퓨터 프로그램에서 객체 사례
  - 테트리스 게임의 각 블록들
  - 한글 프로그램의 메뉴나 버튼들
 
### 객체 지향 특성 : 캡슐화
- 캡슐화 : 객체를 캡슐로 싸서 내부를 볼 수 없게 하는 것
  - 객체의 본질적인 특징
    - 외부의 접근으로부터 객체 보호
   
#### 자바의 캡슐화
- 클래스(class) : 객체 모양을 선언한 틀(캡슐화)
  - 메소드(멤버 함수)와 필드(멤버 변수)는 모두 클래스 내에 구현
- 객체(object)
  - 클래스의 모양대로 생성된 실체(instance)
  - 객체 내 데이터에 대한 보호, 외부 접근 제한
  - object = instance
  ```
  Class class = new Class();
          ↳인스턴스
  ```

### 객체 지향 특성 : 상속
- 상속
  - 상위 개체의 속성이 하위 개체에 물려짐
  - 하위 객체가 상위 개체의 속성을 모두 가지는 관계
- 실세계의 상속 사례
  - 유전적 상속 관계
    - 나무는 식물의 속성과 생물의 속성을 모두 가짐
    - 사람은 생물의 속성은 가지지만 식물의 속성은 가지고 있지 않음

#### 자바의 상속
- 자식 클래스가 부모 클래스의 속성 물려받고, 기능 확장
  - 부모 클래스 : 수퍼 클래스
  - 하위 클래스 : 서브 클래스, 수퍼 클래스를 재사용하고 새로운 특성 추가

### 객체 지향 특성 : 다형성
- 다형성
  - 같은 이름의 메소드가 클래스나 객체에 따라 다르게 동작하도록 구현
- 다형성 사례
  - 메소드 오버로딩 : 같은 이름이지만 다르게 작동하는 여러 메소드
  - 메소드 오버라이딩 : 슈퍼클래스의 메소드를 서브 클래스마다 다르게 구현

### 객체 지향 언어의 목적
- 소프트웨어 생산성 향상
- 실세계에 대한 쉬운 모델링

### 절차 지향 프로그래밍과 객체 지향 프로그래밍
- 절차 지향 프로그래밍
  - 작업 순서 표현
  - 작업을 함수로 작성한, 함수들의 집합
- 객체 지향 프로그래밍
  - 객체들간의 상호 작용으로 표현
  - 클래스 혹은 객체들의 집합으로 프로그램 작성

### 클래스와 객체
- 클래스
  - 객체를 만들어내기 위한 설계도 혹은 틀
  - 객체의 속성(state)과 행동(behavior) 포함
- 객체
  - 클래스의 모양 그대로 찍어낸 실체
    - 프로그램 실행 중에 생성되는 실체
    - 메모리 공간을 갖는 구체적인 실체
    - 인스턴스(instance)라고도 부름

### 클래스 구성
```
public class Circle {
    public int radius; // 원의 반지름 필드
    public String name; // 원의 이름 필드

    public Circle() { // 원의 생성자 메서드
    }
    public double getArea() { // 원의 면적 계산 메서드
        return 3.14 * radius * radius;
    }
}
```
- 클래스 구성 설명
  - 클래스 선언, class Circle
    - class 키워드로 선언
    - 클래스는 {로 시작하여 }로 닫으며 이곳에 모든 필드와 메서드 구현
    - class Circle은 Circle 이름의 클래스 선언
    - 클래스 접근 권한, public
      - 다른 클래스들에서 Circle클래스를 사용하거나 접근할 수 있음을 선언
  - 필드와 메서드
    - 필드(field) : 객체 내의 값을 저장하는 멤버 변수
    - 메서드(method) : 함수이며 객체의 행동(행위)를 구현
  - 필드의 접근 지정자, public
    - 필드와 메서드 앞에 붙어 다른 클래스의 접근 허용을 표시
    - public 접근 지정자 : 다른 모든 클래스의 접근 허용
  - 생성자
    - 클래스의 이름과 동일한 특별한 메서드
    - 객체가 생성될 때 자동으로 한 번 호출되는 메서드
    - 개발자는 객체를 초기화하는데 필요한 코드 작성

### 객체 생성 및 접근
- 객체 생성
  - 반드시 new 키워드를 이용하여 생성
    - new는 객체의 생성자 호출
- 객체 생성 과정
  - 객체에 대한 레퍼런스 변수 선언
  - 객체 생성
    - 클래스 타입 크기의 메모리 할당
    - 객체 내 생성자 코드 실행
- 객체의 멤버 접근
  - 객체 레퍼런스.멤버
 
#### 객체 생성과 접근 코드 설명
- 1. 레퍼런스 변수 선언
  ```
  Circle pizza;
  ```
- 2. 객체 생성 : new 연산자 이용
  ```
  pizza = new Circle();
  ```
- 3. 객체 멤버 접근 : 점(.) 연산자 이용
  ```
  pizza.radius = 10;
  pizza.name = "자바피자";
  double area = pizza.getArea();
  ```

#### 예제 4-1 : Circle 클래스의 객체 생성 및 활용
- 반지름과 이름을 가진 Circle 클래스를 작성하고, Circle 클래스의 객체를 생성하라. 그리고 객체가 생성된 모습을 그려보라.
```
package FourJang;

public class Circle {
	int radius; // 원의 반지름 필드
	String name; // 원의 이름 필드
	
	public Circle() {} // 원의 생성자
	
	public double getArea() { // 원의 면적 계산 메서드
		return 3.14*radius*radius;
	}
	public static void main(String[] args) {
		Circle pizza;
		pizza = new Circle(); // Circle 객체 생성
		pizza.radius = 10; // 피자의 반지름을 10으로 설정
		pizza.name = "자바피자"; // 피자의 이름 설정
		double area = pizza.getArea(); // 피자의 면적 알아내기
		System.out.println(pizza.name + "의 면적은 " + area);
		
		Circle donut = new Circle(); // Circle 객체 생성
		donut.radius = 2; // 도넛의 반지름을 2로 설정
		donut.name = "자바도넛"; // 도넛의 이름 설정
		area = donut.getArea(); // 도넛의 면적 알아내기
		System.out.println(donut.name + "의 면적은 " + area);
	}
}

- 결과
자바피자의 면적은 314.0
자바도넛의 면적은 12.56
```

#### 예제 4-2 : Rectangle 클래스 만들기 연습
- 너비와 높이를 입력 받아 사각형의 합을 출력하는 프로그램을 작성하라. 너비(weight)와 높이(height) 필드, 그리고 면적 값을 제공하는 getArea() 메서드를 가진 Rectangle 클래스를 만들어 활용하라.
```
package FourJang;

import java.util.Scanner;

public class Rectangle {
	int width;
	int height;
	
	public int getArea() {
		return width*height;
	}
	
	public static void main(String[] args) {
		Rectangle rect = new Rectangle();
		Scanner scanner = new Scanner(System.in);
		System.out.print(">> ");
		
		rect.width = scanner.nextInt();
		rect.height = scanner.nextInt();
		
		System.out.println("사각형의 면적은 " + rect.getArea());
		
		scanner.close();
	}

}

- 결과
>> 4 3
사각형의 면적은 12
```

#### 예제 4-3 : 두 개의 생성자를 가진 Circle 클래스
- 다음 코드는 2개의 생성자를 가진 Circle 클래스이다. 실행 결과는 무엇인가?
```
public class Circle {
	int radius;
	String name;

	// 생성자 이름은 클래스 이름과 동일
	public Circle() { // 매개 변수 없는 생성자
		radius = 1; name = ""; // radius의 초기값은 1
	}

 	// 생성자는 리턴 타입 없음
	public Circle(int r, String n) { // 매개 변수를 가진 생성자
		radius = r; name = n;
	}

	public double getArea() {
		return 3.14 * radius * radius;
	}

	public static void main(String[] args) {
		Circle pizza = new Circle(10, "자바피자"); // Circle 객체 생성, 반지름 10

		double area = pizza.getArea();
		System.out.println(pizza.name + "의 면적은" + area);

		Circle donut = new Circle(); // Circle 객체 생성, 반지름 1
		donut.name = "도넛피자";
		area = donut.getArea();
		System.out.println(donut.name + "의 면적은" + area);
	}
}
```

### 생성자의 특징
- 생성자는 메소드
- 생성자 이름은 클래스 이름과 반드시 동일
- 생성자 여러 개 작성 가능(오버로딩)
- 생성자는 new를 통해 객체를 생성할 때, 객체당 한 번 호출
- 생성자는 리턴 타입을 지정할 수 없음
- 생성자의 목적은 객체 초기화
- 생성자는 객체가 생성될 때 반드시 호출됨
  - 그러므로 하나 이상 선언되어야 함
    - 개발자가 생성자를 작성하지 않았으면 컴파일러가 자동으로 기본 생성자 삽입

#### 예제 4-4 : 생성자 선언 및 활용 연습
- 제목과 저자를 나타내라 title과 author 필드를 가진 Book 클래스를 작성하고, 생성자를 작성하여 필드를 초기화하라
```
public class Book {
	String title;
	String author;

	public Book(String t) { // 생성자
		title = t; author = "작자미상";
	}

	public Book(String t, String a) {
		title = t; author = a;
	}

	public static void main(String[] args) {
		Book littlePrince = new Book("어린왕자", "생텍쥐페리");
		Book loveStory = new Book("춘향전");
		System.out.println(littlePrince.title + " " + littlePrince.author);
		System.out.println(loveStory.title + " " + loveStory.author);
	}
}
```

### 기본 생성자
- 기본 생성자(default constructor)
  - 매개 변수 없고 아무 작업 없이 단순 리턴하는 생성자
  - 디폴트 생성자라고도 부름
- 클래스에 생성자가 하나도 선언되지 않은 경우, 컴파일러에 의해 자동으로 삽입
```
[개발자가 작성한 코드]

public class Circle() {
	int radius;
	void set(int r) { radius = r; }
	double getArea() { return 3.14 * radius * radius; }

	public static void main(String[] args) {
		Circle pizza = new Circle();
		pizza.set(3);
	}
}

이 코드에는 생성자가 없지만 컴파일 오류가 생기지 않음
```
```
[이유]

public class Circle() {
	int radius;
	void set(int r) { radius = r; }
	double getArea() { return 3.14 * radius * radius; }

	public Circle() {} // 컴파일러에 의해 자동 삽입된 기본 생성자

	public static void main(String[] args) {
		Circle pizza = new Circle();
		pizza.set(3);
	}
}

컴파일러가 자동으로 기본 생성자 삽입
```

### 기본 생성자가 자동 생성되지 않는 경우
- 개발자 클래스에 생성자가 하나라도 작성한 경우
  - 기본 생성자 자동 삽입되지 않음
```
public class Circle() {
	int radius;
	void set(int r) { radius = r; }
	double getArea() { return 3.14 * radius * radius; }

	// 컴파일러가 기본 생성자를 자동 생성하지 않음 | public Circle() {} |
	public Circle(int r) {
		radius = r;
	}

	public static void main(String[] args) {
		Circle pizza = new Circle(10);
		System.out.println(pizza.getArea());

		Circle donut = new Circle(); // 컴파일 오류, 해당하는 생성자가 없음
		System.out.println(donut.getArea());
	}
}
```

### this 레퍼런스
- this
  - 객체 자신에 대한 레퍼런스
    - 컴파일러에 의해 자동 관리, 개발자는 사용하기만 하면 됨
    - this.멤버 형태로 멤버 사용
```
public class Circle() {
	int radius;

	public Circle() { radius = 1; }
	public Circle(int r) { radius = r; }
	double getArea() {
		return 3.14 * radius * radius;
	}
	....
}

=

public class Circle() {
	int radius;

	public Circle() { this.radius = 1; }
	public Circle(int radius) {
		this.radius = radius;
	}
	double getArea() {
		return 3.14 * this.radius * this.radius;
	}
	...
}

this를 사용하여 수정한 경우
```

### this가 필요한 경우
- this의 필요성
  - 객체의 멤버 변수와 메소드 변수의 이름이 같은 경우
  - 다른 메소드 호출 시 객체 자신의 레퍼런스를 전달할 때
  - 메소드가 객체 자신의 레퍼런스를 반환할 때

### 객체 속에서의 this
```
public class Circle() {
	int radius;
	public Circle(int radius) {
		this.radius = radius;
	}
	public void set(int radius) {
		this.radius = radius;
	}

	public static void main(String[] args) {
		Circle ob1 = new Circle(1);
		Circle ob2 = new Circle(2);
		Circle ob3 = new Circle(3);

		ob1.set(4); // radius(1) → radius(4)
		ob2.set(5); // radius(2) → radius(5)
		ob3.set(6); // radius(3) → radius(6)
	}
}
```

### this()로 다른 생성자 호출
- this()
  - 클래스 내의 다른 생성자 호출
  - 생성자 내에서만 사용 가능
  - 반드시 생성자 코드의 제일 처음에 수행
 
### this() 사용 실패 예
```
public Book() {
	System.out.println("생성자가 호출되었음");
	this(null, null, 0); // 생성자의 첫 번째 문장이 아니기 때문에 컴파일 오류
}
```

#### 예제 4-5 : this()로 다른 생성자 호출
- 예제 4-4에서 작성한 Book 클래스의 생성자를 this()를 이용하여 수정하라
```
public class Book {
	String title;
	String author;
	void show() { System.out.println(title + " " + author); }

	public Book(String title) {
		this(title, "작자미상");
	}

	public Book(String title, String author) {
		this.title = title; this.author = author;
	}

	public static void main(String[] args) {
		Book littlePrince = new Book("어린왕자", "생텍쥐페리");
		Book loveStory = new Book("춘향전");
		Book emptyBook = new Book();
		loveStory.show();
	}
}
```

### 객체의 치환
- 객체의 치환은 객체가 복사되는 것이 아니며 레퍼런스가 복사된다
```
public class Circle() {
	int radius;
	public Circle(int radius) { this.radius = radius; }
	public void set(int radius) { this.radius = radius; }

	public static void main(String[] args) {
		Circle ob1 = new Circle(1);
		Circle ob2 = new Circle(2);
		Circle s;

		s = ob2;
		ob1 = ob2; // 객체 치환
		System.out.println("ob1.radius = " + ob1.radius);
		System.out.println("ob2.radius = " + ob2.radius);
	}
}

-------------------------------------------------------------

ob1 → radius(1) → radius(2) // ob1은 쓰레기값
ob2 → radius(2)
s → radius(2)
```

### 객체 배열
- 객체 배열 생성 및 사용
```
Circle [] c; // Circle 배열에 대한 레퍼런스 변수 c 선언 
c = new Circle[5]; // 레퍼런스 배열 생성

for(int i = 0; i < c.length; i++) // c.length는 배열 c의 크기로서 5
	c[i] = new Circle(i); // 배열의 각 원소 객체 생성
```
```
for(int i = 0; i < c.length; i++) // 배열에 있는 모든 Circle 객체의 면적 출력
	System.out.print((int)(c[i].getArea()) + " "); // c[i].getArea() 배열의 원소 객체 사용
```

### 객체 배열 선언과 생성 과정
```
| Circle[] c; |

    c [ O ]
```
```
| c = new Circle[5]; |

   c [ O ] ↴
     c[0] | O |
     c[1] | O |
     c[2] | O |
     c[3] | O |
     c[4] | O |
```
```
for (int i = 0; i < c.length; i++)
		c[i] = new Circle(i);

   c [ O ] ↴      Circle 객체
     c[0] | O |→| radius = 0 |
     c[1] | O |→| radius = 1 |
     c[2] | O |→| radius = 2 |
     c[3] | O |→| radius = 3 |
     c[4] | O |→| radius = 4 |
```

#### 예제 4-6 : Circle 객체 배열 만들기
- 반지름이 0~4인 Circle 객체 5개를 가지는 배열을 생성하고, 배열에 있는 모든 Circle 객체의 면적을 출력하라
```
class Circle {
	int radius;
	public Circle(int radius) {
		this.radius = radius;
	}
	public double getArea() {
		return 3.14 * radius * radius;
	}
}

public class CircleArray {
	public static void main(String[] args) {
		Circle[] c;
		c = new Circle[5];

		for (int i = 0; i < c.length; i++)
			c[i] = new Circle(i);

		for (int i = 0; i < c.length; i++)
			System.out.print((int)(c[i].getArea()) + " ");
	}
}
```

#### 예제 4-7 : 객체 배열 만들기 연습
- 예제 4-4의 Book 클래스를 활용하여 2개짜리 Book 객체 배열을 만들고, 사용자로부터 책의 제목과 저자를 입력 받아 배열을 완성하라
```
import java.util.Scanner;
class Book {
	String title, author;
	public Book(String title, String author) {
		this.title = title;
		this.author = author;
	}
}

public class BookArray {
	public static void main(String[] args) {
		Book[] book = new Book[2]; // Book 배열 선언

		Scanner scanner =new Scanner(System.in);
		for(int i = 0; i < book.length; i++) {
			System.out.print("제목>>");
			System title = scanner.nextLine();
			System.out.print("저자>>");
			String author = scanner.nextLine();
			book[i] = new Book(title, author); // 배열 원소 객체 생성
		}

		for(int i = 0; i < book.length; i++)
			System.out.print("(" + book[i].title + ", " + book[i].author + ")");

		scanner.close();
		}
}
```

### 메소드 형식
- 메소드
  - 클래스의 멤버 함수, C/C++의 함수와 동일
  - 자바의 모든 메소드는 반드시 클래스 안에 있어야 함(캡슐화 원칙)
- 메소드 구성 형시
  - 접근 지정자
    - public, private, protected, 디폴트(접근 지정자 생략된 경우)
  - 리턴 타입
    - 메소드가 반환하는 값의 데이터 타입
```
public int getSum(int i, int j) {
	int sum;
	sum = i + j;
	return sum;
}

public = 접근 지정자
int = 리턴 타입
getSum = 메소드 이름
int i, in j = 메소드 인자들

메소드 코드
int sum;
sum = i + j;
return sum;
```

### 인자 전달
- 자바의 인자 전달 방식
  - 경우 1. 기본 타입의 값 전달
    - 값이 복사되어 전달
    - 메소드의 매개변수가 변경되어도 호출한 실인자 값은 변경되지 않음
  - 경우 2. 객체 혹은 배열 전달
    - 객체나 배열의 레퍼런스만 전달
      - 객체 혹은 배열이 통째로 복사되어 전달되는 것이 아님
    - 메소드의 매개변수와 호출한 실인자 객체나 배열 공유

#### 인자 전달 - 기본 타입의 값이 전달되는 경우
- 매개변수가 byte, int, double 등 기본 타입의 값일 때
  - 호출자가 건네는 값이 매개변수에 복사되어 전달. 실인자 값은 변경되지 않음
```
public class ValuePassing {
	public static void main(String args[]) {
		int n = 10;

		increase(n);

		System.out.println(n);
	}

    	호출 ↓

static void increase(int m) {
	m = m + 1;
	}
}
```
```
main() 실행 시작

int n = 10;				n[10]
----------------------------------------------------------------------
                                              increase(int m) 실행 시작
increase(n);			n[10] ------------→ [10]m 
						n[10]				[11]m	m = m + 1;
                                              increase(int m) 종료
----------------------------------------------------------------------
System.out.println(n);	n[10]
```

#### 인자 전달 - 객체가 전달되는 경우
- 객체의 레퍼런스만 전달
  - 매개 변수가 실인자 객체 공유
```
public class RefrencePassing {
	public static void main(String args[]) {
		Circle pizza = new Circle(10);

		increase(pizza);

		System.out.println(pizza.radius);
	}

    	호출 ↓

static void increase(Circle m) {
	m.radius++;
	}

}
```
```
main() 실행 시작

pizza = new Circle(10);		pizzza[ ]→radius [10]
----------------------------------------------------------------------
                                              increase(Circle m) 실행 시작
                                    레퍼런스 복사
increase(pizza);			pizza[ ]→radius [10]←[ ]m

							pizza[ ]→radius [11]←[ ]m		m.radius++;
                                              increase(Circle m) 종료
----------------------------------------------------------------------
System.out.println(pizza.radius);
							pizza[ ]→radius [11]
```

#### 인자 전달 - 배열이 전달되는 경우
- 배열 레퍼런스만 매개 변수에 전달
  - 배열 통째로 전달되지 않음
  - 객체가 전달되는 경우와 동일
  - 매개변수가 실인자의 배열을 공유
```
public class ArrayPassing {

	public staitc void main(String args[]) {
		int a[] = {1, 2, 3, 4, 5};

		increase(a);

		for(int i = 0; i < a.length; i++)
			System.out.print(a[i] + " ");
	}

  → 레퍼런스 복사 →
 a           array
[ ]           [ ]
 ↘           ↙
     [  2  ]  1에서 바뀜
     [  3  ]  2에서 바뀜
     [  4  ]  3에서 바뀜
     [  5  ]  4에서 바뀜
     [  6  ]  5에서 바뀜

static void increase(int[] array) {
	for(int i = 0; i < array.length; i++) {
		array[i]++;
	}
  }
}
```

#### 예제 4-8 : 인자로 배열이 전달되는 예
- char[] 배열을 전달받아 출력하는 printCharArray() 메소드와 배열 속의 공백 (' ') 문자를 ','로 대치하는 replaceSpace() 메소드를 출력하라
```
public class ArrayParmeterEx {
	staic void replaceSpace(char a[]) {
		for(int i = 0; i < a.length; i++)
			if(a[i] == ' ')
			a[i] = ',';
	}
	static void printCharArray(char a[]) {
		for(int i = 0; i < a.length; i++)
			System.out.print(a[i]);
		System.out.println();
	}
	public static void main(String args[]) {
		char c[] = {'T', 'h', 'i', 's', ' ', 'a', ' ', 'p', 'e', 'n', 'c', 'i', 'l', '.'};
		printCharArray(c);
		replaceSpace(c);
		printCharArray(c);
	}
}
```
```
 [ ] a		replaceSpace(char a[])
  |
  |
  |
  |
  ↓             ,↓          ,↓      ,↓ 
| T | h | i | s |  | i | s |   | a |   | p | e | n | c | i | l | . |
  ↑
 [ ] c
```

### 메소드 오버로딩
- 메소드 오버로딩(Overloading)
  - 이름이 같은 메소드 작성, 다음 2개의 조건
    - 매개변수의 개수나 타입이 서로 다르고
    - 이름이 동일한 메소드들
  - 리턴 타입은 오버로딩과 관련 없음
    - 오버로딩의 성공 여부를 따질 때 리턴 타입은 고려하지 않음
```
// 메소드 오버로딩이 성공한 사례

class MethodOverloading {
	public int getSUm(int i, int j) {
		return i + j;
	}
	public int getSum(int i, int j, int k) {
		return i + j + k;
	}
}
```
```
// 메소드 오버로딩이 실패한 사례

class MethodOverloadingFail {
	public int getSum(int i, int j) {
		return i + j;
	}
	public double getSum(int i, int j) {
		return (double(i + j);
	}
}

두 개의 getSum() 메소드는 매개변수의 개수, 타입이 모두 같기 때문에 메소드 오버로딩 실패
```

### 오버로딩된 메소드 호출
```
public static void main(String args[]) {
	MethodSample a = new MethodSample();

	int i = a.getSum(1, 2);

	int j = a.getSum(1, 2, 3);

	double k = a.getSum(1.1, 2.2);
}

매개 변수의 개수와 타입이 서로 다른 3 함수 호출
```
```
public class MethodSample {
	public int getSum(int i, int j) {
		return i + j;
	}

	public int getSum(int i, int j, int k) {
		return i + j + k;
	}

	public double getSum(double i, double j) {
		return i + j;
	}
}
```

### 객체의 소멸과 가비지 컬렉션
- 객체 소멸
  - new에 의해 할당된 객체 메모리를 자바 가상 기계의 가용 메모리로 되돌려 주는 행위
- 자바 응용프로그램에서 임의로 객체 소멸할 수 없음
  - 객체 소멸은 자바 가상 기계의 고유한 역할
  - 자바 개발자에게는 매우 다행스러운 기능
    - C/C++에서는 할당받은 객체를 개발자가 되돌려 주어야 함
      - C/C++ 프로그램 작성을 어렵게 만드는 요인
- 가비지
  - 자신을 가리키는 레퍼런스가 하나도 없는 객체
    - 프로그램에서 사용할 수 없게 된 메모리
- 가비지 컬렉션
  - 자바 가상 기계의 가비지 컬렉터가 자동으로 가비지 수집 반환

### 가비지 사례
```
Person a, b;
a = new Person("이몽룡");
b = new Person("성춘향");
b = a; // b가 가리키던 객체는 가비지가 됨
```
```
        Person 객체
a [   ]→["이몽룡"]
      ↗
b [   ]↛ ["성춘향"]
            ↑가비지 객체
```

#### 예제 4-9 : 가비지의 발생
- 다음 코드에서 언제 가비지가 발생하는지 설명하라
```
public class GarbageEx {
	public static void main(String[] args) {
		String a = new String("Good");
		String b = new String("Bad");
		String c = new String("Normal");
		String d, e;
		a = null;
		d = c;
		c = null;
	}
}
```
```
a[   ]→["Good"]
b[   ]→["Bad"]
c[   ]→["Normal"]
d[   ]
e[   ]

(a) 초기 객체 생성 시(라인 6까지)
-----------------------------------
a[   ]		["Good"] ← 가비지
b[   ]→		["Bad"]
c[   ]      ["Normal"]
d[   ]↗
e[   ]

(b) 코드 전체 실행 후
```

### 가비지 컬렉션
- 가비지 컬렉션
  - 자바에서 가비지를 자동 회수하는 과정
    - 가용 메모리로 반환
  - 가비지 컬렉션 스레드에 의해 수행
  - 언제?
    - 아무도 모름. 가용 메모리 량이 일정 수준 이하로 떨어질 때
- 개발자에 의한 강제 가비지 컬렉션
  - System 또는 Runtime 객체의 gc() 메소드 호출
  ```
  System.gc(); // 가비지 컬렉션 작동 요청
  ```
    - 이 코드는 자바 가상 기계에 강력한 가비지 컬렉션 요쳥
      - 그러나 자바 가상 기계가 가비지 컬렉션 시점을 전적으로 판단

### 자바의 패키지 개념
- 패키지
  - 관련 있는 클래스 파일(컴파일된 .class)을 저장하는 디렉터리
  - 자바 응용프로그램은 하나 이상의 패키지로 구성
```
              - 자바 응용프로그램 -

  [패키지 A]        [패키지 B]        [패키지 C]
클래스 파일      |   클래스 파일    |  클래스 파일
     클래스 파일 |      클래스 파일 |      클래스 파일
 클래스 파일     |  클래스 파일     | 클래스 파일
```

### 접근 지정자
- 자바의 접근 지정자
  - 4가지
    - private, protected, public, 디폴트(접근 지정자 생략)
- 접근 지정자의 목적
  - 클래스나 일부 멤버를 공개하여 다른 클래스에서 접근하도록 허용
  - 객체 지향 언어의 캡슐화 정책은 멤버를 보호하는 것
    - 접근 지정은 캡슐화에 묶인 보호를 일부 해제할 목적
- 접근 지정자에 따른 클래스나 멤버의 공개 범위
```
      private     <       디폴트      <          protected            <     public
외부로부터 완벽차단 | 동일 패키지에 허용 | 동일 패키지와 자식 클래스에 허용 | 모든 클래스에 허용
------------------|-------------------|-------------------------------|------------------→
```

### 클래스 접근 지정
- 클래스 접근 지정
  - 다른 클래스에서 사용하도록 허용할 지 지정
  - public 클래스
    - 다른 모든 클래스에게 접근 허용
  ```
  public class World { // public 클래스
  .........
  }
  ```
  - 디폴트 클래스(접근지정자 생략)
    - package-private 라고도 함
    - 같은 패키지의 클래스에만 접근 허용
  ```
  class Local { // 디폴트 클래스
  .........
  }
  ```
```
[패키지 P]                |                                   [패키지 Q]
-------------------------------------------------------------------------------------------------------------------
                         |
class A {                |     public class B {         class C {                     class D {
	void f() {           |           ...                    void g() {                     void h() {
		B b = new B();   |     }                                 B b = new B();                 C c = new C();
		...              |                                  }                               }
		C c = new C();   |                               }                             }
	}                    |                         디폴트 클래스는 다른 패키지의 접근 불허
}                        |
-------------------------------------------------------------------------------------------------------------------
                                [public 클래스와 디폴트 클래스의 접근 사례]
```

### 멤버 접근 지정
- public 멤버
  - 패키지에 관계 없이 모든 클래스에게 접근 허용
- private 멤버
  - 동일 클래스 내에만 접근 허용
  - 상속 받은 서브 클래스에서 접근 불가
- protected 멤버
  - 같은 패키지 내의 다른 모든 클래스에게 접근 허용
  - 상속 받은 서브 클래스는 다른 패키지에 있어도 접근 가능
- 디폴트(default) 멤버
  - 같은 패키지 내의 다른 클래스에게 접근 허용
- 
| 멤버에 접근하는 클래스 | private | 디폴트 접근 지정 | protected | public |
|----------------------|---------|----------------|-----------|--------|
| 같은 패키지의 클래스 | ✕ | ○ | ○ | ○ |
| 다른 패키지의 클래스 | ✕ | ✕ | ✕ | ○ |
| 접근 가능 영역 | 클래스 내 | 동일 패키지 내 | 동일 패키지 및 자식 클래스 | 모든 클래스 |

### 멤버 접근 지정자의 이해
- public 접근 지정 사례
```
                                              [패키지 P]
class A {              | public class B {                class C {
	void f() {         |      public int n;					public void k() {
		B b = new B(); |      public void g() {					B b = new B();
		b.n = 3;       |		n = 5;								b.n = 7;
		b.g();         |      }										b.g();
	}                  | }									 }					
}                      |                                  }

b.n = 3; → public int n; ← b.n = 7;
b.g(); → public void g() { ← b.g();
```
- private 접근 지정 사례
```
                                              [패키지 P]
class A {              | public class B {                class C {
	void f() {         |      public int n;					public void k() {
		B b = new B(); |      public void g() {					B b = new B();
		b.n = 3;       |		n = 5;								b.n = 7;
		b.g();         |      }										b.g();
	}                  | }									 }					
}                      |                                  }

b.n = 3; ↛  public int n; ↚  b.n = 7;
b.g(); ↛  public void g() { ↚  b.g();
```
- 디폴트 접근 지정 사례
```
                                              [패키지 P]
class A {              | public class B {                class C {
	void f() {         |      public int n;					public void k() {
		B b = new B(); |      public void g() {					B b = new B();
		b.n = 3;       |		n = 5;								b.n = 7;
		b.g();         |      }										b.g();
	}                  | }									 }					
}                      |                                  }

b.n = 3; ↛  public int n; ← b.n = 7;
b.g(); ↛  public void g() { ← b.g();
```
- protected 접근 지정 사례
```
                                              [패키지 P]
class A {              | public class B {                class C {
	void f() {         |      public int n;					public void k() {
		B b = new B(); |      public void g() {					B b = new B();
		b.n = 3;       |		n = 5;								b.n = 7;
		b.g();         |      }										b.g();
	}                  | }									 }					
}                      |                                  }
                 D가 B를 상속받음 ↑
 
                class D extends B {
					void f() { // extends는 상속받음을 나타냄
						n = 3;
						g();
					}
				 }

b.n = 3; ↛  public int n; ← b.n = 7;, n = 3;
b.g(); ↛  public void g() { ← b.g();, g();
```

#### 예제 4-10 : 멤버의 접근 지정자
- 다음 코드의 두 클래스 Sample과 AccessEx 클래스는 동일한 패키지에 저장, 컴파일 오류를 찾아 내고 이유를 설명
```
class Sample {
	public int a;
	private int b;
	int c;
}

public class AccessEx {
	public static void main(String[] args) {
		Sample aClass = new Sample();
		aClass.a = 10;
		aClass.b = 10;
		aClass.c = 10;
	}
}
```
  - Sample 클래스의 a와 c는 각각 public, default 지정자로 선언이 되었으므로, 같은 패키지에 속한 AccessEx 클래스에서 접근 가능
  - b는 private으로 선언이 되었으므로 AccessEx 클래스에서 접근 불가능

### static 멤버와 non-static 멤버
- non-static 멤버의 특성
  - 공간적 특성 - 멤버들은 객체마다 독립적으로 별도 존재
    - 인스턴스 멤버라고도 부름
  - 시간적 특성 - 필드와 메소드는 객체 생성 후 비로소 사용 가능
  - 비공유 특성 - 멤버들은 다른 객체에 의해 공유되지 않고 배타적
- static 멤버란?
  - 객체마다 생기는 것이 아님
  - 클래스당 하나만 생성됨
    - 클래스 멤버라고도 부름
  - 객체를 생성하지 않고 사용가능
  - 특성
    - 공간적 특성 - staitc 멤버들은 클래스 당 하나만 생성
    - 시간적 특성 - static 멤버들은 클래스가 로딩될 때 공간 할당
    - 공유의 특성 - static 멤버들은 동일한 클래스의 모든 객체에 의해 공유
```
class StaticSample {
	int n; // non-static 필드
	void g() {...} // non-static 메소드

	static int m; // static 필드
	static void f() {...} // static 메소드
}
```

### non-static 멤버와 static 멤버의 차이
- 
| 구분 | non-static 멤버 | static 멤버 |
|------|----------------|-------------|
| 선언 | ```java<br>class Sample {<br>&nbsp;&nbsp;int n;<br>&nbsp;&nbsp;void g() { ... }<br>}<br>``` | ```java<br>class Sample {<br>&nbsp;&nbsp;static int m;<br>&nbsp;&nbsp;static void f() { ... }<br>}<br>``` |
| 공간적 특성 | 멤버는 객체마다 별도 존재<br>• 인스턴스 멤버라고 부름 | 멤버는 클래스당 하나 생성<br>• 객체 내부가 아닌 별도 공간(클래스 코드가 적재되는 메모리)에 생성<br>• 클래스 멤버라고 부름 |
| 시간적 특성 | 객체 생성 시에 멤버 생성됨<br>• 객체가 생길 때 멤버도 생성<br>• 객체 생성 후 멤버 사용 가능<br>• 객체가 사라지면 멤버도 사라짐 | 클래스 로딩 시에 멤버 생성<br>• 객체가 생기기 전에 이미 생성<br>• 객체가 생기기 전에도 사용 가능<br>• 객체가 사라져도 멤버는 사라지지 않음<br>• 프로그램이 종료될 때 사라짐 |
| 공유의 특성 | 공유되지 않음<br>• 멤버는 객체 내에 각각 공간 유지 | 동일한 클래스의 모든 객체에 의해 공유됨 |
