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
>  - Cache memory flush가 큰 오버헤드 발생



__프로세스를 스케줄링하기 위한 큐__

>- Job queue : 현재 시스템 내에 있는 모든 프로세스의 집합
>- Ready queue : 현재 메모리 내에 있으면서 CPU를 잡아서 실행되기를 기다리는 프로세스의 집합
>- Device queues : I/O device의 처리를 기다리는 프로세스의 집합
>- 프로세스들은 각 큐들을 오가며 수행된다



__프로세스 생성__

>- 부모 프로세스가 자식 프로세스 생성
>- 프로세스의 트리 형성
>- 프로세스는 자원을 필요로 함
>  - 운영체제로부터 받는다
>  - 부모와 공유한다
>- 자원의 공유
>  - 부모와 자식이 모든 자원을 공유하는 모델
>  - 일부를 공유하는 모델
>  - 전혀 공유하지 않는 모델
>- 수행
>  - 부모와 자식은 공존하며 수행되는 모델
>  - 자식이 종료될 때까지 부모가 기다리는 모델
>- 주소 공간
>  - 자식은 부모의 공간을 복사함
>  - 자식은 그 공간에 새로운 프로그램을 올림

```C
// fork() system call 
Parent process pid>0
Child process pid = 0

int main(){
	int pid;
	pid = fork();
	if(pid == 0) printf("Hello i'm child");
	else if(pid > 0) printf("hello i'm parent");  
}	

// wait() system call
- 프로세스 A가 wait() 시스템 콜을 호출하면 커널은 child가 종료될 때까지 프로세스 A sleep시킴(block)
    child process가 종료되면 커널은 프로세스 A를 깨운다 (ready 상태)
    

```



__프로세스 종료__

>- 프로세스가 마지막 명령을 수행한 후 운영체제에게 이를 알려줌(exit)
>  - 자식이 부모에게 output data를 보냄(via wait)
>  - 프로세스의 각종 자원들이 운영체제에게 반납됨
>- 부모 프로세스가 자식의 수행을 종료시킴(abort)
>  - 자식이 할당 자원의 한계치를 넘어섬
>  - 자식에게 할당된 태스크가 더 이상 필요하지 않음
>  - 부모가 종료하는 경우
>    - 운영체제는 부모 프로세스가 종료하는 경우 자식이 더 이상 수행되도록 두지 않는다
>    - 단계적인 종료
>- exit() System call
>  - 자발적 종료
>    - 마지막 statement 수행 후 exit() 시스템 콜을 통해
>    - 프로그램에 명시적으로 적어주지 않아도 main 함수가 리턴되는 위치에 컴파일러가 넣어줌
>  - 비자발적 종료
>    - 부모 프로세스가 자식 프로세스를 강제 종료시킴
>      - 자식 프로세스가 한계치를 넘어서는 자원요청
>      - 자식에게 할당된 태스크가 더 이상 필요하지 않음
>    - 키보드로 kill, break 등을 친 경우
>    - 부모가 종료하는 경우
>      - 부모 프로세스가 종료하기 전에 자식들이 먼저 종료됨



__프로세스 간 협력__

>- 독립적 프로세스
>  - 프로세스는 각자의 주소 공간을 가지고 수행되므로 원칙적으로 하나의 프로세스는 다른 프로세스의 수행에 영향을 미치지 못함
>- 협력 프로세스
>  - 프로세스 협력 메커니즘을 통해 하나의 프로세스가 다른 프로세스의 수행에 영향을 미칠 수 있음
>- 프로세스 간 협력 메커니즘(__IPC : Interprocess Communication__)
>  - 메시지를 전달하는 방법
>    - message passing : 커널을 통해 메세지 전달
>  - 주소 공간을 공유하는 방법
>    - shared memory : 서로 다른 프로세스 간에도 일부 주소 공간을 공유하게 하는 shared memory 메커니즘이 있음



