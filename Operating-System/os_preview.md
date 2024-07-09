# Operating System Preview & Background
## 📍 about OSTEP
[OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/)은 Operating Systems: Three Easy Pieces의 준말으로, 운영체제를 중요한 3개의 조각으로 나눠 볼 수 있다는 의미다.
<br>
<img src="https://github.com/ghi512/ghi-log/assets/77954741/25b0431a-ed0a-4a95-977f-f2c929511600" width=500px><br>

1. **Virtualization; 가상화**
    - CPU 가상화: 프로세스, 직접 수행, 스케줄링
    - 메모리 가상화: 주소 공간, 주소 변환, segmentation, paging
2. **Concurrency; 병행성**
    - 락(lock), 스레드(thread), 세마포(semaphore), 데드락
3. **Persistence; 영속성**
    - 파일 시스템(FS), 하드디스크드라이브(HDD), 파일, 디렉토리
<br><br>

## 📍 Background
### 📝 컴퓨터 시스템의 층 구조 (Layered Structure)
<img src="https://media.geeksforgeeks.org/wp-content/uploads/needofos.png" width=500px><br>

| 층 구조 | 예시1 | 예시2 |
| :--------------------: | :--------------------: | :--------------------: |
| User (사용자) | user1 | Minji |
| Application | 컴파일러, 어셈블러, MS word, sqlite, ... | chrome, visual studio code |
| Operating System (운영체제) | Windows, Linux, ... | macOS |
| Hardware (하드웨어) | CPU, DRAM, Disk, Terminal | Apple M2 |

<br><br>

### 📝 프로그램이 수행될 때 어떤 일이 일어날까?
#### [컴퓨터 구성요소: CPU, 메인 메모리, I/O 모듈]
컴퓨터 시스템의 주요 구성요소에는 CPU, 메인 메모리, I/O가 있고, 장치들은 버스(bus)로 연결된다.<br>
<img src="https://voer.edu.vn/post-file/2d1c9e51/11893.png" width=500px><br>

**CPU**<br>
CPU 내부엔 다양한 레지스터들이 존재한다.
- PC: Program counter. 다음 수행할 명령어의 위치를 가리키는 레지스터
- IR: Instruction Resiter. fetch한 명령어를 보관하는 레지스터
- MAR, MBR, I/O AR, I/O BR: 메모리와 I/O 장치에 접근하기 위한 레지스터

※ 위의 명칭은 공통 레지스터 명칭이다. x86 아키텍처의 레지스터는 eip, eax, ebx 등으로 불린다.<br>

**메인 메모리**<br>
instruction, data를 저장한다.<br><br>

#### [프로그램 수행 과정]

**Instruction Cycle(명령 주기)**<br>
프로그램이 수행될 때는 CPU와 메모리가 협업한다.<br>
<img src="https://github.com/ghi512/ghi-log/assets/77954741/5b1d0bb7-55e0-4660-a9b3-02ed9cd0050a" width=500px><br>

- Start: 프로그램 수행
- Fetch: 명령어 가져옴 (메인 메모리 -> CPU)
- Execute: 명령어 수행 (CPU or CPU -> 메인 메모리)

<u>메인 메모리</u>에 명령어와 데이터를 저장하고, <u>CPU</u>의 다양한 레지스터들이 명령어를 가져와 처리한다.<br> 프로그램 수행은 <u>fetch와 execute의 반복</u>이다.<br><br>

**프로그램 수행 예시 - 명령어 1개**<br>
아래 예시의 CPU는 16비트 명령어를 사용한다.<br>

<details>
  <summary>Memory: Instruction format (e.g. 300-302)</summary>

<img src="https://github.com/ghi512/ghi-log/assets/77954741/841be3fc-8b24-4fd6-84b6-b4fd9fa9ab05" width=500px><br>

- 상위 4비트: Opcode
    - 기능 수행
    - 0001 (1): Load AC from Memory
    - 0010 (2): Store AC to Memory
    - 0101 (5): Add to AC from Memory
- 하위 12비트: Address
    - 명령어 주소 (메모리)

</details>

<details>
  <summary> Memory: Data format (e.g. 940-941)</summary>

<img src="https://github.com/ghi512/ghi-log/assets/77954741/e22d1e24-38bf-467f-b70e-df4beb4b4d39" width=500px><br>
- 상위 1비트: 부호 (사인 비트)
- 하위 15비트: 실제 숫자
<br>
</details>
<br>

<img src="https://github.com/ghi512/ghi-log/assets/77954741/e3276537-1909-42b8-af6a-75184f037977" width=500px><br>

```b = a+b;```를 수행하는 과정으로 a와 b의 초기값은 각각 3,2이다.
- step 1,2 : a 읽어옴
- step 3,4 : b 읽어와서 a와 더함
- step 5,6 : b에 더한 결과 저장

<details>
<summary> fetch & execute 세부 과정 (Step 1~6)</summary>

Step 1
- fetch 단계
- PC는 다음 수행할 명령어의 위치를 저장. 현재 수행할 명령어의 위치는 300
- 메인 메모리의 주소 300에서 명령어를 IR에 가져옴
- IR의 명령어 해석
  - 1940: 1(0001; Load AC from Memory) + 940(처리할 데이터의 주소; 데이터값 3)
  - 940번지에 있는 데이터를 load(메인 메모리 -> CPU의 AC)한다.
- AC: 범용 레지스터(Accumulator). 예로 eax가 있음.

Step 2
- execute 단계
- PC는 다음 수행할 명령어의 위치 301로 변경됨
- AC에 3이 저장됨

Step 3
- fetch 단계
- PC가 가리키는 301번지의 명령어를 IR에 가져옴
- IR의 명령어 해석
  - 5941: 5(0101; Add to AC from Memory) + 941(처리할 데이터의 메모리 주소)
  - 941번지에 있는 데이터를 add함

Step 4
- execute 단계
- PC는 다음 수행할 명령어의 위치 302로 변경됨
- AC의 값이 5가 됨 (3+2)

Step 5
- fetch 단계
- PC가 가리키는 302번지의 명령어를 IR에 가져옴
- IR의 명령어 해석
  - 2941: 2(0010; Store AC to Memory) + 941(처리할 데이터의 메모리 주소)
  - AC에 있는 값 5를 941번지에 store함

Step 6
- execute 단계
- PC는 다음 수행할 명령어의 위치 303로 변경됨
- 메모리 주소 941에 5가 저장됨
</details>

<br><br>

#### [프로그램 수행에 필요한 다양한 작업]
실제 컴퓨터는 더 복잡하기 때문에 fetch & execute 이외에 다양한 작업들이 요구됨 <br>

<img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*f3zluXpJOncOpILMdD5T3A.png" width=500px><br>

- loading
  - disk에 있는 프로그램을 main memory로 가져오는 작업
  - 프로그램 수행 시 fetch 이전에 선행되어야 함
- memory management
  - loading을 하려면 main memory 관리가 필요 (빈 공간 확인 등)
- scheduling
  - 수행 중인 여러 프로그램을 어떻게 스케줄링 할 지
- context switching (문맥 교환)
- I/O processing
  - 출력(e.g. printf) 시 I/O 작업
- file management
- IPC

운영체제는 위 작업들을 수행함으로써 <u>프로그램이 수행되기 쉬운 환경</u>을 제공한다.
<br><br>

### 📝 운영체제의 정의 (definition)
자원을 관리하고, 가상화를 제공하는 시스템 소프트웨어

#### 1) 자원 관리자 (Resource manager)
- 자원(physical, virtual)을 관리한다
- **Physical Resource**: CPU, DRAM, Disk, Flash, Device, Network 등
- **Virtual Resource**: Process, Thread, Virtual memory, Page, File, Directory, Driver, Protocol, Access control, Security 등

#### 2) 가상화(추상화) 제공 (Virtualization, Abstraction)
물리적 자원으로 논리적(추상적) 형태로 제공한다.

| Resource | 1 | 2 | 3 | 4 | 5 |
| :--: | :--: | :--: | :--: | :--: | :--: |
| **Physical** | CPU(core) | DRAM | Disk, Flash | Device | Network |
| **Virtual** | Process, Thread | Virtual memory, Page | File, Directory | Driver | Protocol |

※ Access control, Security는 논리적 형태로만 존재함 (물리적 자원 X)<br>

<img src="https://www.oreilly.com/api/v2/epubs/1565922921/files/tagoreillycom20070301oreillyimages146960.png" width=500px>
<br><br>

### 📝 시스템콜 (System call)
**OS가 사용자**(user programs & applications)**에게 제공하는 인터페이스(APIs)** 로,<br>
프로세스 관리, 파일 관리, 장치 관리, 정보 관리, 통신, 보호 등의 기능을 제공한다.

<details>
  <summary> 시스템콜 예시</summary>

| 제공 기능               | Windows                                                                              | Unix(Linux)                            |
|:-------------------------:|:--------------------------------------------------------------------------------------:|:----------------------------------------:|
| Process Control         | CreateProcess()<br>ExitProcess()<br>WaitForSingleObject()                            | fork()<br>exit()<br>wait()             |
| File Manipulation       | CreateFile()<br>ReadFile()<br>WriteFile()<br>CloseHandle()                           | open()<br>read()<br>write()<br>close() |
| Device Manipulation     | SetConsoleMode()<br>ReadConsole()<br>WriteConsole()                                  | ioctl()<br>read()<br>write()           |
| Information Maintenance | GetCurrentProcessId()<br>SetTimer()<br>Sleep()                                       | getpid()<br>alarm()<br>sleep()         |
| Communication           | CreatePipe()<br>CreateFileMapping()<br>MapViewOfFile()                               | pipe()<br>shmget()<br>mmap()           |
| Protection              | SetFileSecurity()<br>InitlializeSecurityDescriptor()<br>SetSecurityDescriptorGroup() | chmod()<br>umask()<br>chown()          |
</details>
<br>

#### 시스템콜의 구현: Mode Switch
System call은 mode switch를 발생시킴으로써 구현된다.<br>
<details>
  <summary> Mode</summary>

- mode의 종류
  1) **user mode**: 일반 애플리케이션 동작
  2) **kernel mode**: 운영체제 동작
- mode를 나눈 이유
  - 소프트웨어를 보호하기 위해서
  - 일반 프로그램에 문제가 생기면 해당 프로그램만 죽음
  - 운영체제에 문제가 생기면 위에서 동작하고 있던 모든 프로그램이 죽음
  - 따라서 운영체제는 일반 프로그램과는 다르게 보호할 필요가 있음 → mode로 동작 환경 구분

</details>
<br>
<img src="https://forns.lmu.build/assets/images/spring-2018/cmsi-387/week-4/syscall.png" width=500px><br>

1. 사용자 프로그램은 기본적으로 **user mode**에서 동작한다.
2. 사용자 프로그램이 커널에 어떤 작업을 요청해야 하는 경우(e.g. 새 파일 만들기), **시스템콜(e.g. open())을 호출해** 작업을 요청한다.
3. 시스템콜은 커널에서 수행되어야 하기 때문에 **mode switch**가 발생한다.
4. **kernel mode**에서 작업을 수행하고 return한다.
5. 다시 **mode switch**가 발생하여 **user mode**로 돌아간다.

<br><br>

## 📍 CPU 가상화 (Virtualizing CPU)
### 📝 정의
**CPU 가상화**란 1개(또는 2-4개)의 물리적 CPU를 사용자에게 **여러 개의 CPU**가 있는 것 보여지는 것이다.<br>
즉, 여러 개의 프로그램이 수행됨으로써 사용자가 여러 개의 CPU가 있는 것처럼 느끼는 것이다.<br>
(하나의 프로그램이 수행을 위해선 하나의 CPU가 필요함)

### 📝 예시 프로그램
```c
// cpu.c - Loops and Prints

#include <stdio.h>
#include <stdlib.h>
#include <sys/time.h>
#include <assert.h>
#include "common.h" // 사용자(Remzi)가 직접 만든 헤더 파일

int main(int argc, char *argv[])
{
  if (argc != 2) { // 인자가 없는 경우 종료 (잘못된 사용법)
    fprintf(stderr, "usage: cpu <string>\n");
    exit(1);
    }
  char *str = argv[1]; // 인자의 주소를 포인터 변수 str에 받음
  while (1) { // 무한 루프
    Spin(1); // 1초동안 기다림 (common.h에 정의된 함수)
    printf("%s\n", str); // 인자로 준 값 출력
  }
  return 0;
}
```

**수행 결과1**
```
prompt> gcc -o cpu cpu.c -Wa;;
prompt> ./cpu "A"
A
A
A
^C
```
- 1초 쉬고 A 출력하고 다시 1초 쉬고 A 출력하는 과정이 반복됨
- ```cpu``` 프로그램이 1번 수행됨 → process 1개 만들어짐

**수행 결과2 - 병렬 수행**
```
prompt> ./cpu A & ./cpu B & ./cpu C & ./cpu D &
[1] 7353
[2] 7354
[3] 7355
[4] 7356
A
B
D
C
A
B
D
C
A
...
```

- &는 백그라운드 수행한다는 의미
- ```cpu``` 프로그램이 4번 수행됨 → process 4개 만들어짐
- &가 있기 때문에 동시에 4개의 process가 만들어진다
- 각각의 프로세스는 각자 독립적인 CPU를 갖고 있는 것 처럼 수행됨 → **CPU 가상화**
- 이러한 CPU 가상화를 하려면 **process**와 **scheduling**의 개념을 알아야 한다.
<br><br>

## 📍 퀴즈
1️⃣ OS is defined as a resource manager. What kind of virtual resources are managed by OS for CPU, DRAM, and disk?<br>
→ CPU는 Process와 thread로, DRAM은 Virtual memory와 page로, Disk는 File과 Directory로 가상화된다.
<br><br>

2️⃣ What is the role of "&" in the above example (running "cpu.c" - 2).<br>
→ 셸 스크립트와 터미널 명령어에서 &는 명령어를 백그라운드에서 실행시키기 위해 사용된다.
```shell
./myprogram &
```
위 예에서 ```&```는 ```myprogram```을 백그라운드에서 실행시키고, 사용자는 셸 프롬프트를 반환받아 다른 명령어를 계속해서 입력할 수 있도록 한다.

<br><br>

## 📍 메모리 가상화 (Virtualizing Memory)
### 📝 정의
**메모리 가상화**란 실제 물리적인 메모리는 하나지만, **프로세스들마다 무한하고 독립적인 메모리를 가지고 있다**고 느끼는 것이다.<br>
(실제로는 여러 프로세스가 하나의 제한된 메모리를 공유함)

### 📝 예시 프로그램
```c
// mem.c
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include "common.h"

int main(int argc, char *argv[]) {
  if (argc != 2) {
    fprintf(stderr, "usage: mem <value>\n");
    exit(1);
    }
  int *p = malloc(sizeof(int)); // 4byte 메모리 공간 할당받아 p로 가리킴
  assert(p != NULL); // assert 함수 인자의 조건이 만족되면 계속 수행, 아니면 에러 처리 -> 프로그램의 신뢰성을 향상시키는 방법
  printf("(%d) addr pointed to by p: %p\n", getpid(), p);
  *p = 0; // p가 가리키는 곳 0으로 초기화
  while (1) {
    Spin(1); // 1초 동안 대기
    *p = *p + 1; // p가 가리키는 곳의 값 1 증가시킴
    printf("(%d) value of p: %d\n", getpid(), *p);
  }
  return 0;
}
```

**수행 결과1**
```
prompt> ./mem
(2134) address pointed to by p: 0x200000
(2134) p: 1
(2134) p: 2
(2134) p: 3
(2134) p: 4
(2134) p: 5
^C
```
- pid가 2134인 프로세스 만들어짐
- 2134 프로세스의 메모리 주소는 0x200000
- mem.c 프로그램을 하나만 수행하면 특별한 상황 없음. 예상한 결과대로 출력됨


**수행 결과2 - 병렬 수행**
```
prompt> ./mem & ./mem &
[1] 24113
[2] 24114
(24113) address pointed to by p: 0x200000
(24114) address pointed to by p: 0x200000
(24113) p: 1
(24114) p: 1
(24114) p: 2
(24113) p: 2
(24113) p: 3
(24114) p: 3
(24113) p: 4
(24114) p: 4
```
- 2개의 프로세스가 만들어짐 (각각의 pid는 24113, 24114)
- 같은 메모리 공간을 사용 중인 것처럼 보이지만 수행 결과를 보면 **독립적으로 p의 값이 증가**되는 것을 알 수 있음

<img src="https://github.com/ghi512/ghi-log/assets/77954741/46f3fddd-eee5-46f6-a13c-bc58f33235ee" width="500"><br>
- 물리 메모리는 하나지만, 프로세스마다 가상 메모리를 가짐
- 각 프로세스는 독립적인 메모리를 가졌다고 느껴짐 (메모리 가상화)
- 두 프로세스의 가상 메모리 주소 값이 우연히 일치할 수 있지만 사실 두 주소는 독립적임

<br><br>

## 📍 병행성 (Concurrency)

### 📝 Background: Scheduling Entity

### 📝 정의

### 📝 예시 프로그램

<br><br>

## 📍 영속성 (Persistence)

### 📝 Background: DRAM vs Disk

### 📝 정의

### 📝 예시 프로그램

<br><br>

## 📍 운영체제 설계 목표