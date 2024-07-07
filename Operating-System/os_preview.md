# Operating System Preview & Background
## about OSTEP
[OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/)은 Operating Systems: Three Easy Pieces의 준말으로, 운영체제는 3개의 조각으로 나뉜다는 의미이다.
<br>
![OSTEP의 3조각](https://github.com/ghi512/ghi-log/assets/77954741/25b0431a-ed0a-4a95-977f-f2c929511600)<br>

1. **Virtualization; 가상화**
    - CPU 가상화: 프로세스, 직접 수행, 스케줄링
    - 메모리 가상화: 주소 공간, 주소 변환, segmentation, paging
2. **Concurrency; 병행성**
    - 락(lock), 스레드(thread), 세마포(semaphore), 데드락
3. **Persistence; 영속성**
    - 파일 시스템(FS), 하드디스크드라이브(HDD), 파일, 디렉토리
<br><br>

## Background
### 컴퓨터 시스템의 층 구조 (Layered Structure)
![computer system - layered](https://media.geeksforgeeks.org/wp-content/uploads/needofos.png)<br>

| 층 구조 | 예시1 | 예시2 |
| :--------------------: | :--------------------: | :--------------------: |
| User (사용자) | user1 | Minji |
| Application | 컴파일러, 어셈블러, MS word, sqlite, ... | chrome, visual studio code |
| Operating System (운영체제) | Windows, Linux, ... | macOS |
| Hardware (하드웨어) | CPU, DRAM, Disk, Terminal | Apple M2 |

<br><br>

### 프로그램이 수행될 때 어떤 일이 일어날까?
#### [컴퓨터 구성요소: CPU, 메인 메모리, I/O 모듈]
컴퓨터 시스템은 아래 그림과 같이 CPU, 메인 메모리, I/O 모듈의 세 파트로 나눌 수 있다. 세 장치는 버스(bus)로 연결된다.<br>
![computer components](https://voer.edu.vn/post-file/2d1c9e51/11893.png)<br>

**CPU**<br>
CPU 내부엔 다양한 레지스터들이 존재한다.
- PC: Program counter. 다음 수행할 명령어의 위치를 가리키는 레지스터
- IR: Instruction Resiter. fetch한 명령어를 보관하는 레지스터
- MAR, MBR, I/O AR, I/O BR: 메모리와 I/O 장치에 접근하기 위한 레지스터

※ 위의 명칭은 공통 레지스터 명칭이다. x86 아키텍처의 레지스터는 eip, eax, ebx 등으로 불린다.<br>

**메인 메모리**<br>
instruction, data를 저장한다.<br>

→ 프로그램이 수행될 때는 CPU와 메모리가 협업한다. **메인 메모리**에 명령어와 데이터를 저장하고, **CPU**의 다양한 레지스터들이 명령어를 가져와서 처리하는 이 과정을 반복한다.(fetch & execute)<br><br>

#### [프로그램 수행 과정]
**Instruction Cycle(명령 주기)**<br>
프로그램 수행 과정은 fetch와 execute의 반복이다.<br>
![basic instruction cycle](https://github.com/ghi512/ghi-log/assets/77954741/5b1d0bb7-55e0-4660-a9b3-02ed9cd0050a)<br>

- Start: 프로그램이 수행되면
- Fetch: 명령어 가져오고
- Execute: 명령어 수행하고

다시 명령어 가져오고 수행하는 과정을 반복한다.<br><br>

**프로그램 수행 예시 - 명령어 1개**<br>
아래 예시의 CPU는 16비트 명령어를 사용한다.<br>

💡 1단계 | 초기 상태 <br>

<details>
  <summary>Memory: Instruction format (e.g. 300-302)</summary>

![instruction format](https://github.com/ghi512/ghi-log/assets/77954741/841be3fc-8b24-4fd6-84b6-b4fd9fa9ab05)

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

![data format](https://github.com/ghi512/ghi-log/assets/77954741/e22d1e24-38bf-467f-b70e-df4beb4b4d39)
- 상위 1비트: 부호 (사인 비트)
- 하위 15비트: 실제 숫자
<br>
</details>
<br>

![step1](https://github.com/ghi512/ghi-log/assets/77954741/9c6e557b-fe62-4481-8ed8-570bdd12b9a4)<br>

| CPU 레지스터 | 값 | 설명 |
| :--: | :--:| :--:|
| PC | 300 | 다음 수행할 명령어의 주소는 300이다. |
| IR | 1940 | 주소 300에 있는 명령어를 패치한다.<br> IR의 값은 1940이 된다.|

<br>

💡 2단계 <br>

![step2](https://github.com/ghi512/ghi-log/assets/77954741/a70a64a3-914b-4742-b99a-5ea65ccb8682)


| CPU 레지스터 | 값 | 설명 |
| :--: | :--:| :--:|
| PC | 301 | step 1에서 주소 300의 명령어를 패치했으므로<br> 다음 주소값인 301로 값이 변경된다. |
| IR | 1940 | 명령어 1940을 수행한다.<br> 즉, 메모리 주소 940에 있는 값을 AC에 load(1)한다.|
| AC | 0003 | 메모리 주소 940에 있는 값 0003이 AC에 load된다.|

<br>

- AC: 범용 레지스터(Accumulator). 예로 eax가 있음.

- 명령어 **1940**의 의미
  - 1 : 메모리에서 AC로 load 한다.
  - 940 : 명령을 수행할 메모리의 주소

<br>

💡 3단계 <br>

![step3](https://github.com/ghi512/ghi-log/assets/77954741/7456e89b-69f6-424e-8f97-d27fd246ff48)



💡 4단계 <br>

💡 5단계 <br>

💡 6단계 <br>



<br><br>

#### [프로그램 수행 시 사용되는 다양한 하드웨어]
![execute instruction - hw](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*f3zluXpJOncOpILMdD5T3A.png)

<br><br>

### 운영체제의 정의 (definition)

<br><br>

### 시스템콜 (System call)

<br><br>

## CPU 가상화 (Virtualizing CPU)

<br><br>

## 퀴즈
1️⃣

<br><br>

2️⃣

<br><br>
