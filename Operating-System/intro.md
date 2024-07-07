# Operating System (운영체제; OS)
## 운영체제 (Wikipedia)
- 컴퓨터 하드웨어와 소프트웨어 **자원**을 관리하는 시스템 소프트웨어이다.<br>
![OS](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Operating_system_placement.svg/165px-Operating_system_placement.svg.png)<br>
- 운영체제에서 중요한 개념 <br>
![Wikipedia](https://github.com/ghi512/ghi-log/assets/77954741/bbd8b653-463d-4e5c-8106-ca6a65f0436e) <br>

**대표적인 운영체제**
- PC 환경 (desktop)
    1. Microsoft Windows
    2. macOS
    3. Linux
- Mobile 환경
    1. Android
    2. iOS
- Server
    1. Linux
<br><br>

## OS 학습 목적
1. OS의 정의와 역할, 목표
    - 자원 관리자
2. OS의 종류
    - Windows, OS X, Linux, Unix, Android, iOS, WebOS, ...
3. OS 내부의 구조
    - 프로세스, 가상 메모리, 파일 시스템, 드라이버, 프로토콜, interrupt
4. 정책(policies)과 기법(mechanisms)
    - 정책: CPU 스케쥴링, LRU
    - 기법: inode 구현, Demand paging
5. 추상화(abstraction)
    - 컴퓨터 시스템을 이해하는데 필수적인 요소
    - 정보 은닉, 인터페이스만 보임, 층 구조 구현, illusion 제공
<br><br>

## 퀴즈
1️⃣ What are the difference between Operating Systems (e.g. MS Windows or Linux) and Applications (e.g. MS Word or Chrome)? Explain the difference using the word “mode”.<br>
→ 운영체제에는 사용자 모드(user mode)와 커널 모드(kernel mode)가 있다. 프로세서는 실행 중인 코드의 종류에 따라 모드를 전환한다. 일반 애플리케이션은 사용자 모드에서 동작하고, 운영체제는 커널 모드에서 동작한다.<br>
![communication](https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/images/userandkernelmode01.png)

- 참고: [User Mode and Kernel Mode - Windows drivers | Microsoft Learn](https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/user-mode-and-kernel-mode)
<br><br>

2️⃣ There is a Confucian philosopher, Confucius, in Chapter 1. “A Dialog on the Book”, of the OSTEP. Explain what he said.<br>
→ I hear, I forget. I see and I remember. I do and I understand; 들은 것은 잊어버리고, 본 것은 기억하고, 직접 해 본 것은 이해한다.<br><br>


## 참고 자료
- [Remzi's OSTEP; OS Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [리눅스 커널 내부 구조](https://product.kyobobook.co.kr/detail/S000001637811)