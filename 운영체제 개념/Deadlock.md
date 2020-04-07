## Deadlock

__Deadlock 발생의 4가지 조건__

>- Mutual exclusion
>    - 매 순간 하나의 프로세스만이 자원을 사용할 수 있음
>- No preemption
>    - 프로세스는 자원을 스스로 내어놓을 뿐 강제로 빼앗기지 않음
>- Hold and wait 
>    - 자원을 가진 프로세스가 다른 자원을 기다릴 때 보유 자원을 놓지 않고 계속 가지고 있음
>- Circular wait
>    - 자원을 기다리는 프로세스간에 사이클이 형성되어야 함



__Deadlock의 처리 방법__

>- Deadlock Prevention
>   - 자원 할당 시 Deadlock의 4가지 필요 조건 중 어느 하나가 만족되지 않도록 하는 것
>- Deadlock Avoidance
>   - 자원 요청에 대한 부가적인 정보를 이용해서 deadlock의 가능성이 없는 경우에만 자원을 할당
>   - 시스템 state가 원래 state로 돌아올 수 있는 경우에만 자원 할당
>   - 각 프로세스가 최대로 쓸 자원을 미리 알고있다고 가정
>   - 자원할당그래프, __Banker's Algorithm__을 통해 해결
>- Deadlock Detection and recovery
>   - Deadlock 발생은 허용하되 그에 대한 detection 루틴을 두어 deadlock 발견시 recover
>   - __Recovery__
>      - Process termination
>         - 데드락에 연관된 프로세스 모두 죽이기
>         - 데드락에 연관된 프로세스 하나 죽이고 데드락이 종료될 때 까지 하나씩 제거
>     - Resource Preemption
>       - 자원을 빼앗아서 데드락이 해결되는지 확인
>- Deadlock Ignorance
>   - Deadlock을 시스템이 책임지지 않음
>   - UNIX를 포함한 대부분의 OS가 채택
>   - Deadlock이 매우 드물게 발생하므로 deadlock에 대한 조치 자체가 더 큰 overhead일 수 있음
>