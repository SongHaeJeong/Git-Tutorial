## Thread

__쓰레드(Thread) 란?__

>- 가벼운 프로세스라고 말한다.
>- Thread의 구성
>  - Program Counter
>  - RegisterSet
>  - Stack Space
>- Thread가 동료 Thread와 공유하는 부분(=task)
>  - Code section
>  - Data section
>  - OS resources
>- 전통적인 개념의 heavyweight process는 하나의 thread를 가지고 있는 task로 볼 수 있다



__Thread__ 장점

>- 다중 스레드로 구성된 태스크 구조에서는 하나의 서버 스레드가 blocked(waiting) 상태인 동안에도 동일한 태스크 내의 다른 스레드가 실행(running)되어 빠른 처리를 할 수 있다
>- 동일한 일을 수행하는 다중 스레드가 협력하여 높은 처리율과 성능 향상을 얻을 수 있다
>- 스레드를 사용하면 병렬성을 높일 수 있다
>- Reponsiveness - 응답성이 빠름
>- Resource Sharing - 공유 프로세스 안에 있는 쓰레드끼리는 공유되는 자원이 있음
>- Economy 



__Thread 구현 방법__

>JAVA
>
>1. Thread 클래스 상속  - run() 함수를 통해 실행
>
>```java
>public class AAA extends Thread{
>	
>	
>}
>```
>
>2. Runnable 인터페이스 상속 - run() 함수를 통해 실행
>
>```java
>public class AAA implements Runnable{
>
>}
>```
>
>