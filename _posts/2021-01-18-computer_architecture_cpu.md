---
title: "컴퓨터 구조 요약 - 중앙 처리 장치"
last_modified_at: 2021-01-18
excerpt: ""
categories:
  - computer_architecture
---

## 1. 중앙 처리 장치
컴퓨터에서 데이터 처리 동작을 수행하는 부분을 중앙 처리 장치(CPU)라고 한다. 
CPU는 주로 세 부분으로 구성된다.
1. 명령어 실행에 필요한 데이터를 저장하는 레지스터 집합
2. 마이크로 연산을 수행하는 ALU
3. 정보 전송 및 ALU 수행 동작을 제어하는 제어 장치

---

CPU구조는 아래 3가지 형식 중 하나이거나 복합적으로 섞인 형태이다.
1. 단일 누산기 구조 - 단일 프로세스 레지스터 AC가 ALU와 연결되어 명령어 수행
2. 범용 레지스터 구조 - 메모리 접근보다 빠르게 접근 가능한 레지스터를 처리 장치에 많이 두어 명령어 수행
3. 스택 구조 - 레지스터 스택, 메모리 스택을 활용하여 명령어 수행

---

명령어 형식은 3-주소, 2-주소, 1-주소, 무주소 명령어가 있다. 
이는 ADD, MUL와 같은 명령어 뒤에 나오는 주소의 개수이다. 
범용 레지스터 구조 형식의 예인 2-주소 명령어가 주로 사용된다고 한다. 
메모리와 CPU 사이의 통신을 할 때, LOAD와 STORE 명령어만 쓸 수 있는 RISC 명령어 형식 또한 존재한다.

---

명령어의 피연산자를 지정하는 방법은, 명령어의 어드레싱 모드 bit에 의해 결정된다. 
어드레싱 모드는 implied, 레지스터 모드 등 다양하다. 
이는 사용자에게 포인터, 카운터 인덱싱, 프로그램 리로케이션? 등의 편의를 제공한다. 
또한, 명령어의 주소 필드 비트를 줄인다. 예를 들어, 레지스터 크기가 총 16bit, 주소 영역이 12bit 이라고 하자. 
피연산자의 주소를 지정하는 레지스터 간접 모드에서, 12bit로 16bit 주소를 가르키는 셈이 된다.

## 2. 명령어 종류
다양한 명령어가 존재하여 사용자에게 편의성을 제공한다.
1. 데이터 전송 명령어 - LOAD, PUSH ...
2. 데이터 처리 명령어 - 산술(INCREMENT, ...), 논리(OR, ...), 시프트(ROTATE RIGHT, ...)
3. 프로그램 제어 명령어 - BRANCH, CALL ...
4. 조건부 분기 명령어 - BRANCH if ZERO ...

---

프로그램 인터럽트는 여러 문제가 발생 했을 때, 이를 해결하기 위해 현재 프로그램에서 벗어나 
다른 서비스 프로그램을 수행한 후 돌아오는 것이다. 
아래와 같이 3가지 형의 인터럽트이 존재 한다. 외부, 내부 인터럽트는 하드웨어 신호에 의해 발생한다.
1. 외부 인터럽트 - 입출력, 타이밍 장치 등에 의해 발생
2. 내부 인터럽트 - 오버플로, 0으로 나눔 등에 의해 발생
3. 소프트웨어 인터럽트 - supervisor call와 같이 프로그래머에 의해 프로그램상의 원하는 위치에서 발생

## 3. CISC / RISC
명령어 집합 수에 따라 복잡한 명령어 집합 컴퓨터(CISC), 간소화된 명령어 집합 컴퓨터(RISC)가 있다.  

CISC 특징 - 고급 언어 문장들에 대해 기계 명령어가 대응 되도록 하여 컴파일 동작 간소화
1. 많은 명령어, 몇몇 명령어는 자주 사용되지 않음
2. 다양한 어드레싱 모드
3. 가변 길이 명령어 형식
4. 메모리의 피연산자를 처리
5. 마이크로 프로그램된 제어 선호

RISC 특징 - 명령어 집합을 간소화 하여 실행 시간 단축
1. 적은 명령어
2. 적은 어드레싱 모드
3. 고정 길이 명령어 형식 - 디코딩 간단 
4. 메모리 참조는 LOAD, STORE 명령어만 하고 나머지는 CPU 레지스터
5. 하드와이어된 제어를 선호