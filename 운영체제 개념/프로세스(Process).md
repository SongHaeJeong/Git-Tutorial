## 프로세스(Process)

__프로세스 란 ?__

>실행중인 프로그램이라고 말할 수 있다.



__프로스세의 문맥(context)__

>- CPU 수행 상태를 나타내는 하드웨어 문맥
>  - Program Counter
>  - 각 종 Register
>- 프로세스 주소 공간
>  - Code, Data, Stack
>- 프로세스 관련 커널 자료 구조
>  - PCB(Process Control Block)
>  - Kernel stack



__프로세스의 상태(Process State)__

>- 프로세스는 상태(state)가 변경되며 수행된다
>  - Running
>    - CPU를 잡고 Instruction을 수행중인 상태
>  - Ready
>    - CPU를 기다리는 상태(메모리 등 다른 조건을 모두 만족하고)
>  - Blocked(wait, sleep)
>    - CPU를 주어도 당장 Instruction을 수행할 수 없는 상태
>    - Process 자신이 요청한 event가 즉시 만족되지 않아 이를 기다리는 상태
>    -  (예 디스크에서 file을 읽어와야 하는 경우)
>  - New : 프로세스가 생성중인 상태
>  - Terminated : 수행(execution)이 끝난 상태



__Process Control Block(PCB)__

>- 운영체제가 각 프로세스를 관리하기 위해 프로세스당 유지하는 정보
>
>- 다음의 구성 요소를 가진다(구조체로 유지)
>
>  1) OS가 관리상 사용하는 정보
>
>  	-	Process State, Process ID
>  	-	Scheduling information, priority
>
>  2) CPU 수행 관련 하드웨어 값
>
>  - Program Counter, Registers
>
>  3) 메모리 관련
>
>  - Code, data, stack의 위치 정보
>
>  4) 파일 관련
>
>  - Open file descriptors



__문맥 교환(Context Switch)__

>- CPU를 한 프로세스에서 다른 프로세스로 넘겨주는 과정
>- CPU가 다른 프로세스에게 넘어갈 때 운영체제는 다음을 수행
>  - CPU를 내어주는 프로세스의 상태를 그 프로세스의 PCB에 저장
>  - CPU를 새롭게 얻는 프로세스의 상태를 PCB에서 읽어옴



__프로세스를 스케줄링하기 위한 큐__

>- Job queue : 현재 시스템 내에 있는 모든 프로세스의 집합
>- Ready queue : 현재 메모리 내에 있으면서 CPU를 잡아서 실행되기를 기다리는 프로세스의 집합
>- Device queues : I/O device의 처리를 기다리는 프로세스의 집합
>- 프로세스들은 각 큐들을 오가며 수행된다







