## Paging vs Segmentation

__Paging__

>- Process의 virtual memory를 동일한 사이즈의 page 단위로 나눔
>- Virtual memory의 내용이 page 단위로 noncontiguous하게 저장됨
>- 일부는 backing storage에, 일부는 physical memory에 저장
>
>
>
>__Basic Method__
>
>- physical memory를 동일한 크기의 frame으로 나눔
>- logical memory를 동일 크기의 page로 나눔(frame과 같은 크기)
>- 모든 가용 frame들을 관리
>- page table을 사용하여 logical address를 physical address로 변환
>- External fragmentation 발생 안함
>- Internal fragmentation 발생 가능 
>



__Segmentation__

>- 프로그램은 의미 단위인 여러 개의 segment로 구성
>  - 작게는 프로그램을 구성하는 함수 하나하나를 세그먼트로 정의
>  - 크게는 프로그램 전체를 하나의 세그먼트로 정의 가능
>  - 일반적으로는 code, data, stack 부분이 하나씩의 세그먼트로 정의됨
>- Logical address는 <segment-number , offset> 으로 구성되어있음
>- Segment-table base register : 물리적 메모리에서의 segment table의 위치
>- Segment-table length register : 프로그램이 사용하는 segment의 수
>
>__Protection__
>
>- 각 세그먼트 별로 protection bit가 있음
>  - Each entry : Valid bit = 0 => illegal segment
>  - Read/Write/Execution 권한 bit
>- Sharing
>  - Shared segment
>  - Same segment number
>  - **Segment는 의미 단위이기 때문에 공유와 보안에 있어 paging보다 훨씬 효과적이다



__Segmentation with Paging__

>__pure segmentation과의 차이점__
>
>- Segment-table entry가 segment의 base address를 가지고 있는 것이 아니라 segment를 구성하는 page table의 base address를 가지고 있음
>
>

