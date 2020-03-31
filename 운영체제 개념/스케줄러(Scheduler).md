## 스케줄러(Scheduler)

__스케줄러 종류__

>- Long-term scheduler (장기 스케줄러 or job scheduler)
>  - 시작 프로세스 중 어떤 것들을 ready queue로 보낼지 결정
>  - 프로세스에 memory(및 각종 자원)을 주는 문제
>  - degree of Multiprogramming을 제어
>  - time sharing system에는 보통 장기 스케줄러가 없음 (무조건 ready)
>- Short-term scheduler (단기 스케줄러 or CPU scheduler)
>  - 어떤 프로세스를 다음번에 running시킬지 결정
>  - 프로세스에 CPU를 주는 문제
>  - 충분히 빨라야함
>- Medium-Term Scheduler(중기 스케줄러 or SWapper)
>  - 여유 공간 마련을 위해 프로세스를 통째로 메모리에서 디스크로 쫓아냄
>  - 프로세스에게서 memory를 뺏는 문제
>  - degree of Multiprogramming을 제어



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
>  - Suspended (stopped)
>    - 외부적인 이유로 프로세스의 수행이 정지된 상태
>    - 프로세스는 통째로 디스크에 swap out 된다
>    - Swap out - 메모리에서 통째로 쫓겨남 Swap in : Swap out의 반대