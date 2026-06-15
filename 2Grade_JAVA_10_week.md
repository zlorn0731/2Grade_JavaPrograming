# ☕ Java Programming Study
## 📘 7장 - 제네릭과 컬렉션

### 컬렉션(collection)의 개념
- 컬렉션
  - 요소(Element) 객체들의 저장소
    - 객체들의 컨테이너라고도 불림
    - 요소의 개수에 따라 크기 자동 조절
    - 요소의 삽입, 삭제에 따른 요소의 위치 자동 이동
  - 고정 크기의 배열을 다루는 어려움 해소
  - 다양한 객체들의 삽입, 삭제, 검색 등의 관리 용이
 
### 컬렉션과 제네릭
- 컬렉션의 요소는 객체만 가능
  - 기본적으로 int, char, double 등의 기본 타입 사용 불가
    - JDK 1.5부터 자동 박싱/언박싱으로 기본 타입 값을 객체로 자동 변환
- 컬렉션은 제네릭(generics) 기법으로 구현됨
- 제네릭
  - 특정 타입만 다루지 않고, 여러 종류의 타입으로 변신할 수 있도록 클래스나 메소드를 일반화시키는 기법
    - <E>, <K>, <V> : 타입 매개 변수
      - 요소 타입을 일반화한 타입
  - 제네릭 클래스 사례
    - 제네릭 스택 : Stack<E>
      - E에 특정 타입으로 구체화
      - 정수만 다루는 스택 Stack<Integer>
      - 문자열만 다루는 스택 Stack<String>

### 제네릭의 기본 개념
- JDK 1.5에서 도입(2004년 기점)
- 모든 종류의 데이터 타입을 다룰 수 있도록 일반화된 타입 매개 변수로 클래스나 메소드를 작성하는 기법
  - C++의 템플릿과 동일
 
### Vector<E>
- Vector<E>의 특성
  - java.util.Vector
    - <E>에서 E 대신 요소로 사용할 특정 타입으로 구체화
  - 여러 객체들을 삽입, 삭제, 검색하는 컨테이너 클래스
    - 배열의 길이 제한 극복
    - 원소의 개수나 넘쳐나는 자동으로 길이 조절
  - Vector에 삽입 가능한 것
    - 객체, null
    - 기본 타입은 Wrapper 객체로 만들어 저장
  - Vector에 객체 삽입
    - 벡터의 맨 뒤에 객체 추가
    - 벡터 중간에 객체 삽입
  - Vector에서 객체 삭제
    - 임의의 위치에 있는 객체 삭제 가능 : 객체 삭제 후 자동 자리 이동

### Vector<E> 클래스의 주요 메소드
- 
| 메서드 | 설명 |
|----------|----------|
| `boolean add(E element)` | 벡터의 맨 뒤에 element 추가 |
| `void add(int index, E element)` | index 위치에 element 삽입 |
| `int capacity()` | 벡터의 현재 용량 반환 |
| `boolean addAll(Collection<? extends E> c)` | 컬렉션 c의 모든 요소를 벡터 맨 뒤에 추가 |
| `void clear()` | 벡터의 모든 요소 삭제 |
| `boolean contains(Object o)` | 벡터가 객체 o를 포함하면 true 반환 |
| `E elementAt(int index)` | index 위치의 요소 반환 |
| `E get(int index)` | index 위치의 요소 반환 |
| `int indexOf(Object o)` | 객체 o와 같은 첫 번째 요소의 인덱스 반환, 없으면 -1 |
| `boolean isEmpty()` | 벡터가 비어 있으면 true 반환 |
| `E remove(int index)` | index 위치의 요소 삭제 |
| `boolean remove(Object o)` | 객체 o와 같은 첫 번째 요소 삭제 |
| `void removeAllElements()` | 모든 요소를 삭제하고 크기를 0으로 만듦 |
| `int size()` | 벡터에 저장된 요소 개수 반환 |
| `Object[] toArray()` | 벡터의 모든 요소를 포함하는 배열 반환 |

### 컬렉션과 자동 박싱/언박싱
- JDK 1.5 이전
  - 기본 타입 데이터를 Wrapper 클래스를 이용하여 객체로 만들어 사용
  ```
  Vector<Integer> v = new Vector<Integer>();
  v.add(Integer.valueOf(4));
  ```
  - 컬렉션으로부터 요소를 얻어올 때, Wrapper 클래스로 캐스팅 필요
  ```
  Integer n = (Integer)v.get(0);
  int k = n.intValue(); // k = 4
  ```
- JDK 1.5 부터
  - 자동 박싱/언박싱이 작동하여 기본 타입 값 사용 가능
  ```
  Vector<Integer> v = new Vector<Integer> ();
  v.add(4); // 4 → Integer.valuOf(4)로 자동 박싱
  int k = v.get(0); // Integer 타입이 int 타입으로 자동 언박싱, k = 4
  ```
    - 제네릭의 타입 매개 변수를 기본 타입으로 구체화할 수는 없음
    ```
    [오류]
    Vector<int> v = new Vector<int> (); // int 오류
    ```

#### 예제 7-1 : 정수만 다루는 Vector<Integer> 컬렉션 활용
- 정수만 다루는 벡터를 생성하고, 활용하는 기본 사례를 보임
```
import java.util.Vector;

public class VectorEx{
  public static void main(String[] args) {
    // 정수 값만 다루는 제네릭 벡터 생성
    Vector<Integer> v = new Vector<Integer>(); 

    v.add(5); // 5 삽입
    v.add(4); // 4 삽입
    v.add(-1); // -1 삽입
  
    // 벡터 중간에 삽입하기
    v.add(2, 100); // 4와 -1 사이에 정수 100 삽입

    System.out.println("벡터 내의 요소 객체 수 : " + v.size()); 
    System.out.println("벡터의 현재 용량 : " + v.capacity()); 

    // 모든 요소 정수 출력하기
    for(int i=0; i<v.size(); i++) {
      intn = v.get(i);
      System.out.println(n);
    }

    // 벡터 속의 모든 정수 더하기
    intsum = 0;
    for(int i=0; i<v.size(); i++) {
      intn = v.elementAt(i);
      sum += n;
    }
    System.out.println("벡터에 있는 정수 합 : " + sum);
  }
}

[실행 결과]
벡터 내의 요소 객체 수 : 4
벡터의 현재 용량 : 10
5
4
100-1
벡터에 있는 정수 합 : 108
```

#### 예제 7-2 : Point 클래스만 다루는 Vector<Point> 컬렉션 활용
- 점(x, y)를 표현하는 Point 클래스를 만들고, Point의 객체만 다루는 벡터를 작성하라
```
import java.util.Vector;

class Point {
  private intx, y;
  public Point(intx, inty) {
    this.x= x;
    this.y= y;
  }

  public String toString() {
    return "(" + x + "," + y + ")";  
  }
}

public class PointVectorEx {
  public static void main(String[] args) {
    // Point 객체를 요소로만 가지는 벡터 생성
    Vector<Point> v = new Vector<Point>(); 

    // 3 개의 Point 객체 삽입 
    v.add(new Point(2, 3));  
    v.add(new Point(-5, 20));
    v.add(new Point(30, -8));

    v.remove(1); // 인덱스 1의 Point(-5, 20) 객체 삭제

    // 벡터에 있는 Point 객체 모두 검색하여 출력
    for(int i=0; i<v.size(); i++) {
      Point p = v.get(i); // 벡터에서 i번째 Point 객체 얻어내기
     System.out.println(p); // p.toString()을 이용하여 객체 p 출력
    }
  }
}

[실행 결과]
(2, 3)
(30, -8)
```

### 컬렉션을 매개변수로 받는 메소드 만들기
- 컬렉션을 매개변수로 받는 메소드 원형
  - (예시) public void printVector(Vector<Integer> v)
  ```
  // Integer 벡터를 매개변수로 받아 원소를 모두 출력하는 printVector() 메소드

  public void printVecotr(Vector<Integer> v) {
    for (int i = 0; i < v.size(); i++) {
      int n = v.get(i); // 벡터의 i 번째 정수
      System.out.println(n);
    }
  }
  ```
  ```
  Vector<Integer> v = new Vector<Integer> (); // Integer 벡터 생성
  printVector(v); // 메소드 호출
  ```

### 자바의 타입 추론 기능의 진화
- Java 7 이전
```
Vector<Integer> v = new Vector<Integer>();
```
- Java 7 이후
  - 컴파일러의 타입 추론 기능 추가
  - <>(다이아몬드 연산자)에 타입 매개변수 생략
  ```
  Vector<Integer> v = new Vector<>();
  ```
- Java 10 이후
  - var 키워드 도입, 컴파일러의 지역 변수 타입 추론 가능
  ```
  var v = new Vector<Integer>();
  ```

### ArrayList<E>
- ArrayList<E>의 특징
  - java.util.ArrayList, 가변 크기 배열을 구현한 클래스
    - <E>에서 E 대신 요소로 사용할 특정 타입으로 구체화
  - ArrayList에 삽입 가능한 것
    - 객체, null
    - 기본 타입은 박싱/언박싱으로 Wrapper 객체로 만들어 저장
  - ArrayList에 객체 삽입/삭제
    - 리스트의 맨 뒤에 객체 추가
    - 리스트의 중간에 객체 삽입
    - 임의의 위치에 있는 객체 삭제 가능
  - 벡터와 달리 스레드 동기화 기능 없음
    - 다수 스레드가 동시에 ArrayList에 접근할 때 동기화되지 않음
    - 개발자가 스레드 동기화 코드 작성

### ArrayList<E> 클래스의 주요 메소드
- 
| 메서드 | 설명 |
|----------|----------|
| `boolean add(E element)` | ArrayList의 맨 뒤에 element 추가 |
| `void add(int index, E element)` | index 위치에 element 삽입 |
| `boolean addAll(Collection<? extends E> c)` | 컬렉션 c의 모든 요소를 ArrayList 맨 뒤에 추가 |
| `void clear()` | ArrayList의 모든 요소 삭제 |
| `boolean contains(Object o)` | ArrayList가 객체 o를 포함하면 true 반환 |
| `E elementAt(int index)` | index 위치의 요소 반환 |
| `E get(int index)` | index 위치의 요소 반환 |
| `int indexOf(Object o)` | 객체 o와 같은 첫 번째 요소의 인덱스 반환, 없으면 -1 |
| `boolean isEmpty()` | ArrayList가 비어 있으면 true 반환 |
| `E remove(int index)` | index 위치의 요소 삭제 |
| `boolean remove(Object o)` | 객체 o와 같은 첫 번째 요소 삭제 |
| `int size()` | ArrayList에 저장된 요소 개수 반환 |
| `Object[] toArray()` | ArrayList의 모든 요소를 포함하는 배열 반환 |

#### 예제 7-3 : 문자열 입력받아 ArrayList에 저장
- 이름을 4개 입력받아 ArrayList에 저장하고 모두 출력한 후 제일 긴 이름을 출력하라
```
import java.util.*;

public class ArrayListEx {
  public static void main(String[] args) {
    // 문자열만 삽입가능한 ArrayList 컬렉션 생성
    ArrayList<String> a = new ArrayList<String>();

    // 키보드로부터 4개의 이름 입력받아 ArrayList에 삽입
    Scanner scanner = new Scanner(System.in); 
    for(int i=0; i<4; i++) {
      System.out.print("이름을 입력하세요>>");
      String s = scanner.next(); // 키보드로부터 이름 입력
      a.add(s); // ArrayList 컬렉션에 삽입
  }

  // ArrayList에 들어 있는 모든 이름 출력
  for(int i=0; i<a.size(); i++) {
    // ArrayList의 i 번째 문자열 얻어오기  
    String name = a.get(i); 
    System.out.print(name + " ");
  }

  // 가장 긴 이름 출력
  int longestIndex = 0; 
  for(int i=1; i<a.size(); i++) {
    if(a.get(longestIndex).length() < a.get(i).length())
      longestIndex = i; 
  }
  System.out.println("\n가장 긴 이름은 : " + 
    a.get(longestIndex));
  }
  scanner.close();
}

[실행 결과]
이름을 입력하세요>>Mike
이름을 입력하세요>>Jane
이름을 입력하세요>>Ashley
이름을 입력하세요>>Helen
Mike Jane Ashley Helen 
가장 긴 이름은 : Ashley

ArrayList<String> a = new ArrayList<>(); 나
var a = new ArrayList<String>();  모두 가능
```

24pg부터
