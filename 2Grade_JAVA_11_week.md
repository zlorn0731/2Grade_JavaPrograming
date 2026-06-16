# ☕ Java Programming Study
## 📘 8장 - 입출력 스트림과 파일 입출력

### 스트림
- 스트림 입출력
  - 버퍼를 가지고 순차적으로 이루어지는 입출력
- 자바의 입출력 스트림
  - 응용프로그램과 입출력 장치를 연결하는 소프트웨어 모듈
    - 입력 스트림 : 입력 장치로부터 자바 프로그램으로 데이터를 전달
    - 출력 스트림 : 출력 장치로 데이터 출력
   
### 자바의 입출력 스트림 특징
- 스트림의 양끝에 입출력장치와 자바 응용프로그램 연결
- 스트림은 단방향
  - 입력과 출력을 동시에 하는 스트림 없음
- 입출력 스트림 기본 단위
  - 바이트 스트림의 경우 : 바이트
  - 문자 스트림의 경우 : 문자(자바에서는 문자 1개 : 2바이트)
- 선입선출 구조

### 자바의 입출력 스트림 종류
- 바이트 스트림과 문자 스트림
  - 바이트 스트림
    - 입출력되는 데이터를 단순 바이트로 처리
      - (예시) 바이너리 파일을 읽는 입력 스트림
  - 문자 스트림
    - 문자만 입출력하는 스트림
    - 문자가 아닌 바이너리 데이터는 스트림에서 처리하지 못함
      - (예시) 텍스트 파일을 읽는 입력 스트림
- JDK는 입출력 스트림을 구현한 다양한 클래스 제공
  - 다음 슬라이드

### JDK의 바이트 스트림 클래스 계층 구조
```
[InputStream]                                                             [OutputStream]
     ↑                                                                          ↑ 
     |    |----- [FileInputStream]                                              |    |----- [FileOutputStream]  
     |---------- [FilterInputStream]                                            |---------- [FilterOutputStream]
          |      ↑   |--- [BufferedInputStream]                                      |      ↑   |--- [BufferedOutputStream] 
          |      |---|--- [DataInputStream]                                          |      |---|--- [DateOutputStream]
          |          |--- [LineNumberInputStream]                                    |          |--- [PrintStream]
          |          |--- [PushbackInputStream]                                      |
          |                                                                          |---- [PipedOutputStream]
          |---- [PipedInputStream]                                                   |---- [ByteArrayOutputStream]
          |---- [SequenceInputStream]                                                |---- [ObjectOutputStream]
          |---- [ByteArrayInputStream]
          |---- [StringBufferInputStream]
          |---- [ObjectInputStream]
```

### JDK의 문자 스트림 클래스 계층 구조
```
[Reader]                                                        [Writer]
   ↑                                                               ↑   
   |     |----- [InputStreamReader]                                |     |----- [OutputStreamWriter]
   |     |      ↑                                                  |     |      ↑  
   |     |      |--- [FileReader]                                  |     |      |--- [FileWriter] 
   |     |                                                         |     |   
   |     |----- [BufferedReader]                                   |     |----- [BufferedWriter]
   |     |      ↑                                                  |     |
   |     |      |--- [LineNumberReader]                            |----------- [FilterWriter]
   |     |                                                               |
   |------------ [FilterReader]                                          |----- [CharArrayWriter]
         |       ↑                                                       |----- [PipedWriter]
         |       |--- [PushbackReader]                                   |----- [StringWriter]
         |
         |----- [CharArrayReader]
         |----- [PipedReader]
         |----- [StringReader]
```

### 문자 스트림
- 문자 스트림
  - 유니 코드(2바이트) 문자를 입출력 하는 스트림
    - 문자로 표현되지 않는 데이터는 다루지 못함
    - 이미지, 동영상과 같은 바이너리 데이터는 입출력 할 수 없음
- 문자 스트림을 다루는 클래스
  - Reader/Writer
  - InputStreamReader/OutputStreamWriter
  - FileReader/FileWriter
    - 텍스트 파일에서 문자 데이터 입출력
   
### FileReader을 이용한 파일 읽기
- 파일 전체를 읽어 화면에 출력하는 코드 샘플
```
FileReader fin = new FileReader("c:\\test.txt"); // c:\test.txt파일을 열고 파일과 입력 바이트 스트림 객체 fin 연결

int c;

while ((c = fin.read() != -1) { // 파일 끝까지 2바이트씩 c에 읽어 들임, 파일의 끝을 만나면 read()는 -1 리턴
  System.out.print((char)c); // 2바이트 c를 문자로 변환하여 화면에 출력
}

fin.close(); // 스트림을 닫음, 파일도 닫힘, 스트림과 파일의 연결을 끊음, 더 이상 스트림으로부터 읽을 수 없음
```

#### 예제 8-1 : FileReader로 텍스트 파일 읽기
- FileReader를 이용하여 c:\windows\system.ini파일을 읽어 화면에 출력하는 프로그램을 작성하라. system.ini는 텍스트 파일이다
```
import java.io.*;

public class FileReaderEx {
  public static void main(String[] args) {
    FileReader fin = null;
    try {
      fin = new FileReader("c:\\windows\\system.ini");
      int c;
      while ((c = fin.read() != -1) { // 한 문자씩 파일 끝까지 읽기
        System.out.print((char)c);
      }
      fin.close();
    }
    catch (IOException e) {
      System.out.println("입출력 오류");
    }
  }
}
```

### 문자 집합과 InpputStreamReader를 이용한 텍스트 파일 읽기
```
FileInputStream fin = new FileInputStream("c:\\Temp\\hangul.txt");
InputStreamReader in = new InputStreamReader(fin, "MS949"); // MS949 : 한글 완성형 확장형 문자 집합
```
```
while ((c = in.read() != -1) {
  System.out.print((char)c);
}
```
```
                                                              ↑ 문자 집합 사용(MS949)
                  ..10101101..              ..10101101..      |       '가', '나'
hangul.txt-메모장 ---------------→ | fin | ---------------→ | in | ---------------→ in.read()
                              FileInputStream          InputStreamReader
```

#### 예제 8-2 : InputStreamReader로 한글 텍스트 파일 읽기
- InputStreamReader를 이용하여 MS949 문자 집합으로 한글 텍스트 파일을 읽고 출력하라
```
import java.io.*;

public class FileReadHangulSuccess{
  public static void main(String[] args) {
    InputStreamReader in = null;
    FileInputStream fin = null;
    try {
      fin = new FileInputStream("c:\\Temp\\hangul.txt");
      in = new InputStreamReader(fin, "MS949"); 
      intc;

      System.out.println("인코딩 문자 집합은 " + in.getEncoding());
      while ((c = in.read()) != -1) {
        System.out.print((char)c);
      }
      in.close();
      fin.close();
     } catch (IOExceptione) {
      System.out.println("입출력 오류");
    }
  }
}
```

#### 예제 8-3 : 한글 텍스트 파일 읽기(문자 집합 지정이 잘못된 경우)
- InputStreamReader의 문자 집합을 US-ASCII로 지정하여 한글 파일을 읽고 출력하라
```
import java.io.*;

public class FileReadHangulFail {
  public static void main(String[] args) {
    InputStreamReader in = null;
    FileInputStream fin = null;
    try {
      fin = new FileInputStream("c:\\Temp\\hangul.txt");
      in = new InputStreamReader(fin, "US-ASCII"); // US-ASCII : 문자 집합 지정이 잘못된 경우의 예를 보이기 위해 일부러 틀린 문자 집합 지정
      int c;

      System.out.println("인코딩 문자 집합은 " + in.getEncoding());
      while ((c = in.read() != -1) {
        System.out.print((char)c);
      }
      in.close();
      fin.close();
    } catch (IOException e) {
      System.out.println("입출력 오류");
    }
  }
}
```

### FileWriter 사용 예시
- c:\Temp\test.txt로의 문자 출력 스트림 생성
```
FileWriter fout = new FileWriter("c:\\Temp\\test.txt");
```
- 파일 쓰기
  - 문자 단위 쓰기
  ```
  FileWriter fout = new FileWriter("c:\\Temp\\test.txt");
  fout.write('A'); // 문자 'A'출력
  fout.close();
  ```
  - 블록 단위 쓰기
  ```
  char[] buf = new char[1024];

  // buf[]배열의 처음부터 배열 크기(1024개 문자)만큼 쓰기
  fout.write(buf, 0, buf.length);
  ```

#### 예제 8-4 : 키보드 입력을 파일로 저장하기
- Scanner를 이용하여 키보드에서 입력받은 데이터를 c:\Temp\test.txt 파일에 저장하는 프로그램을 작성하라
```
import java.io.*;
import java.util.*;

  public class FileWriterEx {
    public static void main(String[] args) {
      Scanner scanner = new Scanner(System.in);
      FileWriter fout = null;
      int c;
      try {
        fout = new FileWriter("c:\\Temp\\test.txt");
        while (true) {
          String line = scanner.nextInt();
          if (lint.length() == 0)
            break;
          fout.write(line, 0, line.length());
          fout.write("\r\n", 0, 2);
        }
        fout.close();
      } catch (IOException e) {
        System.out.println("입출력 오류");
  }
  scanner.close();
  }
}
```

### 바이트 스트림 클래스
- 바이트 스트림
  - 바이트 단위의 바이너리 값을 읽고 쓰는 스트림
- 바이트 스트림 클래스
  - InputStream/OutputStream
    - 추상 클래스
    - 바이트 스트림을 다루는 모든 클래스의 슈퍼 클래스
  - FileInputStream/FileOutputStream
    - 파일로부터 바이트 단위로 읽거나 저장하는 클래스
    - 바이너리 파일의 입출력 용도
  - DataInputStream/DataOutputStream
    - 자바의 기본 데이터 타입의 값(변수)을 바이너리 값 그래도 입출력
    - 문자열도 바이너리 형태로 입출력

### FileOutputStream을 이용한 파일 쓰기
- 바이너리 값을 파일에 저장하는 바이트 스트림 코드
```
FileOutputStream fout = new FileOutputStream("c:\\Temp\\test.out");

byte b[] = {7, 51, 3, 4, -1, 24};
  for (int i = 0; i < b.length; i++)
    fout.write(b[i]); // 파일에 배열 b[i]의 정수 값(바이너리)을 그대로 기록

fout.close(); // 스트림을 닫음. 파일도 닫힘. 더 이상 스트림으로부터 읽을 수 없음
```

#### 예제 8-5 : FileOutputStream으로 바이너리 파일 쓰기
- FileOutputStream을 이용하여 byte[] 배열 속에 들어 있는 바이너리 값을 c:\Temp\test.out 파일에 저장하라.
  이 파일은 바이너리 파일이 되므로 메모장으로 볼 수 없다. 이 파일은 예제 8-6에서 FileInputStream을 이용하여 읽어 다시 출력한다.
```
import java.io.*;

public class FileOutputStreamEx{
  public static void main(String[] args) {
    byte b[] = {7,51,3,4,-1,24};
    try {
      FileOutputStreamfout= 
        new FileOutputStream("c:\\Temp\\test.out");
      for(int i=0; i<b.length; i++)
        fout.write(b[i]); // 배열 b의 바이너리를 그대로 기록
      fout.close();
      } catch(IOExceptione) {
        System.out.println( "c:\\Temp\\test.out에 저장할 수 없었습니다. 경로명을 확인해 주세요");
        return;
      }
    System.out.println("c:\\Temp\\test.out을 저장하였습니다.");
  }
}
```

#### 예제 8-6 : FileInputStream으로 바이너리 파일 읽기
- FileInputStream을 이용하여 c:\Temp\test.out파일 (예제 8-5에서 저장한 파일)을 읽어 byte[] 배열 속에 저장하고 화면에 출력하라
```
import java.io.*;

public class FileInputStreamEx{
  public static void main(String[] args) {
    byte b[] = new byte [6]; // 비어 있는 byte 배열
    try {
      FileInputStreamfin = new FileInputStream("c:\\Temp\\test.out");
      intn=0, c;
      while((c = fin.read())!= -1) {
        b[n] = (byte)c; 
        n++;
      }
      System.out.println("c:\\Temp\\test.out에서 읽은 배열을 출력합니다.");
      for(int i=0; i<b.length; i++) System.out.print(b[i] + " ");
      System.out.println();
      fin.close();
    } catch(IOExceptione) {
      System.out.println( "c:\\Temp\\test.out에서 읽지 못했습니다. 경로명을 체크해보세요");
    }
  }
}
```

### 버퍼 입출력 스트림과 버퍼 입출력의 특징
- 버퍼 스트림
  - 버퍼를 가진 스트림
  - 입출력 데이터를 일시적으로 저장하는 버퍼를 이용하여 입출력 효율 개선
- 버퍼 입출력의 목적
  - 입출력 시 운영체제의 API 호출 횟수를 줄여 입출력 성능 개선
    - 출력시 여러 번 출력되는 데이터를 버퍼에 모아두고 한 번에 장치로 출력

### 버퍼 스트림의 종류
- 바이트 버퍼 스트림
  - 바이트 단위의 바이너리 데이터를 처리하는 버퍼 스트림
  - BufferedInputStream와 BufferedOutputStream
- 문자 버퍼 스트림
  - 유니코드의 문자 데이터만 처리하는 버퍼 스트림
  - BufferedReader와 BufferedWriter
 
#### 예제 8-7 : 버퍼 스트림을 이용한 출력
- 버퍼 크기를 5로 하고, 표준 출력 스트림(System.out)과 연결한 출력 스트림을 생성하라.
  c:\temp\test2.txt 파일을 저장된 영문 텍스트를 읽어 버퍼 출력 스트림을 통해 출력하라.
```
import java.io.*;
import java.util.Scanner;

public class BufferedIOEx {
  public static void main(String[] args) {
    FileReader fin = null;
    int c;
    try {
      fin = new FileReader("c:\\Temp\\test2.txt");
      BufferedOutputStream out = new;
        BufferedOutputStream(System.out, 5);
      while ((c = fin.read() != -1) {
        out.write(c);
      }

      // 파일 데이터가 모두 출력된 상태
      new Scanner(System.in).nextLine();
      out.flush(); // 버퍼에 남아 있던 문자 모두 출력
      fin.close();
      out.close();
    } catch (IOException e) {
        e.printStackTrace();
    }
  }
}
```

### File 클래스
- File 클래스
  - 파일의 경로명을 다루는 클래스
    - java.io.File
    - 파일과 디렉토리 경로명의 추상적 표현
  - 파일 관리 기능
    - 파일 이름 변경, 삭제, 디렉토리 생성, 크기 등 파일 관리
    - File 객체는 파일 읽고 쓰기 기능 없음
   
### File 클래스 사용 예시
- 파일 객체 생성
```
File f = new File("c:\\windows\\system.ini");
```
- 파일의 경로명
```
String filename = f.getName(); // "system.ini"
String path = f.getPath(); // "c:\\windows\\system.ini"
String parent = f.getParent(); // "c:\\windows"
```
- 파일인지 디렉토리인지 구분
```
if(f.isFile()) // 파일인 경우
  System.out.println(f.getPath() + "는 파일입니다.");
else if(f.isDirectory()) // 디렉터리인 경우
  System.out.println(f.getPath() + "는 디렉터리입니다.");
```
- 서브 디렉토리 리스트 얻기
```
File f = new File("c:\\Temp");
File[] subfiles= f.listFiles(); // c:\Temp 파일 및 서브디렉터리 리스트 얻기

for(int i=0; i<filenames.length; i++) {
  System.out.print(subfiles[i].getName()); // 파일명 출력
  System.out.println("\t파일 크기: " + subfiles[i].length()); // 크기 출력
}
```

#### 예제 8-8 : File 클래스 활용한 파일 관리
- File 클래스를 이용하여 파일의 타입을 알아내고, 디렉터리에 있는 파일들을 나열하며, 디렉터리 이름
을 변경하는 프로그램을 작성해보자
```
import java.io.File;

public class FileEx {
  public static void listDirectory(File dir) {
    System.out.println("-----" + dir.getPath() + "의 서브 리스트 입니다.-----");
    File[] subFiles = dir.listFiles(); 
    for(int i=0; i<subFiles.length; i++) {
      File f = subFiles[i];
      long t = f.lastModified();
      System.out.print(f.getName());
      System.out.print("\t파일 크기: " + f.length());
      System.out.printf("\t수정한 시간: %tb %td %ta %tT\n",t, t, t, t);
    }
  }

  public static void main(String[] args) {
    File f1 = new File("c:\\windows\\system.ini");
    System.out.println(f1.getPath() + ", " + f1.getParent() + ", " + f1.getName());
    String res="";
    if(f1.isFile()) res = "파일";
    else if(f1.isDirectory()) res = "디렉토리";
    System.out.println(f1.getPath() + "은 " + res + "입니다.");

    File f2 = new File("c:\\Temp\\java_sample"); 
    if(!f2.exists()) {
      f2.mkdir(); // 존재하지 않으면 디렉토리 생성
    }
    listDirectory(new File("c:\\Temp")); 
    f2.renameTo(new File("c:\\Temp\\javasample")); 
    listDirectory(new File("c:\\Temp"));
    }
}
```

#### 예제 8-9 : 텍스트 파일 복사
- 문자 스트림 FileReader와 FileWriter를 이용하여 c:\windows\system.ini를 c:\Temp\system.txt파일로 복사하는 프로그램을 작성하라
```
import java.io.*;

public class TextCopyEx{
  public static void main(String[] args){
    File src= new File("c:\\windows\\system.ini"); // 원본 파일 경로명
    File dest= new File("c:\\Temp\\system.txt"); // 복사 파일 경로명
    intc;
    try {
      FileReaderfr= new FileReader(src);
      FileWriterfw= new FileWriter(dest); 
      while((c = fr.read()) != -1) { // 문자 하나 읽고
        fw.write((char)c); // 문자 하나 쓰고
    }
      fr.close(); fw.close();
      System.out.println(src.getPath()+ "를 " + dest.getPath()+ "로 복사하였습니다.");
    } catch (IOExceptione) {
      System.out.println("파일 복사 오류");
    }
  }
}
```

#### 예제 8-10 : 바이너리 파일 복사
- FileInputStream과 FileOutputStream을 이용하여 이미지 파일을 복사하라
```
import java.io.*;

public class BinaryCopyEx {
  public static void main(String[] args) {
    File src = new File("c:\\Temp\\srcimg.jpg"); // 원본 파일 경로명
    File dest = new File("c:\\Temp\\copyimg.jpg"); // 복사 파일 경로명
    long start = System.currentTimeMillis(); // 현재 시간
    int c;
    try {
      FileInputStream fi = new FileInputStream(src); // 파일 입력 바이트 스트림 생성
      FileOutputStream fo = new FileOutputStream(dest); // 파일 출력 바이트 스트림 생성
      while((c = fi.read()) != -1) {
        fo.write((byte)c);
      }
      fi.close();
      fo.close();
      long end = System.currentTimeMillis(); // 복사 완료 시간
      double seconds = (end-start)/1000.0; // 복사에 걸린 시간(초 단위)
      System.out.println(src.getPath()+ "를 " + dest.getPath()+ "로 복사하였습니다.");
      System.out.println("복사 시간은 " + seconds + "초입니다.");
    } catch (IOException e) {
        System.out.println("파일 복사 오류");
    }
  }
}
```

### 예제 8-11 : 블록 단위로 바이너리 파일 고속 복사
- 예제 8-10을 10KB 단위로 읽고 쓰도록 수정하여 고속으로 파일을 복사하라
```
import java.io.*;

public class BlockBinaryCopyEx {
  public static void main(String[] args) {
    File src = new File("c:\\Temp\\srcimg.jpg"); // 원본 파일 경로명
    File dest = new File("c:\\Temp\\copyimg.jpg"); // 복사 파일
    long start = System.currentTimeMillis(); // 현재 시간
    try {
      FileInputStream fi = new FileInputStream(src); // 파일 입력 바이트 스트림 생성
      FileOutputStream fo = new FileOutputStream(dest); // 파일 출력 바이트 스트림 생성
      byte [] buf = new byte [1024*10]; // 10KB 버퍼
      while(true) {
        int n = fi.read(buf); // 버퍼 크기만큼 읽기. n은 실제 읽은 바이트
        fo.write(buf, 0, n); // buf[0]부터 n 바이트 쓰기
        if(n < buf.length)
          break; // 버퍼 크기보다 작게 읽었기 때문에 파일 끝에 도달. 복사 종료
      }
      fi.close();
      fo.close();
      long end = System.currentTimeMillis(); // 복사 완료 시간
      double seconds = (end-start)/1000.0; // 복사에 걸린 시간(초 단위)
      System.out.println( src.getPath() + "를 " + dest.getPath() + "로 복사하였습니다.");
      System.out.println("복사 시간은 " + seconds + "초입니다.");
    } catch (IOException e) {
      System.out.println("파일 복사 오류");
    }
  }
}
```

##### ✍️ 작성자: 박지안
##### 🐧 실습 환경: Eclipse
##### 🗓️ 작업일: 2026-06-16
