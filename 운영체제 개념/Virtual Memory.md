## Virtual Memory

>__Demand Paging__
>
>- 실제로 필요할 때 page를 메모리에 올리는 것
>  - I/O 양의 감소
>  - Memory 사용량 감소
>  - 빠른 응답 시간
>  - 더 많은 사용자 수용
>- Valid / Invalid bit의 사용
>  - Invalid의 의미
>    - 사용되지 않는 주소 영역인 경우
>    - 페이지가 물리적 메모리에 없는 경우
>  - 처음에는 모든 page entry가 invalid로 초기화
>  - address translation 시에 invalid bit이 set 되어 있으면 => "page fault" 가 발생하고 운영체제가 CPU를 가짐 



>__Page Fault__
>
>- invalid page를 접근하면 MMU가 trap을 발생시킴(page fault trap)
>- Kernel mode로 들어가서 page fault handler가 invoke 됨



