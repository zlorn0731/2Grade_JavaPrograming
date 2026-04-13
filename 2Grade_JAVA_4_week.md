# ☕ Java Programming Study
## 📘 3장 - 반복문과 배열 

### 반복문의 특징
- for문
- while문
- do-while문

### for문의 구성
```
       ①       ②        ④
for (초기문; 조건식; 반복 후 작업) {
         ③
     ..작업문..
}
```
```
순서도

              [초기문]
                 ↓
   ↑---------→<조건식>----false----↓
   ↑             ↓true            ↓
   ↑          [작업문]             ↓
   ↑             ↓                ↓
   ↑-------[반복 후 작업]          ↓ 
                 ↓----------------↓
                 ↓
```
```
for (i = 0; i < 10; i++) { // i가 0~9까지 10번 반복
         System.out.print(i); // 0에서 9까지 출력
}

- 결과
0123456789
```

#### for문의 예시
- 0에서 9까지 정수 출력
```
int i;
for ( i = 0; i < 10; i++ ) {
      System.out.print(i);
}

- 결과
0123456789
```
- 반복문에 변수 선언 가능
```
for ( int i = 0; i < 10; i++ ) { // 변수 i는 for문을 벗어나서 사용할 수 없음
      System.out.print(i);
}

- 결과
0123456789
```
- 0에서 100까지의 합 구하기
```
int sum = 0;
for ( int i = 0; i <= 100; i++ ) {
      sum += i;
      System.out.println(sum);
}

int i, sum;
for ( i = 0, sum = 0; i <= 100; i++) {
      sum += i;
      System.out.println(sum);
}
```

#### for문의 특이한 형태
```
for (초기작업; ture; 반복 후 작업) { // 반복 조건이 true이면 무한 반복
...............
}
```
```
for (초기작업;;반복 후 작업) { // 반복 조건이 비어 있으면 true로 간주, 무한 반복
...............
}
```
```
// 초기 작업과 반복 후 작업은 ','로 분리하여 여러 문장 나열 가능
for ( i = 0; i < 10; i++, System.out.println(i)) {
...............
}
```
```
// for문 내에 변수 선언
for ( int i = 0; i < 10; i++) { // 변수 i는 for문 내에서만 사용 가능
...............
}
```

#### 예제 3-1 : for문을 이용하여 1부터 10까지 출력
```
	public static void forTest3_1() {
		int sum = 0;
		
		for ( int i = 1; i <= 10; i++ ) { // 1~10까지 반복
			sum += i;
			System.out.print(i); // 더하는 수 출력
			
			if (i <= 9) // 1~9까지는 '+' 출력
				System.out.print(" + ");
			else {
				System.out.print(" = "); // '=' 출력하고
			System.out.print(sum); // 덧셈 결과 출력
			}
		}
	}

- 결과
1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10 = 55
```

### while문의 구성
```
         ① 
while (조건식) { 
       ②
   ..조건문..
}
```
```
순서도

 ↑------↓
 ↑   <조건식>---false----↓
 ↑      ↓true           ↓
 ↑---[작업문]            ↓
                        ↓
            ↓-----------↓
            ↓


반복 조건이 true이면 반복, false이면 반복 종료
반복 조건이 없으면 컴파일 오류
처음부터 반복 조건을 통과한 후 작업문 수행
```
```
i = 0;
while (i<10) {
    System.out.print(i);
    i++;
}

- 결과
0123456789
```

#### 예제 3-2 : -1이 입력될 때까지 입력된 수의 평균 구하기
```
	public static void whileTest3_2() {
		int count = 0;
		int sum = 0;
		Scanner scanner = new Scanner(System.in);
		System.out.println("정수를 입력하고 마지막에 -1을 입력하세요.");
		
		int n = scanner.nextInt();
		while (n != -1) {
			sum += n;
			count++;
			n = scanner.nextInt();
		}
		if (count == 0)
			System.out.println("입력된 수가 없습니다.");
		else {
			System.out.print("정수의 개수는" + count + "개이며");
			System.out.println("평균은 " + (double)sum/count + "입니다.");
		}
		scanner.close();
	}

- 결과
정수를 입력하고 마지막에 -1을 입력하세요.
10
30
-20
40
-1
정수의 개수는 4개이며 평균은 15.0입니다.
```

### do-while문의 구성
```
do {
  ..작업문.. ① 
} while(조건식);
          ②
```
```
순서도

               ↓
 ↑----------[작업문]
 ↑             ↓
 ↑---true---<조건식>
               ↓false

무조건 최소 한번 작업문 실행
반복 조건이 true이면 반복, false이면 반복 종료
반복 조건이 없으며 컴파일 오류
```
```
i = 0;
do {
   System.out.print(i);
   i++;
} while(i<10);

- 결과
0123456789
```

#### 예제 3-3 : a-z까지 출력
```
	public static void DoWhileSample() {
		char c = 'a';
		
		do {
			System.out.print(c);
			c = (char)(c + 1);
		} while (c <= 'z');
	}

- 결과
abcdefghijklmnopqrstuvwxyz
```

### 중첩 반복
- 반복문이 다른 반복문을 내포하는 구조
- 이론적으로는 몇 번이고 중첩 반복 가능
- 너무 많은 중첩 반복은 프로그램 구조를 복잡하게 하므로 2중 또는 3중 반복이 적당
```
for (int i = 0; i < 100; i++) { // 100개의 학교 성적을 모두 더함
   .......
   for (int j = 0; j < 10000; j++) { // 10000명의 학생 성적을 모두 더함
        .......
   }
 ....
}

10000명의 학생이 있는 100개 대학의 모든 학생 성적의 합을 구할 때, for문을 이용한 이중 중첩 구조
```

#### 예제 3-4 : 2중 중첩을 이용한 구구단
```
    public static void forFor3_4() {
    	for (int i = 1; i < 10; i++) {
    		for (int j = 1; j <10; j++) {
    			System.out.print(i + "*" + j + "=" + i*j);
    			System.out.print('\t');
    		}
    		System.out.println();
    	}
	}
```

### continue문
- 반복문을 빠져 나가지 않으면서 다음 반복으로 진행
```
for (초기문; 조건식; 반복 후 작업) {
    ............
    continue;
    ............
}
```
```
while (조건식) {
    ............
    continue;
    ............
}
```
```
do {
    ............
    continue;
    ............
} while(조건식);
```

#### 예제 3-5 : continue문을 이용하여 양수 합 구하기
- 5개의 정수를 입력받고 그 중 양수들만 합하여 출력하는 프로그램을 작성하라
```
	public static void continueTest3_5() {
		Scanner scanner = new Scanner(System.in);
		System.out.println("정수를 5개 입력하세요.");
		
		int sum = 0;
		for (int i = 0; i < 5; i++) {
			int n = scanner.nextInt();
			if (n <= 0)
				continue;
			else
				sum += n;
		}
		System.out.println("양수의 합은 " + sum);
		
		scanner.close();
	}

- 결과
정수를 5개 입력하세요.
5
-2
6
10
-4
양수의 합은 21
```

### break문
- 반복문 하나를 완전히 빠져 나갈 때 사용
  - 하나의 반복문만 벗어남
  - 중첩 반복의 경우 안쪽 반복문의 break문이 실행되면 안쪽 반복문만 벗어남
```
for (초기문; 조건식; 반복 후 작업) {
   .........
   break;
   .........
}
.........

(a) 현재 반복문 벗어나기
```
```
for (초기문; 조건식; 반복 후 작업) {
   while (조건식) {
        .........
        break;
        .........
   }
   .........
}
.........

(b) 중첩 반복에서 안쪽 반복문만 벗어나는 경우
```

#### 예제 3-6 : break문을 이용하여 while문 벗어나기
- "exit"이 입력되면 while문을 벗어나도록 break문을 활용하여 프로그램을 작성하라
```
	public static void breakSample() {
		Scanner scanner = new Scanner(System.in);
		System.out.println("exit을 입력하면 종료합니다.");
		
		while(true) {
			System.out.print(">>");
			String text = scanner.nextLine();
			if(text.equals("exit"))
				break;
		}
		System.out.println("종료합니다...");
		
		scanner.close();
	}

- 결과
exit을 입력하면 종료합니다.
>>dasda
>>sadasda
>>asdasd
>>exit
종료합니다...
```

##### ✍️ 작성자: 박지안
##### 🐧 실습 환경: Eclipse
##### 🗓️ 작업일: 2026-04-13
