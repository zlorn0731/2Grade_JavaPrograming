# ☕ Java Programming Study
## 📘 5장 - 상속 pg23 부터

### 업캐스팅(upcasting)
- 서브 클래스의 객체는
  - 슈퍼 클래스의 멤버를 모두 가지고 있음
  - 슈퍼 클래스의 객체로 취급할 수 있음
    - '사람은 생물이다'의 논리와 같음
- 업캐스팅이란?
  - sub 클래스 객체를 super 클래스 타입으로 타입 변환
  ```
  class Person {...}
  class Student extends Person {...}

  Student s = new Student();
  Person p = s; // 업캐스팅, 자동타입변환
  ```
- 업캐스팅된 레퍼런스
  - 객체 내에 슈퍼 클래스의 멤버만 접근 가능

### 업캐스팅 사례
```
class Person {
  String name;
  String id;

  public Person(String name) {
    this.name = name;
  {
}

class Student extends Person {
  String grade;
  String department;

  public Student(String name) {
    super(name);
  }
}

public class UpcastingEx {
  public static void main(String[] args) {
    Person p;
    Student s = new Student("이재문");
    p = s; // 업캐스팅

    System.out.println(p.name); // 오류 없음

    // p.grade = "A"; // 컴파일 오류
    // p.department = "Com"; // 컴파일 오류
  }
}

[실행 결과]
이재문
```
```
Student s | . |      Person p | . |
            ↓                   ↓
           ----------------------
           | name       [이재문] |
           | id         [     ] |  레퍼런스 p를 이용하면 Student 객체의 멤버 중 
           | Person()           |  Person의 멤버만 접근 가능하다
           ----------------------
           | grade      [     ] |
           | department [     ] |
           | Student()          |
           ----------------------
            레퍼런스 s를 이용하면 위의 6개 멤버에 모두 접근 가능하다
```

### 다운캐스팅(downcasting)
- 다운캐스팅이란?
  - 슈퍼 클래스 객체를 서브 클래스 타입으로 변환
  - 개발자의 명시적 타입 변환 필요
  ```
  class Person {...}
  class Student extends Person {...}
  ...
  Person p = new Student("이재문"); // 업캐스팅
  ...
  Student s = (Student)p; // 다운캐스팅, (Student)의 타입 변환 표시 필요
  ```

### 다운캐스팅 사례
```
public class DowncastingEx {
  public static void main(String[] args) {
    Person p = new Student("이재문"); // 업캐스팅
    Student s;

    s = (Student)p; // 다운캐스팅

    System.out.println(s.name); // 오류 없음
    s.grade = "A"; // 오류 없음
  }
}

[실행 결과]
이재문
```
```
        s | . |             p | . |
            ↓                   ↓
           ----------------------
           | name       [이재문] |
           | id         [     ] |  
           | Person()           |  
           ----------------------
           | grade      [     ] |
           | department [     ] |
           | Student()          |
           ----------------------
```

### instanceof 연산자와 객체의 타입 판단
- 업캐스팅된 레퍼런스로 객체의 타입 판단 어려움
  - 슈퍼 클래스는 여러 서브 클래스에 상속되기 때문
    - (예시) '생물', 팻말(레퍼런스)이 가리키는 박스에 들어 있는 객체의 타입이 사람인지, 동물인지 팻말만 보고서는 알 수 없음
- instanceof 연산자
  - 레퍼런스가 가리키는 객체의 타입 식별을 위해 사용
  - 사용법
  ```
  | 객체레퍼런스 instanceof 클래스타입 |
    연산의 결과 : true / false의 불린 값
  ```

### 업캐스팅 레퍼런스가 가리키는 객체는?
- 1. 상속 관계에 있는 옆의 클래스 사례에서
```
                         class Person {  }
                                 ↑
            ↑-------------------→←---------------------↑
class Student extends Person {            class Researcher extends Person {
}                                         }
                                                       ↑
                                          class Professor extends Researcher {
                                          }
```
- 2. 다음과 같은 업캐스팅이 가능하므로
```
Person p = new Person();
Person p = new Student(); // 업캐스팅
Person p = new Researcher(); // 업캐스팅
Person p = new Professor(); // 업캐스팅
```
- 3. print(p);를 호출하면, print() 메소드에서 person이 어떤 객체를 가리키는지 알 수 없음
```
void print(Person person) {
  // person이 가리키는 객체가 Person 타입일 수도 있고,
  // Student, Researcher, 혹은 Professor 타입일 수도 있다
  ...
}
```

### Person타입의 레퍼런스 person이 어떤 타입의 객체를 가리키는지 알 수 없음
```
                                               void print(Person person) {
                                                      ... 
                                               }
                        ↗                                 ↑                                ↖
         print(p); 호출                            print(p); 호출                             print(p); 호출
             ↗                                            ↑                                            ↖
Person p; | . |                                Person p; | . |                                Person p; | . |
            |                                              |                                              |
            |Person p = new Student()                      |Person p = new Researcher()                   |Person p = new Professor()
            ↓                                              ↓                                              ↓
      Class Student                               class Researcher                                 class Professor
```

### instanceof 사용 예
```
                         class Person {  }
                                 ↑
            ↑-------------------→←---------------------↑
class Student extends Person {            class Researcher extends Person {
}                                         }
                                                       ↑
                                          class Professor extends Researcher {
                                          }
```
```
Person jee = new Student();
Person kim = new Professor();
Person lee = new Researcher();
if (jee instanceof Person) // jee는 Person 타입이므로 true
if (jee instanceof Student) // jee는 Student 타입이므로 true
if (kim instanceof Student) // kim은 Student 타입이 아니므로 false
if (kim instanceof Professor) // kim은 Professor 타입이므로 true
if (kim instanceof Researcher) // Professor 객체는 Researcher 타입이기도 하므로 true
if (lee instanceof Professor) // lee는 Professor 타입이 아니므로 false

오류
if (3 instanceof int) // 문법 오류. instanceof는 객체에 대한 레퍼런스만 사용

if ("java" instanceof String) // true
```

#### 예제 5-4 : instanceof 연산자 활용
- instanceof 연산자를 이용하여 상속 관계에 따라 레퍼런스가 가리키는 객체의 타입을 알아본다
- 실행 결과는 무엇인가?
```
class Person {}
class Student extends Person {}
class Researcher extends Person {}
class Professor extends Researcher {}

public class InstanceOfEx {
  static void print(Person p) {
    if (p instanceof Person)
      System.out.print("Person ");
    if (p instanceof Student)
      System.out.print("Student ");
    if (p instanceof Researcher)
      System.out.print("Researcher ");
    if (p instanceof Professor)
      System.out.print("Professor ");
    System.out.println();
  }
  public static void main(String[] args) {
    System.out.print("new Student() -> \t"); print(new Student());
    System.out.print("new Researcher() -> \t"); print(new Researcher());
    System.out.print("new Professor() -> \t"); print(new Professor());
  }
}

[실행 결과]
new Student() -> Person Student
new Researcher() -> Person Researcher
new Professor() -> Person Researcher Professor      // new Professsor() 객체는 
                                                       Person 타입이기도 하고,
                                                       Researcher, Professor 타입이기도 함 
```

### 메소드 오버라이딩
- 메소드 오버라이딩(Method Overriding)
  - 슈퍼 클래스의 메소드를 서브 클래스에서 재정의
    - 슈퍼 클래스 메소드의 이름, 매개변수 타입 및 개수, 리턴 타입 등 모든 것 동일하게 작성
  - 메소드 무시하기, 덮어쓰기로 번역되기도 함
  - 동적 바인딩 발생
    - 서브 클래스에 오버라이딩된 메소드가 무조건 실행되는 동적 바인딩
```
                                     ------------- 슈퍼 클래스
                                     | 메소드1() |
메소드2() 호출 ---------X-----------→ | 메소드2() |
              ↘                     | 메소드3() |
                 ↘                  | ......... |     
                    ↘               -------------
                       ↘                 ↑
                          ↘              | 상속
                   동적 바인딩↘           |
                                ↘--→ | 메소드2() | 서브 클래스
                                           ↳ 메소드2() 오버라이딩

                                      [서브 클래스 객체]
```

### 메소드 오버라이딩 사례
- Shape 클래스의 draw() 메소드를 Line, Rect, Circle 클래스에서 각각 오버라이딩한 사례
```
                                              class Shape {
                                                public void draw() {
                                                  System.out.println("Shape");
                                                }
                                              }
                                                        ↑
            -------------------------------------------→|←---------------------------------------------
            ↑                                           ↑                                              ↑
class Line extends Shape {                  class Rect extends Shape {                  class Circle extends Shape {
  public void draw() {                        public void draw() {                        public void draw() {
    System.out.println("Line");                 System.out.println("Rect");                 System.out.println("Circle");
  }                                           }                                           }
}                                           }                                           }
```

### 오버라이딩에 의해 서브 클래스의 메소드 호출
- (1) 서브 클래스 레퍼런스로 오버라이딩된 메소드 호출
```
Line line = new Line();
line.draw();

[실행 결과]
Line
```
```
line | . |----→
         Shape | draw() | // draw()의 메소드
          Line | draw() | // Line에서 오버라이딩한 메소드
```
- (2) 업캐스팅에 의해 슈퍼 클래스 레퍼런스로 오버라이딩된 메소드 호출(동적 바인딩)
```
Shape shape = new Line();
shape.draw();

[실행 결과]
Line
```
```
shape | . |----→
          Shape | draw() | ↓동적 바인딩
           Line | draw() |
```

### 오버라이딩의 목적, 다형성 실현
- 오버라이딩
  - 슈퍼 클래스에 선언된 메소드를, 각 서브 클래스들이 자신만의 내용으로 새로 구현하는 기능
  - 상속을 통해 '하나의 인터페이스(같은 이름)에 서로 다른 내용 구현'이라는 객체 지향의 다형성 실현
    - Line 클래스에서 draw()는 선을 그리고
    - Circle 클래스에서 draw()는 원을 그리고
    - Rect 클래스에서 draw()는 사각형을 그리고
- 오버라이딩은 실행 시간 다형성 실현
  - 동적 바인딩을 통해 실행 중에 다형성 실현
    - 오버로딩은 컴파일 타임 다형성 실현

#### 예제 5-5 : 메소드 오버라이딩으로 다형성 실현
```
class Shape { // 슈퍼 클래스
  public Shape next;
  public Shape() { next = null; }

  public void draw() {
    System.out.println("Shape");
  }
}

class Line extends Shape {
  public void draw() { // 메소드 오버라이딩
    System.out.println("Line");
  }
}

class Rect extends Shape {
  public void draw() { // 메소드 오버라이딩
    System.out.println("Rect");
  }
}

class Circle extends Shape {
  public void draw() { // 메소드 오버라이딩
    System.out.println("Circle");
  }
}
```
```
public class MethodOverridingEx {
  static void paint(Shape p) {
    p.draw(); // p가 가리키는 객체 내에 오버라이딩된 draw() 호출
              // 동적 바인딩
  }

  public static void main(String[] args) {
    Line line = new Line();
    paint(line);
    paint(new Shape());
    paint(new Line());
    paint(new Rect());
    paint(new Circle());
  }
}
```
```
[실행 결과]
Line
Shape
Line
Rect
Circle
```

#### 예제 실행 과정
```
Line line = new Line()
paint(line);

line | . |----→| void draw() | Shape의 멤버
               ---------------
   동적 바인딩↓ | void draw() | Line의 멤버 → "Line" 출력
                   Line 객체 
---------------------------------------------------------
paint(new Shape());

p | . |----→| void draw() | Shape의 멤법 → "Shape" 출력
                Shape 객체
---------------------------------------------------------
paint(new Line());

p | . |----→| void draw() | Shape의 멤버
            ---------------
          ↓ | void draw() | Line의 멤버 → "Line" 출력
                Line 객체
---------------------------------------------------------
paint(new Rect());

p | . |----→| void draw() | Shape의 멤버
            ---------------
          ↓ | void draw() | Rect의 멤버 → "Rect" 출력
                Rect 객체
---------------------------------------------------------
paint(new Circle());

p | . |----→| void draw() | Shape의 멤버
            ---------------
          ↓ | void draw() | Circle의 멤버 → "Circle" 출력
                Circle 객체
```

#### 예제 5-5의 Shape, Line, Rect, Circle 클래스 활용 : 오버라이딩 활용
```
public class UsingOverride {
  public static void main(String[] args) {
    Shape start, last, obj;
    // 링크도 리스트로 도형 생성하여 연결
    start = new Line(); // Line 객체 연결
    last = start;
    obj = new Rect();
    last.next = obj; // Rect 객체 연결
    last = obj;
    obj = new Circle(); // Circle 객체 연결
    last.next = obj;
    // 모든 도형 출력
    Shape p = start;
    while (p != null) {
      p.draw();
      p = p.next;
    }
  }
}

[실행 결과]
Line
Rect
Line
Circle
```
```
        p | . |                                         last | . |
            ↓                                                  ↓
Shape start   Shape         Shape         Shape         Shape
  | . |----→| draw() |---→| draw() |---→| draw() |---→| draw() |
            ----------------------------------------------------
            | draw() |↓   | draw() |↓   | draw() |↓   | draw() |↓ 
              Line          Rect           Line         Circle
```

#### 예제 5-5의 동적 바인딩
- 동적 바인딩
  - 실행할 메소드를 실행 시(run time)에 결정
  - 오버라이딩 메소드가 항상 호출
```
public class Shape {
  protected String name;
  public void paint() {
    draw();
  }
  public void draw() {
    System.out.println("Shape");
  }
  public static void main(String[] args) {
    Shape a = new Shape();
    a.paint();
  }
}

[실행 결과]
Shape

a | . |----→| paint() |
            ----------
            |  draw() |↓ Shape 부분
```
```
class Shape {
  protected String name;
  public void paint() {
    draw();
  }
  public void draw() {
    System.out.println("Shape");
  }
}

public class Circle extends Shape {
  @Override
  public void draw() {
    System.out.println("Circle");
  }
  public static void main(String[] args) {
    Shape b = new Circle();
    b.paint();
  }
}

[실행 결과]
Circle

b | . |----→| paint() | Shape 부분
            |  draw() | Shape 부분
            -----------
            |  draw() |↓ Circle 부분
```

### 오버라이딩 super 키워드
- super는 슈퍼 클래스의 멤버를 접근할 때 사용되는 레퍼런스
- 서브 클래스에서만 사용
- 슈퍼 클래스의 메소드 호출
- 컴파일러는 super의 접근을 정적 바인딩으로 처리
```
class Shape {
  protected String name;
  public void paint() {
    draw();
  }
  public void draw() { // (1)
    System.out.println(name);
  }
}

public class Circle extends Shape {
  protected String name;
  @Oberride
  public void draw() {
    name = "Circle";
    super.name = "Shape";
    super.draw(); // 정적 바인딩(1) ↑
    System.out.println(name);
  }
  public static void main(String[] args) {
    Shape b = new Circle();
    b.paint();
  }
}

[실행 결과]
Shape
Circle

b | . |----→| name ["Shape"] |
            | paint()        | Shape 부분
            | draw()         |
            ------------------
            | name ["Circle"] | Circle 부분
            | draw()          |
```

#### 예제 5-6 : 메소드 오버라이딩
- 게임에서 무기를 표현하는 Weapon 클래스를 만들고 살상능력을 리턴하는 fire() 메소드를 작성하면 다음과 같다. fire()은 1을 리턴한다
```
class Weapon {
  protected int fire() {
    return 1; // 무기는 기본적으로 한 명만 살상
  }
}
```
- 대포를 구현하기 위해 Weapon을 상속받는 Cannon 클래스를 작성하라. Cannon은 살상능력이 10이다.
  fire() 메소드를 이에 맞게 오버라이딩하라. main()을 작성하여 오버라이딩을 테스트하라
```
class Cannon extends Weapon }
  @Override
  protected int fire() { // 오버라이딩
    return 10; // 대포는 한 번에 10명을 살상
  }
}
```
```
public class Overriding {
  public static void main(String[] args) {
    Weapon weapon;
    weapon = new Weapon();
    System.out.println("기본 무기의 살상 능력은" + weapon.fire());
    weapon = new Cannon();
    System.out.println("대포의 살상 능력은" + weapon.fire());
  }
}

[실행 결과]
기본 무기의 살상 능력은 1
대포의 살상 능력은 10
```

### 오버라이딩 vs 오버라이딩
- 
| 비교 요소 | 메서드 오버로딩 (Overloading) | 메서드 오버라이딩 (Overriding) |
|-----------|-------------------------------|--------------------------------|
| 선언 | 같은 클래스나 상속 관계에서 동일한 이름의 메서드를 중복 작성 | 서브 클래스에서 슈퍼 클래스에 있는 메서드와 동일한 이름의 메서드 재작성 |
| 관계 | 동일한 클래스 내 혹은 상속 관계 | 상속 관계 |
| 목적 | 이름이 같은 여러 개의 메서드를 작성하여 사용의 편리성 향상, 다형성 실현 | 슈퍼 클래스의 메서드를 재정의하여 새로운 기능 구현, 다형성 실현 |
| 조건 | 메서드 이름은 같고 매개변수의 타입이나 개수가 달라야 함 | 메서드 이름, 매개변수 타입·개수, 반환 타입이 모두 같아야 함 |
| 바인딩 | 정적 바인딩(컴파일 시 결정) | 동적 바인딩(실행 시 결정) |

### 추상 메소드와 추상 클래스
- 추상 메소드(abstract method)
  - 선언되어 있으나 구현되어 있지 않은 메소드, abstract로 선언
  ```
  public abstract String getname();
  public abstract void setName(String s);
  ```
  - 추상 메소드는 서브 클래스에서 오버라이딩하여 구현해야 함
- 추상 클래스(abstract class)의 2종류
  - 1. 추상 메소드를 하나라도 가진 클래스
    - 클래스 앞에 반드시 abstract라고 선언해야 함
  - 2. 추상 메소드가 하나도 없지만 abstract로 선언된 클래스

### 2가지 종류의 추상 클래스 사례
- 1. 추상 메소드를 포함하는 추상 클래스
```
abstract class Shape { // 추상 클래스 선언
  public Shape() {}
  public void paint() { draw(); }
  abstract public void draw(); // 추상 메소드
}
```
- 2. 추상 메소드 없는 추상 클래스
```
abstract class MyComponent { // 추상 클래스 선언
  String name;
  public void load(String name) {
    this.name = name;
  }
}
```
- 추상 클래스는 객체를 생성할 수 없다

### 추상 클래스의 상송
- 추상 클래스의 상속 2가지 경우
  - 1. 추상 클래스의 단순 상속
    - 추상 클래스를 상속받아, 추상 메소드를 구현하지 않으면 추상 클래스 됨
    - 서브 클래스도 abstract로 선언해야 함
    ```
    abstract class Shape { // 추상 클래스
      public Shape() {}
      public void paint() { draw(); }
      abstract public void draw(); // 추상 메소드
    }
    abstract class Line extends Shape { // 추상 클래스. draw()를 상속받기 때문
      public String toString() { return "Line"; }
    }
    ```
  - 2. 추상 클래스 구현 상속
    - 서브 클래스에서 슈퍼 클래스의 추상 메소드 구현(오버라이딩)
    - 서브 클래스는 추상 클래스 아님

### 추상 클래스의 용도
- 설계와 구현 분리
  - 슈퍼 클래스에서는 개념 정의
    - 서브 클래스마다 다른 구현이 필요한 메소드는 추상 메소드로 선언
  - 각 서브 클래스에서 구체적 행위 구현
    - 서브 클래스마다 목적에 맞게 추상 메소드 다르게 구현
- 계층적 상속 관계를 갖는 클래스 구조를 만들 때

#### 예제 5-7 : 추상 클래스의 구현 연습
- 다음 추상 클래스 Calculator를 상속받은 GoodCalc 클래스를 구현하라
```
abstract class Calculator {
  public abstract int add(int a, int b);
  public abstract int subtract(int a, int b);
  public abstract double average(int[] a);
}
```
```
[예제 5-7 정답]

public class GoodCalc extends Calculator {
  @Override
  public int add(int a, int b) { // 추상 메소드 구현
    return a + b;
  }
  @Override
  public int substract(int a, int b) { // 추상 메소드 구현
    return a - b;
  }
  @Override
  public double average(int[] a) { // 추상 메소드 구현
    double sum = 0;
    for(int i = 0; i < a.length; i++)
      sum += a[i];
    return sum / a.length;
  }

  public static void main(String[] args) {
    GoodCalc c = new GoodCalc();
    System.out.println(c.dd(2, 3));
    System.out.println(c.substract(2, 3));
    System.out.println(c.average(new int[] { 2, 3, 4 }));
  }
}

[실행 결과]
5
-1
3.0
```

### 자바의 인터페이스
- 자바의 인터페이스
  - 클래스가 구현해야 할 메소드들이 선언되는 추상형
  - 인터페이스 선언
    - interface 키워드로 선언
    - (예시) public interface SerialDriver {...}
- 자바 인터페이스에 대한 변화
  - java 7까지
    - 인터페이스는 상수와 추상 메소드로만 구성
  - java 8부터
    - 상수와 추상메소드 포함
    - default 메소드 포함(java 8)
    - private 메소드 포함(java 9)
    - static 메소드 포함(java 9)
  - 여전히 인터페이스에는 필드(멤버 변수) 선언 불가

### 자바 인터페이스 사례
```
interface PhoneInterface { // 인터페이스 선언
  public static final int TIMEOUT = 10000; // 상수 필드 public static final 생략 가능
  public abstract void sendCall(); // 추상 메소드 public abstract 생략 가능
  public abstract void receiveCall(); // 추상 메소드 public abstract 생략 가능
  public default void printLogo() { // default 메소드 public 생략 가능
    System.out.println("** Phone **");
  };  // 디폴트 메소드
}
```

### 인터페이스의 구성 요소들의 특징
- 인터페이스의 구성 요소들
  - 상수
    - public만 허용, public static final 생략
  - 추상 메소드
    - public abstract 생략 가능
  - default 메소드
    - 인터페이스에 코드가 작성된 메소드
    - 인터페이스를 구현하는 클래스에 자동 상속
    - public 접근 지정만 허용. 생략 가능
  - private 메소드
    - 인터페이스 내에 메소드 코드가 작성되어야 함
    - 인터페이스 내에 있는 다른 메소드에 의해서만 호출 가능
  - static 메소드
    - public, private 모두 지정 가능. 생략하면 public
   
### 자바 인터페이스의 전체적인 특징
- 인터페이스의 객체 생성 불가
```
[오류]
new PhoneInterface(); // 오류. 인터페이스 PhoneInterface 객체 생성 불가
```
- 인터페이스 타입의 레퍼런스 변수 선언 가능
```
PhoneInterface galaxy; // galaxy는 인터페이스에 대한 레퍼런스 변수
```
- 인터페이스 구현
  - 인터페이스를 상속받는 클래스는 인터페이스의 모든 추상 메소드 반드시 구현
- 다른 인터페이스 상속 가능
- 인터페이스의 다중 상속 가능

### 인터페이스 구현
- 인터페이스의 추상 메소드를 모두 구현한 클래스 작성
  - implements 키워드 사용
  - 여러 개의 인터페이스 동시 구현 가능
- 인터페이스 구현 사례
  - PhoneInterface 인터페이스를 구현한 SamsungPhone 클래스
  ```
  class SamsungPhone implements PhoneInterface { // 인터페이스 구현
    // PhoneInterface의 모든 메소드 구현
    public void sendCall() { System.out.println("띠리리리링"); }
    public void receiveCall() { System.out.println("전화가 왔습니다."); }

    // 메소드 추가 작성
    public void flash() { System.out.println("전화기에 불이 켜졌습니다."); }
  }
  ```

#### 예제 5-8 : 인터페이스 구현
- PhoneInterface 인터페이스를 구현하고 flash() 메소드를 추가한 SamsungPhone 클래스를 작성하라
```
interface PhoneInterface {    // 인터페이스 선언
    final int TIMEOUT = 10000;    // 상수 필드 선언

    void sendCall();      // 추상 메소드
    void receiveCall();   // 추상 메소드

    default void printLogo() {    // default 메소드
        System.out.println("** Phone **");
    }
}

class SamsungPhone implements PhoneInterface {    // 인터페이스 구현

    // PhoneInterface의 모든 추상 메소드 구현
    @Override
    public void sendCall() {
        System.out.println("띠리리리링");
    }

    @Override
    public void receiveCall() {
        System.out.println("전화가 왔습니다.");
    }

    // 메소드 추가 작성
    public void flash() {
        System.out.println("전화기에 불이 켜졌습니다.");
    }
}

public class InterfaceEx {
    public static void main(String[] args) {

        SamsungPhone phone = new SamsungPhone();

        phone.printLogo();
        phone.sendCall();
        phone.receiveCall();
        phone.flash();
    }
}

[실행 결과]
** Phone **
띠리리리링
전화가 왔습니다.
전화기에 불이 켜졌습니다.
```

### 인터페이스 상속
- 인터페이스가 다른 인터페이스 상속
  - extends 키워드 이용
  ```
  interface MobilePhoneInterface extends PhoneInterface {
    void sendSMS(); // 새로운 추상 메소드 추가
    void receiveSMS(); // 새로운 추상 메소드 추가
  }
  ```
  - 다중 인터페이스 상속
  ```
  interface MP3Interface {
    void play(); // 추상 메소드
    void stop(); // 추상 메소드
  }

  interface MusicPhoneInterface extends MobilePhoneInterface, Mp3Interface {
    void playMP3RingTone(); // 새로운 추상 메소드 추가
  }
  ```

### 인터페이스의 목적
- 인터페이스는 스펙을 주어 클래스들이 그 기능을 서로 다르게 구현할 수 있도록 하는 클래스의 규격 선언이며, 클래스의 다형성을 실현하는 도구이다

### 다중 인터페이스 구현
- 클래스는 하나 이상의 인터페이스를 구현할 수 있음
```
interface AIInterface {
    void recognizeSpeech();   // 음성 인식
    void synthesizeSpeech();  // 음성 합성
}

class AIPhone implements MobilePhoneInterface, AIInterface {

    // MobilePhoneInterface의 모든 메소드 구현
    @Override
    public void sendCall() {
        System.out.println("전화 걸기");
    }

    @Override
    public void receiveCall() {
        System.out.println("전화 받기");
    }

    @Override
    public void sendSMS() {
        System.out.println("문자 보내기");
    }

    @Override
    public void receiveSMS() {
        System.out.println("문자 받기");
    }

    // AIInterface의 모든 메소드 구현
    @Override
    public void recognizeSpeech() {
        System.out.println("음성 인식");
    }

    @Override
    public void synthesizeSpeech() {
        System.out.println("음성 합성");
    }

    // 추가 메소드
    public int touch() {
        System.out.println("터치 기능");
        return 0;
    }
}

클래스에서 인터페이스의 메소드를 구현할 때 public을 생략하면 오류 발생
```

#### 예제 5-9 : 인터페이스를 구현하고 동시에 클래스를 상속받는 사례
```
interface PhoneInterface {    // 인터페이스 선언
    final int TIMEOUT = 10000;    // 상수 필드 선언

    void sendCall();      // 추상 메소드
    void receiveCall();   // 추상 메소드

    default void printLogo() {    // default 메소드
        System.out.println("** Phone **");
    }
}

interface MobilePhoneInterface extends PhoneInterface {
    void sendSMS();
    void receiveSMS();
}

interface MP3Interface {    // 인터페이스 선언
    public void play();
    public void stop();
}

class PDA {    // 클래스 작성

    public int calculate(int x, int y) {
        return x + y;
    }
}

// SmartPhone 클래스는 PDA를 상속받고,
// MobilePhoneInterface와 MP3Interface에 선언된 추상 메소드를 모두 구현한다.
class SmartPhone extends PDA implements MobilePhoneInterface, MP3Interface {

    // MobilePhoneInterface의 추상 메소드 구현
    @Override
    public void sendCall() {
        System.out.println("따르릉따르릉~~");
    }

    @Override
    public void receiveCall() {
        System.out.println("전화 왔어요.");
    }

    @Override
    public void sendSMS() {
        System.out.println("문자갑니다.");
    }

    @Override
    public void receiveSMS() {
        System.out.println("문자왔어요.");
    }

    // MP3Interface의 추상 메소드 구현
    @Override
    public void play() {
        System.out.println("음악 연주합니다.");
    }

    @Override
    public void stop() {
        System.out.println("음악 중단합니다.");
    }

    // 추가로 작성한 메소드
    public void schedule() {
        System.out.println("일정 관리합니다.");
    }
}

public class InterfaceEx {

    public static void main(String[] args) {

        SmartPhone phone = new SmartPhone();

        phone.printLogo();
        phone.sendCall();
        phone.play();

        System.out.println("3과 5를 더하면 " +
                           phone.calculate(3, 5));

        phone.schedule();
    }
}

[실행 결과]
** Phone **
따르릉따르릉~~
음악 연주합니다.
3과 5를 더하면 8
일정 관리합니다.
```

### 추상 클래스와 인터페이스 비교
- 유사점
  - 객체를 생성할 수 없고, 상속을 위한 슈퍼 클래스로만 사용
  - 클래스의 다형성을 실현하기 위한 목적
- 차이점
  - 
  | 비교 | 추상 클래스 | 인터페이스 |
  |--------|--------|--------| 
  | 목적 | 서브 클래스에서 필요한 대부분의 기능을 구현해 두고, 서브 클래스가 상속받아 활용하도록 함. 필요에 따라 기능을 추가·재정의하여 다형성을 구현 | 객체의 기능을 표준화하여 여러 클래스가 동일한 규격을 따르도록 함. 다형성 구현 |
  | 메소드 구성 | 추상 메소드 + 일반 메소드 모두 포함 가능 | 추상 메소드 중심, default 메소드와 static 메소드 포함 가능 |
  | 필드 구성 | 상수, 변수 필드 모두 포함 가능 | 상수만 가능 (변수 필드 불가) |
  | 생성자 | 가능 | 불가능 |
  | 접근 지정자 | 자유롭게 사용 가능 | protected 선언 불가 |
  | 상속 | 단일 상속만 가능 | 다중 상속 지원 |
  | 사용 키워드 | extends | implements |
  | 특징 | 공통 기능을 일부 구현하여 코드 재사용 | 기능의 규격(설계도)만 제공 |

##### ✍️ 작성자: 박지안
##### 🐧 실습 환경: Eclipse
##### 🗓️ 작업일: 2026-06-14
