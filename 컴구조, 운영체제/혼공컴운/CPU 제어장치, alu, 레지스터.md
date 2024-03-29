## cpu의 ALU, 제어장치

alu는 피연산자, 제어신호를 받아들인다
신호에 따라 연산 한 후에 결과값, 플래그를 내보낸다
플래그는 연산결과에 대한 추가적인 정보

제어장치는 클럭신호, 명령어, 플래그, 제어신호를 받아들이고
cpu내부,외부에 제어신호를 보낸다

---

## 레지스터

프로그램 카운터에는 명령어를 가져올 메모리의 주소가 들어있다
메모리 주소 레지스터에는 메모리 주소가 들어간다 , 얘를 통해서 메모리에 접근함
메모리에서 가져온 값은 메모리 버퍼 레지스터에 들어감
메모리 버퍼 레지스터에 있는 값(명령어)가 명령어 레지스터에 들어감

<실행순서>
프로그램 카운터값이 메모리 주소 레지스터로 전달됨
메모리 주소레지스터의 주소를 주소버스를 통해접근, 제어신호와 함께 메모리로 전달된다
해당 메모리에서 값을 데이터 버스를 통해 가져와서 메모리 버퍼 레지스터에 넣는다
값을 가져왔으므로 프로그램 카운터는 1증가한다
메모리 버퍼 레지스터의 값(명령어)가 명령어 레지스터로 전달된다
명령어가 실행된다

이 과정이 반복됨

네가지 레지스터
- 프로그램 카운터
- 메모리 주소 레지스터
- 메모리 버퍼 레지스터
- 명령어 레지스터

+
- 범용 레지스터
- 플래그 레지스터
- 스택 포인터
- 베이스 레지스터

스택 포인터 -> 메모리의 스택영역의 최상단을 가리킴, 최상단의 메모리 주소를 갖는 레지스터
데이터가 남아있는 최상단을 가리킴

변위 주소 지정방식 = 오퍼랜드에 있는 값을 더해서 주소를 찾는 방식

원하는 데이터가 있는 주소를 찾는 방식 : 주소 지정 방식(addressing mode)
= 유효 주소에 접근하는 방식

---
## 명령어 사이클, 인터럽트

명령어 사이클(인출, 실행 사이클)

인터럽트 = cpu가 하던 행동을 멈추도록 방해하는것

동기 인터럽트(예외)
비동기 인터럽트(하드웨어 인터럽트)

<비동기 인터럽트 처리 과정>
명령어를 처리한후 인터럽트 플래그를 확인한다
인터럽트 요청이 왔으면 스택에 현재 레지스터의 정보를 백업을 한 후
인터럽트 벡터를 통해 인터럽스 서비스 루틴의 시작주소를 찾아 인터럽트 서비스 루틴을 실행한다
처리가 끝난 후 스택에서 정보를 가져와 계속 사이클을 실행한다

인터럽트 서비스 루틴 = 인터럽트가 발생했을때 실행할 프로그램



---

23/11/15 복습
cpu내부 부품

ALU(연산장치), 제어장치, 레지스터(기억장치)

ALU는 피연산자와 제어신호를 받아서 연산을 수행하고 결과를 레지스터에 저장한다
플래그 레지스터에 연산결과에 대한 추가적인 정보도 저장한다

제어장치는 cpu에서 매우 정교한 장치
클럭신호에 맞춰 동작하기 위해 클럭신호를 받는다
명령어 레지스터에서 명령어를 받아서 해석하여 제어신호를 보낸다
여러 장치에 제어신호를 보낸다 - alu, 레지스터, 메모리, i/o
메모리, io장치로부터 제어신호를 받는다

레지스터
프로그램카운터, 명령어 레지스터, 메모리 주소 레지스터, 메모리 버퍼 레지스터 (메모리 data 레지스터)

프로그램카운터 = 실행할 명령어의 주소가 들어있다
메모리 주소 레지스터 = 접근할 메모리 주소가 들어있다, 주소 버스와 제어신호를 통해 메모리에 접근한다
메모리 버퍼 레지스터 = 메모리에서 가져온값, 쓸 값이 들어있다. 데이터 버스를 이용한다
명령어 레지스터 = 실행할 명령어가 들어있다. 제어장치가 해석한다


실행흐름에 따른 레지스터의 작동
1. 프로그램 카운터에 있는 주소에 접근하기 위해 값을 메모리 주소 레지스터에 보낸다
2. 주소버스와 제어신호를 통해 메모리에 접근하여 값을 가져와서 메모리 버퍼 레지스터에 넣는다
3. 프로그램 카운터를 1 증가한다
4. 메모리 버퍼 레지스터에 넣은 값을 명령어 레지스터에 넣는다
5. 명령어를 해석하고 수행한다. 명령어 처리가 끝나면 다음 명령어를 실행하기 위해 다시 1부터 수행한다


