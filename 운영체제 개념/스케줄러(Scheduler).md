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



__CPU Scheduler & Dispatcher__

>- CPU Scheduler
>  - Ready 상태의 프로세스 중에서 이번에 CPU를 줄 프로세스를 고른다
>- Dispatcher
>  - CPU의 제어권을 CPU scheduler에 의해 선택된 프로세스에게 넘긴다
>  - 이 과정을 context switch(문맥 교환)라고 한다
>- CPU 스케줄링이 필요한 경우는 프로세스에게 다음과 같은 상태 변화가 있는 경우이다
>  1. Running -> Blocked (예 : I/O 요청하는 시스템 콜)
>  2. Running -> Ready (에: 할당시간만료로 timer interrupt)
>  3. Blocked -> Ready(예 : I/O 완료후 인터럽트)
>  4. Terminate



__Scheduling Criteria(스케줄링 척도)__

>- CPU utilization(이용률)
>- Throughput(처리량)
>- Turnaround   time(소요시간, 반환시간)
>- Waiting time(대기시간)
>- Response time(응답시간)
>- 이용률이 높고 처리량이 많고 시간들이 짧으면 좋은 스케줄링을 의미



__CPU Scheduling__

>- FCFS(First-Come First-Service)
>
>  - 먼저들어오면 먼저 CPU를 할당받음
>  - Convoy effect : 앞에 Burst time이 엄청나게 긴 프로세스가 도착하면 뒤에 프로세스는 계속 기다려야됨
>
>- SJF(Shortest-Job-First)
>
>  - 각 프로세스의 다음번 CPU burst time을 가지고 스케줄링에 활용
>  - CPU burst time이 가장 짧은 프로세스를 제일 먼저 스케줄
>  - Waiting time 부분에서는 최적화
>  - Two schemes :
>    - Nonpreemptive : 일단 CPU를 잡으면 이번 CPU burst가 완료될 때까지 CPU를 선점 당하지 않음
>    - Preemptive : 현재 수행중인 프로세스의 남은 burst time보다 더 짧은 CPU burst time을 가지고 새로운 프로세스가 도착하면 CPU를 빼앗김 (SRTF)
>  - __문제점__
>    - Starvation 발생시킬 수 있음(Long Job에 대해서 CPU를 점유 못할 수도 있음)
>      - Aging 기법을 통해 해결
>    - 다음번 CPU burst time을 어떻게 알 수 있을가?
>      - 추정만이 가능
>      - 과거의 CPU burst time을 이용해서 추정
>
>- SRTF(Shortest-Remaining-Time-First)
>
>  - SJF의 선점방식
>
>- Priority Scheduling
>
>  - 높은 우선순위를 가진 프로세스에게 CPU 할당
>  - Two schemes :
>    - Nonpreemptive
>    - Preemptive
>  - __문제점__
>    - Starvation
>      - Aging 기법을 통해서 해결
>
>- __RR(Round Robin)__
>
>  - 각 프로세스는 동일한 크기의 할당 시간(time quantum)을 가짐
>
>  - 할당 시간이 지나면 프로세스는 선점당하고 ready queue의 제일 뒤에 가서 다시 줄을 선다
>
>  - n  개의 프로세스가 ready queue에 있고 할당 시간이 q time unit인 경우 각 프로세스는 최대 q time unit 단위로 CPU시간의 1/n을 얻는다.
>
>    => 어떤 프로세스도 (n-1)q time unit 이상 기다리지 않는다.
>
>  - Performance
>
>    - q larege => FCFS
>    - q small => context switch 오버헤드가 커진다
>
>- Multilevel Queue
>
>  - Ready queue를 여러개로 분할
>
>    - foreground(interactive) 
>    - background(batch - no human interaction) : 일괄적으로 CPU를 오래쓰는 작업
>
>  - 각 큐는 독립적인 스케줄링 알고리즘을 가짐
>
>    - foreground - RR
>    - background - FCFS
>
>  - 큐에 대한 스케줄링이 필요
>
>    - Fixed priority schduling
>
>      - foreground를 처리한다음에 background를 처리
>
>    - Time slice
>
>      - 각 큐에 CPU time을 적절한 비율로 할당 ex) 80% foreground , 20% background
>
>      
>
>- Multilevel Feedback Queue
>
>  - 프로세스가 다른 큐로 이동 가능
>  - 에이징을 이와 같은 방식으로 구현할 수 있다