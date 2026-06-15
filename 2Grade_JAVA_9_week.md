# ☕ Java Programming Study

## 📘 6장 - 패키지

### 패키지 개념과 필요성
- 3명이 분담하여 자바 응용프로그램을 개발하는 경우, 동일한 이름의 클래스가 존재할 가능성 있음 → 합칠 때 오류발생

### 디렉토리로 각 개발자의 코드 관리(패키지)
```
[Project]
    |-----→ [FileIO]
    |           |
    |           |---→ WebFile.class
    |           |---→ FileCopy.class
    |           |---→ FileRW.class
    |           |---→ Tools.class
    |
    |-----→ [Graphic]
    |           |
    |           |---→ Shape.class
    |           |---→ Line.class
    |           |---→ Rect.class
    |           |---→ Circle.class
    |
    |------→ [UI]
               |
               |---→ Main.class
               |---→ GUI.class
               |---→ EventHandler.class
               |---→ Tools.class

Tools.class : 이름은 같지만 경로명이 달라 서로 다른 파일로 취급
              Project/FileIO/Tools.class
              Project/UI/Tools.class
```

### 자바의 모듈(module)과 패키지(package)
- 패키지
  - 서로 관련된 클래스와 인터페이스의 컴파일 된 클래스 파일들을 하나의 디렉토리에 묶어 놓은 것
- 모듈
  - 여러 패키지와 이미지 등의 자원을 모아 놓은 컨테이너
  - JDK 9부터 자바 API의 모든 클래스들(자바 실행 환경)을 패키지 기반에서 모듈들로 완전히 재구성
  - 응용프로그램 역시 여러 개의 모듈로 분할하여 작성 가능
    - 클래스들은 패키지로 만들고, 다시 패키지를 모듈로 만듦
  - 목적
    - 자바 API를 여러 모듈(99개)로 분할하여 응용프로그램의 실행에 적합한 모듈들로만 실행 환경을 구축할 수 있도록 함
    - 메모리 등의 자원이 열악한 작은 소형 기기에 꼭 필요한 모듈로 구성된 작은 크기의 실행 이미지를 만들기 위함
  - 모듈의 현실
    - Java 9부터 전면적으로 도입, 복잡한 개념, 큰 자바 응용프로그램에는 개발, 유지보수 등에 적합
- 패키지명과 클래스의 경로명
  - 점(.)으로 연결
    - Project.FileO.Tools.class
    - Project.UI.Tools.class
   
### 자바 API의 모듈 파일들
- 자바 JDK에 제공되는 모듈 파일들
  - 자바가 설치된 jmods 디렉토리에 모듈 파일 존재
    - 자바 버전에 따라 100개에 가까운 모듈 파일
    - 모듈 파일(.jmod 파일)은 ZIP 포맷으로 압축된 파일
  - 모듈 파일에는 자바 API의 패키지와 클래스들이 들어 있음
  - Jmod 명령을 이용하여 모듈 파일에 들어 있는 패키지를 풀어 낼 수 있음
 
### 패키지 사용하기, import문
- 다른 패키지에 작성된 클래스 사용
  - import를 이용하지 않는 경우
    - 소스 내에서 패키지 이름과 클래스 이름의 전체 경로명을 써주어야 함
  ```
  public class ImportExample {
    public static void main(Stringp[] args) {
      java.util.Scanner scanner = new java.util.Scanner(System.in);
      System.out.println(scanner.next());
    }
  }
  ```
  - import를 이용하는 경우
    - 소스의 시작 부분에 사용하려는 패키지 명시
      - 소스에는 클래스 명만 명시하면 됨
    - 특정 클래스의 경로명만 포함
      - import java.util.Scanner;
    ```
    import java.util.Scanner;
    public class ImportExample {
      public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
      }
    }
    ```
    - 패키지 내의 모든 클래스 포함
      - import java.util.*;
      - *는 현재 패키지 내의 클래스만을 의미하며 하위 패키지의 클래스까지 포함하지 않음
    ```
    import java.util.*;
    public class ImportExample {
      public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
      }
    }
    ```

### 패키지 만들기
- 패키지 선언
  - package 패키지명;
    - 컴파일한 클래스 파일을 패키지명의 디렉토리에 저장하라는 지시
    - 소스 파일의 첫 줄에 선언
- 사례
```
package UI; // Tools 클래스를 컴파일하여 UI패키지에 저장할 것을 지시

public class Tools { // 이제 이 클래스의 경로명은 UI.Tools가 됨
  .......
}
```
  - Tools 클래스의 경로명은 UI.Tools
  - 다른 클래스에서 Tools 클래스를 사용하기 위해서는 import UI.Tools
  ```
  package Graphic; // Line 클래스를 Graphic 패키지에 저장

  import UI.Tools; // Tools 클래스의 경로명 알림

  public class Line {
    public void draw() {
      Tools t = new Tools();
    }
  }
  ```

### 디폴트 패키지와 패키지의 특징
- 디폴트 패키지
  - package 선언문이 없이 만들어진 클래스의 패키지
  - 디폴트 패키지는 현재 디렉토리
- 패키지의 특징
  - 패키지 계층구조
    - 관련된 클래스 파일을 하나의 패키지로 계층화하여 관리 용이
  - 패키지별 접근 제한
    - 패키지 별로 접근 권한 가능
  - 동일한 이름의 클래스와 인터페이스의 사용 가능
    - 서로 다른 패키지에 이름이 같은 클래스와 인터페이스 존재 가능
  - 높은 소프트웨어 재사용성
 
### 모듈 개념
- 모듈
  - Java 9에서 도입된 개념
  - 패키지와 이미지 등의 리소스를 담은 컨테이너
  - 모듈 파일(.jmod)로 저장
 
### 자바 플랫폼의 모듈화
- 자바 플랫폼
  - 자바의 개발 환경(JDK)과 자바의 실행 환경(JRE)을 지칭
    - Java SE(자바 API) 포함
  - 자바 API의 모든 클래스가 여러 개의 모듈로 재구성됨
  - 모듈 파일은 JDK의 jmods 디렉토리에 저장하여 베포
- 모듈 파일로부터 모듈을 푸는 명령
  - (Microsoft사의 OpenJDK를 설치한 경우)
  - jmod extract "C:\Program Files\Microsofe\jdk-17.0.3+7\jmods\java.base.jmod"
    - 풀어놓고자 하는 디렉토리로 이동 후,
    - jmod 명령을 입력하면
    - 현재 디렉토리에 java.base 모듈이 풀림

### 모듈 기반의 자바 실행 환경
- 자바 실행 환경
  - JRE : 디폴트 자바 실행 환경
    - 자바 모듈(컴파일된 자바 API 클래스들), 자바 가상 기계 등으로 구성
- 
| 비교 관점 | Java 8까지 | Java 9 이후 |
|----------|-------------|-------------|
| 자바 API 클래스의 컨테이너 | rt.jar의 단일체에 자바 API의 패키지들을 모두 담음 | rt.jar를 버렸음, 자바 API를 수십개의 모듈 파일에 나누어 저장
| 디폴트 실행 환경 | 실행되는 컴퓨터에 rt.jar 설치(rt.jar의 크기가 큼) | modules(JRE의 lib 밑에) 비공개 파일(약 109MB)에 모듈 저장, 응용프로그램 실행 시 modules 파일에서 필요한 모듈 및 클래스 코딩 |
| 맞춤형 실행 환경(custo, JRE) | 없음, 소형 기기에 rt.jar를 설치할 수 없는 한계 | 맞춤형 실행 환경 구출 가능, jlink 명령을 이용하여 응용프로그램의 실행에 필요한 모듈들로 실행 환경 구축 가능, 메모리가 열악한 소형 기기에도 응용프로그램 실행 가능 |

### 자바 모듈화의 목적
- 가장 큰 목적
  - 자바 컴포넌들을 필요에 따라 조립하여 사용하기 위함
  - 컴퓨터 시스템의 불필요한 부담 감소
    - 세밀한 모듈화를 통해 필요 없는 모듈이 로드되지 않게 함
    - 소형 IoT 장치에도 자바 응용프로그램이 실행되고 성능을 유지하게함
   
### 주요 패키지
- java.lang
  - 자바 language 패키지
    - 스트링, 수학 함수, 입출력 등 자바 프로그래밍에 필요한 기본적인 클래스와 인터페이스
  - 자동으로 import, import문 필요 없음
- java.util
  - 자바 유틸리티 패키지
    - 날짜 시간, 벡터, 해시맵 등과 같은 다양한 유틸리티 클래스와 인터페이스 제공
- java.io
  - 키보드, 모니터, 프린터, 디스크 등에 입출력을 할 수 있는 클래스와 인터페이스 제공
- java.awt
  - 자바 GUI 프로그래밍을 위한 클래스와 인터페이스 제공
- javax.swing
  - 자바 GUI 프로그래밍을 위한 스윙 패키지

### Object 클래스
- 특징
  - java.lang 패키지에 포함
  - 모든 클래스의 슈퍼 클래스
    - 모든 클래스에 강제 상속
    - 모든 객체가 공통으로 가지는 객체의 속성을 나타내는 메소드 보유
- 주요 메소드
- 
| 메소드 | 설명 |
|--------|------|
| boolean equals(Object obj) | obj가 가리키는 객체와 현재 객체를 비교하여 같으면 true 리턴 |
| Class getClass() | 현 객체의 런타임 클래스를 리턴 |
| int hashCode() | 현 객체에 대한 해시 코드 값 리턴 |
| String toString() | 현 객체에 대한 문자열 표현을 리턴 |
| void notify() | 현 객체에 대해 대기하고 있는 하나의 스레드를 깨운다 |
| void notifyAll() | 현 객체에 대해 대기하고 있는 모든 스레드를 깨운다 |
| void wait() | 다른 스레드가 깨울 때가지 현재 스레드를 대기하게 한다 |

#### 예제 6-1 : Object 클래스로 객체 속성 알아내기
- 객체 레퍼런스만으로 객체의 클래스명, 해시코드 값, 객체의 문자열을 출력해보자
```
class Point {
  private int x, y;
  public Point(int x, int y) {
    this.x = x;
    this.y = y;
  }
}

public class ObjectPropertyEx {
  public static void print(Object obj) {
    System.out.println(obj.getClass().getName()); // 클래스 이름
    System.out.println(obj.hashCode()); // 해시 코드 값
    System.out.println(obj.toString()); // 객체를 문자열로 만들어 출력
    System.out.println(obj); // 객체 출력
  }
  public static void main(String[] args) {
    Point p = new Point(2, 3);
    print(p);
  }
}

[실행 결과]
Point
366712642
Point@15db9742
Point@15db9742
```

### 객체를 문자열로 변환
- String toString()
  - 객체를 문자열로 반환
  - Object 클래스에 구현된 toString()이 반환하는 문자열
  ```
  public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
  }
  ```
- '객체 + 문자열' → '객체.toString() + 문자열'로 자동변환
```
Point p = new Point(2, 3);       변환
System.out.println(p);        ---------→ System.out.println(p.toString()); 
String s = p + "점";                     String s = p.toString() + "점";

                                         [실행 결과]
                                          Point@15db9742점
```
- 개발자는 자신만의 toString() 작성 필요
  - Object의 toString() 오버라이딩

#### 예제 6-2 : Point 클래스에 toString() 작성
- Point 클래스에 Point 객체를 문자열로 리턴하는 toString() 메소드를 작성하라
```
class Point {
  private int x, y;
  public Point(int x, int y) {
    this.x = x;
    this.y = y;
  }
  public Strinf toString() { // Point 객체를 문자열로 리턴하는 toString() 작성
    return "Point(" + x + "," + y + ")";
  }
}

public class ToStringEx {
  public static void main(String[] args) {
    Point p = new Point(2, 3);
    System.out.println(p.toString());
    System.out.println(p); // p는 p.toString()으로 자동 변환
    System.out.println(p + "입니다."); // p.toString() + "입니다."로 자동 변환
  }
}

[실행 결과]
Point(2, 3)
Point(2, 3)
Point(2, 3)입니다.
```

### 객체 비교와 equals()
- == 연산자
  - 두 개의 레퍼런스 비교
  ```
  class Point {
    private int x, y;
    public Point(int x, int y) {
      this.x = x; thi.y = y;
    }
  }

  Point a = new Point(2, 3);
  Point b = new Point(2, 3);
  Point c = a;
  if (a == b) // false
    System.out.println("a == b");
  if (a == c) // true
    System.out.println("a == c");

  [실행 결과]
  a == c
  ```
  ```
  c | . | ↘
  a | . |--→ | x = 2, y = 3 | Point 객체
  b | . |--→ | x = 2, y = 3 | Point 객체
  ```
- boolean equals(Object obj)
  - 객체 내용이 같은지 비교
  ```
  class Point {
    private int x, y;
    public Point(int x, int y) {
      this.x = x; thi.y = y;
    }
    public boolean equals(Object obj) {
      Point p = (Point)obj;
      if (x == p.x && y == p.y)
        return true;
      else return false;
    }
  }

  Point a = new Point(2, 3);
  Point b = new Point(2, 3);
  Point c = new Point(3, 4);

  if (a == b) // false
    System.out.println("a == b");
  if (a.equals(b)) // true
    System.out.println("a is equal to b");
  if (a.equals(c)) // false
    System.out.println("a is equal to c");

  [실행 결과]
  a is equal to b
  ```
  ```
  a | . |--→ | x = 2, y = 3 | Point 객체
  b | . |--→ | x = 2, y = 3 | Point 객체
  c | . |--→ | x = 3, y = 4 | Point 객체
  ```

#### 예제 6-3 : Point 클래스에 equals() 작성
- Point 클래스에 두 점의 좌표가 같으면 true를 리턴하는 equals()를 작성하라
```
class Point {
  private int x, y;
  public Point(int x, int y) {
    this.x = x; this.y = y;
  }
  public boolean equals(Object obj) {
    Point p = (Point)obj;
    if (x == p.x && y == p.y) return true;
    else return false;
  }
}

public class EqualsEx {
  public static void main(String[] args) {
    Point a = new Point(2, 3);
    Point b = new Point(2, 3);
    Point c = new Point(3, 4);

    if (a == b) // false
      System.out.println("a == b");
    if (a.equals(b)) // true
      System.out.println("a is equal to b");
    if (a.equals(c)) // false
      System.out.println("a is equal to c");
  }
}

[실행 결과]
a is equal to b
```
```
a | . |--→ | x = 2, y = 3 | Point 객체
b | . |--→ | x = 2, y = 3 | Point 객체
c | . |--→ | x = 3, y = 4 | Point 객체
```

#### 예제 6-4 : Rect 클래스와 equals() 만들기 연습
- int 타입의 width(너비)와 height(높이) 필드를 가지는 Rect 클래스를 작성하고, 면적이 같으면
  두 Rect 객체가 같은 것으로 판별하는 equals()를 작성하라. 생성자에서 너비와 높이를 받아 width, height 필드를 초기화하라
```
class Rect {
  private int width;
  private int height;
  public Rect(int width, int height) {
    this.width = width;
    this.height = height;
  }
  public boolean equals(Object obj) {
    Rect p = (Rect)obj;
    if (width * height == p.width * p.height)
      return true;
    else
      return false;
  }
}

public class EqualsEx {
  public static void main(String[] args) {
    Rect a = new Rect(2, 3);
    Rect b = new Rect(3, 2);
    Rect c = new Rect(3, 4);
    if (a.equals(b))
      System.out.println("a is equal to b");
    if (a.euqals(c))
      System.out.println("a is equal to c");
    if (a.equals(c))
      System.out.println("b is equal to c");
  }
}

[실행 결과]
a is equal to b
```

### Wrapper 클래스
- 자바의 기본 타입을 클래스화한 8개 클래스
- 
| 타입 | 단위 | 단위 | 단위 | 단위 | 단위 | 단위 | 단위 | 단위 |
|------|------|-----|-----|-----|-----|-----|-----|-----|
| 기본 타입 | byte | short | int | long | char | float | double | boolean |
| Wrapper 클래스 | Byte | Short | Integer | Long | Character | Float | Double | Boolean |
