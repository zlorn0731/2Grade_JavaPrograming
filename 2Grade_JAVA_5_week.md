# ☕ Java Programming Study
## 📘 3장 - 배열(array)

### 배열?
- 배열(array)
  - 인덱스와 인덱스에 대응하는 데이터들로 이루어진 자료 구조
    - 배열을 이용하면 한 번에 많은 메모리 공간 할당 가능
  - 같은 타입의 데이터들이 순차적으로 저장
    - 인덱스를 이용하여 원소 데이터 접근
    - 반복문을 이용하여 처리하기에 적합
  - 배열 인덱스
    - 0부터 시작
    - 인덱스는 배열의 시작 위치에서부터 데이터가 있는 상대 위치
   
### 자바 배열의 필요성과 모양
- (1) 10개의 정수형 변수를 사용하는 경우
```
int i0, i1, i2, i3, i4;

i0 [4]
      i1[55]
i2[32]
      i3[28]
i4[99]

sum = i0 + i1 + i2 + i3 + i4;
```
- (2) 10개의 정수로 구성된 배열을 사용하는 경우
```
int i[] = new int[10];

i[0] |  4  |
i[1] |  55 |
i[2] |  32 |
i[3] |  28 |
i[4] |  99 |

for (sum=0, n=0; n<10; n++)
     sum += i[n];
```

### 1차원 배열 만들기 
#### 배열 선언과 배열 생성의 두 단계 필요
- 배열 선언
```
int intArray[];
char charArray[];
또는
int[] intArray;
char[] charArray;
```
- 배열 생성
```
int intArray[] = new int[10];
char charArray[] = new char[20];
또는
int[] intArray = new int[10];
char[] charArray = new char[20];
```
#### 선언과 함께 초기화
- 배열 선언 시 값 초기화 → 데이터가 작거나 정해졌을 때
```
int intArray[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}; // 초기화된 값의 개수(10)만큼의 배열 생성
```
- 잘못된 배열 선언
```
int intArray[10]; // 컴파일 오류. 배열의 크기를 지정하면 안됨
```

### 레퍼런스 변수와 배열
- (1) 배열에 대한 레퍼런스 변수 intArray 선언
```
int intArray [];

- int : 배열 타입
- intArray : 배열에 대한 레퍼런스 변수
- [] : 배열 선언

intArray|     |
```
- (2) 배열 생성
```
intArray = new int [5];

- intArray : 배열에 대한 레퍼런스 변수
- new : 배열 생성
- int : 타입
- 5 : 원소 개수

intArray|     |-----→|     | intArray[0]
                     |     | intArray[1]
                     |     | intArray[2]
                     |     | intArray[3]
                     |     | intArray[4]
```

### 배열을 초기화하면서 생성한 결과
```
int intArray[] = {4, 3, 2, 1, 0};

intArray|     |-----→|  4  | intArray[0]
                     |  3  | intArray[1]
                     |  2  | intArray[2]
                     |  1  | intArray[3]
                     |  0  | intArray[4]
-----------------------------------------------------
double doubleArray[] = {0.01, 0.02, 0.03, 0.04};

doubleArray|     |-----→|  0.01  | doubleArray[0]
                        |  0.02  | doubleArray[1]
                        |  0.03  | doubleArray[2]
                        |  0.04  | doubleArray[3]
```

### 배열 인덱스와 원소 접근
- 배열 원소 접근
  - 배열 변수명과 []사이에 원소의 인덱스를 적어 접근
    - 배열의 인덱스는 0부터 시작
    - 배열의 마지막 항목의 인덱스는 (배열 크기 -1)
```
int intArray[] = new int[5]; // 원소가 5개인 배열 생성, 인덱스는 0~4까지 가능
intArray[0] = 5; // 원소 0에 5 저장
intArray[3] = 6; // 원소 3에 6 저장
int n = intArray[3]; // 원소 3의 값을 읽어 n에 저장, n은 6이 됨
```
- 인덱스의 범위
```
n = intArray[-2]; // 실행 오류 : 인덱스로 음수 사용 불가
n = intArray[5]; // 실행 오류 : 5는 인덱스의 범위(0~4)를 넘었음
```
- 반드시 배열 생성 후 접근
```
int intArray[]; // 오류 안나려면 "= new int[5];" 이런식으로 붙여줘야됨
intArray[1] = 8; // 오류 : 생성 되지 않은 배열 사용
```

### 레퍼런스 치환과 배열 공유
- 하나의 배열을 다수의 레퍼런스가 참조 가능
```
int intArray[] = new int[5];
int myArray[] = intArray;


intArray |     |-------------→   |     |     |     |     |     |
                      →------→   |     |     |     |     |     |
myArray  |     |------↑
```

#### 예제 3-7 : 배열에 입력 받은 수 중 제일 큰 수 찾기
- 양수 5개를 입력 받아 배열에 저장하고, 제일 큰 수를 출력하는 프로그램을 작성하시오
```
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		
		int intArray[] = new int[5];
		
		int max = 0;
		System.out.println("양수 5개를 입력하세요.");
		for(int i=0; i<5; i++) {
			intArray[i] = scanner.nextInt();
			if(intArray[i] > max)
				max = intArray[i];
		}
		System.out.print("가장 큰 수는 " + max + "입니다.");
		
		scanner.close();
	}

- 결과
양수 5개를 입력하세요.
13
13
442
555
55343
가장 큰 수는 55343입니다.
```

### 배열의 크기, length 필드
- 배열은 자바에서 객체로 관리
  - 배열 객체 내에 length 필드는 배열의 크기를 나타냄
```
int intArray[];
intArray = new int[5];

int size = intArray.length;
// size는 5

                      |     | intArray[0]
                      |     |
intArray |     |-----→|     | int length |  5  |
                      |     |
                      |     | intArray[4]
```

#### 예제 3-8 : 배열 원소의 평균 구하기
- 배열의 length 필드를 이용하여 배열 크기만큼 정수를 입력 받고 평균을 구하는 프로그램을 작성하시오
```
	public static void arrayLength() {
		int intArray[] = new int[5];
		int sum = 0;
		
		Scanner scanner = new Scanner(System.in);
		System.out.print(intArray.length + "개의 정수를 입력하세요>>");
		for(int i=0; i<intArray.length; i++)
			intArray[i] = scanner.nextInt();
		
		for(int i=0; i<intArray.length; i++)
			sum += intArray[i];
		
		System.out.print("평균은 " + (double)sum/intArray.length);
		
		scanner.close();
	}

- 결과
5개의 정수를 입력하세요>>3 4 5 6 7 
평균은 5.0
```

### 배열과 for-each문
- 배열이나 나열의각 원소를 순차적으로 접근하는데 유용한 for문
```
기본 구조

for (자료형 변수 : 배열 or 컬렉션) {
   // 실행 코드
}
```
```
int[] num = {1, 2, 3, 4, 5};
int sum = 0;
for (int k : num) // 반복될 때마다 k는 num[0], num[1], ......, num[4] 값으로 설정
   sum += k;
System.out.println("합은 " + sum);
```
```
String names[] = {"사과", "배", "바나나", "체리", "딸기", "포도"};
for (String s : names) // 반복할 때마다 s는 names[0], names[1], ......, names[5]로 설정
   System.out.print(s + " ");
```
```
enum Week {월, 화, 수, 목, 금, 토, 일} // enum는 array아님
for (Week day : Week.values()) // 반복될 때마다 day는 월, 화, 수, 목, 금, 토, 일로 설정
   System.out.print(day + "요일 ");
```

#### 예제 3-9 : for-each문 활용
```
	public static void foreachEx() {
		int[] n = {1, 2, 3, 4, 5};
		String names[] = {"사과", "배", "바나나", "체리", "딸기", "포도"};
		
		int sum = 0;
		
		for(int k : n) {
			System.out.print(k + " ");
			sum += k;
		}
		System.out.println("합은" + sum);
		
		for(String s : names)
			System.out.print(s + " ");
		System.out.println();
		
		for(Week day : Week.values())
			System.out.print(day + "요일 ");
		System.out.println();

	}

- 결과
1 2 3 4 5 합은15
사과 배 바나나 체리 딸기 포도 
월요일 화요일 수요일 목요일 금요일 토요일 일요일
```

#### 2차원 배열
```
[2차원 배열 선언]

int           intArray[][];
char          charArray[][];
double        doubleArray[][];
--------------------------------
int[][]      intArray;
char[][]     charArray;
double[][]   doubleArray;
```
```
[2차원 배열 생성]

int[][] intArray = new int[2][5];
char[][] charArray = new char[5][5];
double[][] doubleArray = new double[5][2];
--------------------------------------------
int intArray[][] = new int[2][5];
char charArray[][] = new char[5][5];
double doubleArray[][] = new double[5][2];
```
```
[2차원 배열 선언, 생성, 초기화]

int intArray[][] = {{0, 1, 2}, {3, 4, 5}, {6, 7, 8}};
char charArray[][] = {{'a', 'b', 'c'}, {'d', 'e', 'f'}};
double doubleArray[][] = {{0.01, 0.02}, {0.03, 0.04}};
```

#### 2차원 배열의 모양과 length 필드
- 2차원 배열의 모양
```
int i[][] = new int[2][5];
int size1 = i.length;
int size2 = i[0].length;
int size3 = i[1].length;
```
- 2차원 배열의 length
  - i.length → 2차원 배열의 행의 개수로서 2
  - i[n].length는 n번째 행의 열의 개수
    - i[0].length → 0번째 행의 열의 개수로서 5
    - i[1].length → 1번째 행의 열의 개수로서 5

#### 예제 3-10 : 2차원 배열로 4년 평점 구하기
```
package HS20260418;

public class ScoreAverage {

	public static void main(String[] args) {
		double score[][] = {{3.3, 3.4},
				{3.5, 3.6},
				{3.7, 4.0},
				{4.1, 4.2}};
		
		double sum = 0;
		
		for(int year=0; year<score.length; year++)
			for(int term=0; term<score[year].length; term++)
				sum += score[year][term];
		
		int n = score.length;
		int m = score[0].length;
		System.out.println("4년 전체 평점 평균은 " + sum/(n*m));
		}

}

- 결과
4년 전체 평점 평균은 3.725
```

#### 비정방형 배열
- 정방형 배열
  - 각 행의 열의 개수가 같은 배열
```
int i[][];
i = new int[4][4];
```
- 비정방향 배열
  - 각 행의 열의 개수가 다른 배열
  - 비정방형 배열의 생성
```
int i[][];
i = new int[4][];

i[0] = new int[1];
i[1] = new int[2];
i[2] = new int[3];
i[3] = new int[4];
```

#### 비정방향 배열의 length
```
int i[][];
i = new int[4][];

i[0] = new int[1];
i[1] = new int[2];
i[2] = new int[3];
i[3] = new int[4];
```
- 비정방향 배열의 length
  - i.length → 2차원 배열의 행의 개수로서 4
  - i[n].length는 n번째 행의 열의 개수
    - i[0].length → 0번쩨 행의 열의 개수로서 1
    - i[1].length → 1번째 행의 열의 개수로서 2
    - i[2].length → 2번째 행의 열의 개수로서 3
    - i[3].length → 3번째 행의 열의 개수로서 4

#### 메서드에서 배열 리턴
- 메서드의 배열 리턴
  - 배열의 레퍼런스 리턴
  - 메서드의 리턴 타입
    - 메서드의 리턴 타입과 리턴 받는 배열 타입과 일치
    - 리턴 타입에 배열의 크기를 지정하지 않음
```
int[] makeArray()
{
   int temp[] = new int[4];
   return temp;
}

int[] → 리턴 타입
makeArray → 메서드 이름
temp → 배열 리턴
```

#### 배열 리턴 과정
- (1) int[] intArray;
```
intArray |     |
```
- (2) makeArray();
```
makeArray() 메서드

             new int[4]
temp |     |→|     |     |     |     |
```
- (3) intArray에 temp 값 치환
```
intArray |     |
```
- (4) intArray[0] = 5;
      ....
      intArray[3] = 8;
```
intArray |     |→|  5  |  6  |  7  |  8  |
```

#### 예제 3-12 : 배열 리턴
- 정수 4개를 가지는 일차원 배열을 생성하고 1, 2, 3, 4로 초기화한 다음, 배열을 리턴하는 makeArray()를 작성하고,
  이 메서드로부터 배열을 전달받아 값을 출력하는 프로그램을 작성
```
package HS20260418;

public class ReturnArray {
	static int[] makeArray()
	{
		int temp[] = new int[4];
		
		for (int i=0; i<temp.length; i++)
			temp[i] = i;
		return temp;
	}
	public static void main(String[] args) {
		int intArray[];
		intArray = makeArray();
		
		for (int i=0; i<intArray.length; i++)
			System.out.print(intArray[i] + " ");
	}

}

- 결과
0 1 2 3
```

#### main() 메서드
- main()은 자바 응용프로그램의 실행 시작 메서드
- main()의 원형
  - 반드시 static
  - 반드시 public
  - 반드시 void
  - 반드시 매개 변수 타입은 문자열 배열
```
public static void main(String[] args) {
}

public - 다른 클래스에서 메서드 접근 허용
static - 객체 생성 전부터 호출 가능
void - 리턴 값 없음
String[] - 문자열 배열
args - 매개변수
```

#### 예제 3-13 : main()에서 명령행 인자의 합 계산
```
package HS20260418;

public class Calc {

	public static void main(String[] args) {
		double sum = 0.0;
		
		for (int i=0; i<args.length; i++)
			sum += Double.parseDouble(args[i]);
		
		System.out.println("합계: " + sum);
	}

}

- 결과
합계: 0.0
```

#### 자바의 예외 처리
- 컴파일 오류
  - 문법에 맞지 않게 작성된 코드
  - 컴파일할 때 발견
- 예외(Exception)
  - 오동작이나 결과에 악영향을 미칠 수 있는 실행 중 발생한 오류
    - 정수를 0으로 나누는 경우
    - 배열보다 큰 인덱스로 배열의 원소를 접근하는 경우
    - 존재하지 않는 파일을 읽으려고 하는 경우
    - 정수 입력을 기다리는 코드가 실행되고 있을 때, 문자가 입력된 경우
  - 자바에서 예외 처리 가능
    - 예외 발생 → 자바 플랫폼 인지 → 응용 프로그램에서 전달

#### 예제 3-14 : 0으로 나누기 예외 발생으로 프로그램이 강제 종료되는 경우
```
package HS20260418;

import java.util.Scanner;

public class DividByZero {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		int dividend;
		int divisor;
		
		System.out.print("나뉨수를 입력하세요: ");
		dividend = scanner.nextInt();
		System.out.print("나눗수를 입력하세요: ");
		divisor = scanner.nextInt();
		System.out.println(dividend + "를" + divisor + "로 나누면 몫은" + dividend/divisor + "입니다.");
		
		scanner.close();
	}
}

- 결과
나뉨수를 입력하세요: 4
나눗수를 입력하세요: 2
4를2로 나누면 몫은2입니다.
```

#### 예외 처리, try-catch-finally문
- 예외 처리
  - 예외가 발생할 때 대응하는 응용프로그램 코드
  - try-catch-finally문 사용
    - finally 블록은 생략 가능
```
try {
      예외가 발생할 가능성이 있는 실행문 (try 블록)
}
carch (처리할 예외 타입 선언) {
     예외 처리문(catch 블록)
}
finally {
          예외 발생 여부와 상관없이 무조건 실행되는 문장
          (finally 블록)
}
```

#### 예외에 따른 제어의 흐름
- try 블록에서 예외가 발생하지 않은 정상적인 경우
```
try {
    ....
    실행문
    ....
}
catch (처리할 예외 타입 선언)
{
  예외 처리문
}
finally {
   finally 블록 문
}
```
- try 블록에서 예외가 발생한 경우
```
try {
    예외발생
    실행문
    ....
}
catch (처리할 예외 타입 선언)
{
  예외 처리문
}
finally {
   finally 블록 문
}
```

#### 자바의 예외 클래스
- 자주 발생하는 예외
- 
| 예외 타입(예외 클래스) | 예외 발생 경우 | 패키지 |
|----------------------|---------------|----------|
| NullPointerException | null 레퍼런스를 참조할 때 발생 | java.lang |
| ArrayIndexOutOfBoundException | 배열의 범위를 벗어난 접근 시 발생 | java.lang |
| IOExecption | 입출력 동작 실패 또는 인터럽트 시 발생 | java.io |

#### 예제 3-15 : 0으로 나눌 때 발생하는 ArithmeticException 예외처리
```
package HS20260418;

import java.util.Scanner;

public class DevidByZeroHandling {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		
		while(true) {
			System.out.print("나뉨수를 입력하시오: ");
			int dividend = scanner.nextInt();
			System.out.print("나눗수를 입력하시오: ");
			int divisor = scanner.nextInt();
			
			try {
				System.out.println(dividend + "를" + divisor + "로 나누면 몫은" + dividend/divisor + "입니다.");
				break;
			}
			catch(ArithmeticException e) {
				System.out.println("0으로 나눌 수 없습니다! 다시 입력하세요: ");
			}
		}
		scanner.close();
	}

}

- 결과
나뉨수를 입력하시오: 10
나눗수를 입력하시오: 2
10를2로 나누면 몫은5입니다.
```

#### 예제 3-16 : 범위를 벗어난 배열의 접근
```
package HS20260418;

public class ArrayException {

	public static void main(String[] args) {
		int[] intArray = new int[5];
		intArray[0] = 0;
		
		try {
			for (int i=0; i<5; i++) {
				intArray[i+1] = i+1 + intArray[i];
				System.out.println("intArray[" + i + "]" + "=" + intArray[i]);
			}
		}
		catch (ArrayIndexOutOfBoundsException e) {
			System.out.println("배열의 인덱스가 범위를 벗어났습니다.");
		}
	}

}

- 결과
intArray[0]=0
intArray[1]=1
intArray[2]=3
intArray[3]=6
배열의 인덱스가 범위를 벗어났습니다.
```

##### ✍️ 작성자: 박지안
##### 🐧 실습 환경: Eclipse
##### 🗓️ 작업일: 2026-04-18
