# Spring Framework & Vue.js

##### 자바로 개발하는데 있어 유용하고 편리한 기능을 제공하는 프레임워크

##### 핵심 기술

- 스프링은 톰켓을 이용할 수 있으며 코드의 경량화 그리고 개발 중에 테스트가 쉽다는 특징이 있다.
- 경량 컨테이너로서 자바 객체를 직접 관리한다. 각각의 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있다.
- 스프링은 MyBATIS나 Hibernate 등  이미 완성도가 높은 데이터베이스 처리 라이브러리와 연결 할 수 있는 인터페이스를 제공한다.
- 스프링은 확정성이 높다. 스프링 프레임워크에 통합하기 위해 간단하게 기존 라이브러리를 감싸는 정도로 스프링에서 사용이 가능하기 때문에 수많은 라이브러리가 이미 스프링에서 지원되고 있고 스프링에서 사용되는 라이브러리를 별도로 분리하기도 용이하다.

##### 제어 역행(IOC : Inversion of Control)

> 컨트롤의 제어권이 사용자가 아니라 프레임워크에 있어 필요에 따라 스프링에서 사용자의 코드를 호출한다.

>일반적인 (의존성에 대한) 제어권 : "내가 사용할 의존성은 내가 만든다"

```java
class OwnerController{
	private OwnerRepository repository = new 		OwnerRepository();
}
```

>##### IoC : "내가 사용할 의존성을 누군가 알아서 주겠지"
>
>- 내가 사용할 의존성의 타입(또는 인터페이스)만 맞으면 어떤거든 상관없다.
>- 그래야 내 코드 테스트 하기도 편하지.



```
class OwnerController{
    private OwnerRepository repo;
    public OwnerContoller(OwnerRepository repo){
        this.repo = repo;
    }

    //repo를 사용합니다.
}

class OwnerControllerTest{
	@Test
	public void create(){
		OwnerRepository repo = new OwnerRepository();
		OwnerController controller = new OwnerController(repo);
	}
}
```

##### DI(Dependency Injection)

> 스프링 컨테이너가 지원하는 핵심 개념 중 하나로, 설정 파일을 통해 객체간의 의존관계를 설정하는 역할을 합니다. 각 클래스 사이에 필요로 하는 의존관계를 Bean 설정 정보 바탕으로 컨테이너가 자동으로 연결합니다. 객체는 직접 의존하고 있는 객체를 생성하거나 검색할 필요가 없으므로 코드 관리가 쉬워지는 장점이 있습니다.



>@Autowired / @Inject를 어디에 붙일까?
>
>- 생성자
>- 필드
>- Setter
>
>







##### Bean

>Bean은 IoC Container가 관리하는 객체
>
>**의존성 주입은 Ioc Container에 존재하는 Bean끼리만 가능**
>
>##### 등록 방법
>
>- Component Scanning
>  - @Component
>    - @Repository
>    - @Service
>    - @Controller
>- 또는 직접 일일히 XML이나 자바 설정 파일에 등록
>
>##### 사용 방법
>
>- @Autowired 또는 @Inject
>- 또는 ApplicationContext에서 getBean()으로 직접 꺼내거나



##### Dispatcher-Servlet

> 서블릿 컨테이너에서 HTTP 프로토콜을 통해 들어오는 모든 요청을 제일 앞에서 처리해주는 프론트 컨트롤러를 말함
>
> 따라서 서버가 받기 전에, 공통처리 작업을 디스패처 서블릿이 처리해주고 적절한 세부 컨트롤러를 작업을 위임해줍니다.
>
> 디스패처 서블릿이 처리하는 URL 패턴을 지정해줘야 하는데, 일반적으로 .mvc와 같은 패턴으로 처리하라고 미리 지정해줍니다.
>
> 디스패처 서블릿으로 인해 web.xml이 가진 역할이 상당히 축소되었습니다. 기존에는 모든 서블릿을 url 매핑 활용을 위해 모두 web.xml에 등록해 주었지만, 디스패처 서블릿은 그 전에 모든 요청을 핸들링해주면서 작업을 편리하게 할 수 있도록 도와줍니다. 또한, 이 서블릿을 통해 MVC를 사용할 수 있기 때문에 웹 개발 시 큰 장점을 가져다 줍니다.

#### AOP(Aspect Oriented Programming)

> 공통의 관심 사항을 적용해서 발생하는 의존 관계의 복잡성과 코드 중복을 해소해줍니다.
>
> 각 클래스에서 공통 관심 사항을 구현한 모듈에 대한 의존관계를 갖기 보단, Aspect를 이용해 핵심 로직을 구현한 각 클래스에 공통 기능을 적용합니다.
>
> 간단한 설정만으로도 공통 기능을 여러 클래스에 적용할 수 있는 장점이 있으며 핵심 로직 코드를 수정하지 않고도 웹 애플리케이션의 보안, 로깅, 트랜잭션과 같은 공통 관심 사항을 AOP를 이용해 간단하게 적용할 수 있습니다.





##### DAO(Data Access Object)

> DB에 데이터를 조회하거나 조작하는 기능들을 전담합니다.
>
> Mybatis를 이용할 때는, mapper.xml에 쿼리문을 작성하고 이를 mapper 클래스에서 받아와 DAO에게 넘겨주는 식으로 구현합니다.



##### Annotation

> 소스코드에 @어노테이션의 형태로 표현하며 클래스, 필드, 메소드의 선언부에 적용할 수 있는 특정기능이 부여된 표현법을 말합니다.
>
> 애플리케이션 규모가 커질수록, xml 환경설정이 매우 복잡해지는데 이러한 어려움을 개선시키기 위해 자바 파일에 어노테이션을 적용해서 개발자가 설정 파일 작업을 할 때 발생시키는 오류를 최소화해주는 역할을 합니다.
>
> 어노테이션 사용으로 소스 코드에 메타데이터를 보관할 수 있고, 컴파일 타임의 체크뿐 아니라 어노테이션 API를 사용해 코드 가독성도 높여줍니다.

- @Controller : dispatcher-servlet.xml에서 bean 태그로 정의하는 것과 같음
- @RequestMapping : 특정 메소드에서 요청되는 URL과 매칭시키는 어노테이션
- @Autowired : 자동으로 의존성 주입하기 위한 어노테이션
- @Service : 비지니스 로직 처리하는 서비스 클래스에 등록
- @Repository : DAO에 등록



##### Spring JDBC

> 데이터베이스 테이블과, 자바 객체 사이의 단순한 매핑을 간단한 설정을 통해 처리하는 것
>
> 기존의 JDBC에서는 구현하고 싶은 로직마다 필요한 SQL 문이 달랐고, 이에 필요한 Connection, PrepareStatement, ResultSet 등을 생성하고 Exception 처리도 모두 해야하는 번거러움이 존재했습니다. 
>
> Spring에서는 JDBC와 ORM 프레임워크를 직접 지원하기 때문에 따로 작성하지 않아도 모두 다 처리해주는 장점이 있습니다.



##### MyBatis

> 객체, 데이터베이스, Mapper 자체를 독립적으로 작서어하고, DTO에 해당하는 부분과 SQL 실행결과를 매핑해서 사용할 수 있도록 지원함
>
> 기존에는 DAO에 모두 SQL문이 자바 소스상에 위치했으나, MyBatis를 통해 SQL은 XML 설정 파일로 관리합니다.
>
> 설정파일로 분리하면, 수정할 때 설정 파일만 건드리면 되므로 유지보수에 매우 좋습니다. 또한 매개변수나 리턴 타입으로 매핑되는 모든 DTO에 관련된 부분도 모두 설정파일에서 작업할 수 있는 장점이 있습니다.



#### Spring Boot vs Spring

> Spring Boot는 Spring 프레임워크를 사용하는 프로젝트를 아주 간편하게 셋업할 수 있는 스프링 프레임워크의 서브 프로젝트 개념이라고 생각. 프로젝트 생성시에 기존의 Spring에서 하듯 복잡한 설정이 아닌 통합된 설정파일인 application.yml으로 쉽게 간단하게 사용



> Web기반인 애플리케이션은 Tomcat이든 Was든 Web Container가 설치 되어있어야한다. 하지만 규모가 작은 형태의 애플리케이션을 실행시키기 위해 그보다 큰 WAS를 설치하기엔 비효율적 그래서 Boot 사용





