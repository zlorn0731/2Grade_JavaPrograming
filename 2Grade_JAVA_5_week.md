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
