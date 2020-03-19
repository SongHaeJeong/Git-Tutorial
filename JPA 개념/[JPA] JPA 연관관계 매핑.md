## JPA 연관관계 매핑

객체지향 설계의 목표는 자율적인 객체들의 __협력 공동체__를 만드는 것이다.

```java
객체를 테이블에 맞추어 모델링 (참조 대신에 외래 키를 그대로 사용)
@Entity
Public class Member{
	@Id @GeneratedValue
	private Long id;
	
	@Column(name ="USERNAME")
	private String name;
	private int age;
	
	@Column(name = "TEAM_ID")
	private Long teamId;
}

@Entity
public class Team{
	@Id @GeneratedValue
	private Long id;
	private String name;
}


//팀 저장
Team team = new Team();
team.set("teamA");
Repository.save(team);
//맴버 동록
Member member = new Member();
membr.setName("cjsong");
member.setTeamId(team.getId());
Repository.save(member);

//맴버 조회할 때
Member findMember = em.find(Member.class, member.getId());
Long teamId = findMember.getTeamId();

Team findTeam = em.find(Team.class, team.getId());

--> 연관관계가 없기 떄문에 하나하나씩 가지고와야됨. 객체 지향적인 설계가 아님
    

```

__객체를 테이블에 맞추어 데이터 중심으로 모델링하면, 협력 관계를 만들 수 없다.__

-  테이블은 외래 키로 조인을 사용해서 연관된 테이블을 찾는다.
- 객체는 참조를 사용해서 연관된 객체를 찾는다.
- 테이블과 객체 사이에는 이런 큰 간격이 있다.



#### 연관관계 매핑 이론

__단방향 매핑__

```java
객체 지향 모델링 (객체의 참조와 테이블의 외래 키를 매핑)
@Entity
Public class Member{
	@Id @GeneratedValue
	private Long id;
	
	@Column(name ="USERNAME")
	private String name;
	private int age;
	
//	@Column(name = "TEAM_ID")
//	private Long teamId;

	@ManyToOne
	@JoinColumn(name = "TEAM_ID")
	private Team team;
}

//팀 저장
Team team = new Team();
team.set("teamA");
Repository.save(team);
//맴버 동록
Member member = new Member();
membr.setName("cjsong");
member.setTeamId(team); //단방향 연관관계 설정, 참조 저장
Repository.save(member);

//맴버 조회할 때
Member findMember = em.find(Member.class, member.getId());
Team findTeam =findMember.getTeamId();


```

#### 양방향 매핑

__연관관계의 주인과 mappedBy__

객체와 테이블이 관계를 맺는 차이

- 객체 연관관계
  - 회원 -> 팀 연관관계 1개 (단방향)
  - 팀 -> 회원 연관관계 1개(단방향)
- 테이블 연관관계
  - 회원 <-> 팀의 연관관계 1개 (양방향)

__객체의 양방향 연관관계__

>객체의 양방향 관계는 사실 양방향 관계가 아니라 서로 다른 단방향 관계 2개다
>
>객체를 양방향으로 참조하려면 단방향 연관관계를 2개 만들어야한다.



__테이블의 양방향 연관관계__

>테이블은 외래 키 하나로 두 테이블의 연관관계를 관리
>
>MEMBER.TEAM_ID 외래 키 하나로 양방향 연관관계 가짐(양쪽으로 조인 할 수 있다.)
>
>```
>Select *
>FROM MEMBER M
>JOIN TEAM T ON M.TEAM_ID = T.TEAM_ID
>
>SELECT *
>FROM TEAM T
>JOIN MEMBER M ON T.TEAM_ID = M.TEAM_ID
>```

![image](https://user-images.githubusercontent.com/59730002/77084317-276c0d80-6a42-11ea-9a1f-a6fb74a0eae4.png)



### 연관 관계의 주인(Owner)

__양방향 매핑 규칙__

- 객체의 두 관계중 하나를 연관관계의 주인으로 지정
- 연관관계의 주인만이 외래 키를 관리(등록, 수정)
- 주인이 아닌쪽은 읽기만 가능
- 주인은 mappedBy 속성 사용 X
- 주인이 아니면 mappedBy 속성으로 주인 지정

### 누구를 주인으로?

----------------------

- 외래 키가 있는 곳을 주인으로 정해라
- 위의 사진에서는 Member.team이 연관관계의 주인
  - 진짜 매핑 - 연관관계의 주인 (Member.team)
  - 가짜 매핑 - 주인의 반대편(Team.members)

### 양방향 매핑의 장점

-------------

- 단방향 매핑만으로도 이미 연관관계 매핑은 완료
- 양방향 매핑은 반대 방향으로 조회(객체 그래프 탐색) 기능이 추가된 것 뿐
- JPQL에서 역방향으로 탐색할 일이 많음
- 단방향 매핑을 잘 하고 양방향은 필요할 때 추가해도 됨 (테이블에 영향을 주지 않음)

### 

