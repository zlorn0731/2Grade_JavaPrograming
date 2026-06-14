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
