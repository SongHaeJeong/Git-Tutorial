## JPA 기초와 매핑

__객체 매핑하기__

```java
@Entity //어노테이션을 통해 JPA가 DB랑 매핑하는 클래스라는 것 을 인식
public class Member {
	@Id //PK 맵핑
	private Long id;
	private String name;
	...
}
```



##### 데이터베이스 스키마 자동 생성하기

- DDL을 애플리케이션 실행 시점에 자동 생성
- 테이블 중심 -> 객체 중심
- 데이터베이스 방언을 활용해서 데이터베이스에 맞는 적절한 DDL 생성
- 이렇게 생성된 DDL은 개발 장비에서만 사용
- 생성된 DDL은 운영서버에서는 사용하지 않거나, 적절히 다듬은 후 사용

```
- Create : 기존테이블 삭제 후 다시 생성(DROP + CREATE)
- Update : 변경분만 반영(운영 DB에는 사용하면 안됨)
- validate : 엔티티와 테이블이 정상 매핑되었는지만 확인
- none : 사용하지 않음

개발 초기 단계에는 create 또는 update
테스트 서버느 update 또는 validate
```



##### DB 매핑 어노테이션

```
@Column(name = "USERNAME")
private String name == > DB 'USERNAME'을 자바의 name과 맵핑

@Temporal(TemporalType.TIMESTAMP)
private Date timestamp; 시간 관련
@Enumerated(EnumType.String)
```

##### 식별자 매핑 어노테이션

```
@Id(직접 매핑)
@GeneratedValue(strategy = GenerationType.AUTO) autocreatement와 비슷
```

__권장하는 식별자 전략__

- 기본 키 제약 조건
- 미래까지 이 조건을 만족하는 자연키는 찾기 어렵다 ex) 주민번호도 기본 키로 적절하기 않다
- 권장 : __Long__ + 대체키 + 키 생성전략 사용