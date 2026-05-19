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
