## Intro
### System Program이란?

프로그램은 두 가지로 구분할 수 있다. <br>
1. Application program (응용 프로그램)
2. System program (시스템 프로그램)

<b>응용 프로그램</b>은 일반 사용자가 컴퓨터에서 사용하는 소프트웨어이다. 워드프로세서, 웹 브라우저, 게임 등이 응용 프로그램에 해당한다. <br>
<b>시스템 프로그램</b>은 사용자가 직접 실행하지 않으며, 운영체제에 의해 실행되고 관리된다. 

### System Programming 학습 목적
1. 소프트웨어가 하드웨어 상에서 어떻게 동작하는지 이해한다.
- 사용자가 작성한 high-level 프로그램이 어떻게 CPU 상에서 동작하는지 이해한다.
    - Compiler (컴파일러)
    - Assembler (어셈블러)
    - Linker (링커)
    - Loader (로더)
    - Debugger (디버거)
    - Library (라이브러리)
- File System (파일 시스템)과 Device Driver (디바이스 드라이버)에 대해 이해한다.
- Process (프로세스)의 개념과 여러 process를 구동하기 위한 Scheduling (스케줄링)에 대해 이해한다.
- 메모리 관리 기법, 가상 메모리에 대해 이해한다.
- 최적화 기법에 대해 이해한다. (Sofrtware level, Hardware level)
- CPU 내부 동작과 intel CPU 구조에 대해 이해한다.

2. Abstraction (추상화) 개념을 이해한다.
- Information hiding (정보 은닉)을 제공한다.
    - interface (인터페이스)와 implementation (구현)을 구분할 수 있다.
- 소프트웨어를 layerd architecture (층 구조)로 구현할 수 있게 한다.