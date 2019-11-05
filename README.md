# japshop

- [실전! 스프링 부트와 JPA 활용1 - 웹 애플리케이션 개발](https://www.inflearn.com/course/스프링부트-JPA-활용-1#)
- [실전! 스프링 부트와 JPA 활용2 - API 개발과 성능 최적화](https://www.inflearn.com/course/스프링부트-JPA-API개발-성능최적화#)



## View

- 스프링 부트 thymeleaf viewName 매핑의 기본은 `resources:templates/ +{ViewName}+ .html`
- `spring-boot-devtools`라이브러리를 추가하고 html 파일을 컴파일 해주면 서버 재시작 없이 View 파일 변경이 가능(Intellij Menu > build > Recompile)



## H2

모든 로그 출력은 가급적 로거를 통해 남겨야 한다.

```yaml
spring:
  datasource:
    url: jdbc:h2:tcp://localhost/~/jpashop;MVCC=TRUE
  username: sa
  password:
  driver-class-name: org.h2.Driver

  jpa:
    hibernate:
      ddl-auto: create
    properties:
      hibernate:
      # show_sql: true #System.out 에 하이버네이트 실행 SQL을 남긴다.
      format_sql: true
    database-platform: org.hibernate.dialect.H2Dialect

logging.level:
  org.hibernate.SQL: debug #logger를 통해 하이버네이트 실행 SQL을 남긴다.
# org.hibernate.type: trace
```