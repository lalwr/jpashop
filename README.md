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



## JPA

persistence.xml 도 없고, LocalContainerEntityManagerFactoryBean도 없이 스프링 부트를 통해 복잡한 설정이 다 자동화 되었다. 

'?'에 입력되는 값을 보고 싶다면 [외부 라이브러리](https://github.com/gavlyukovskiy/spring-boot-data-source-decorator)를 사용한다.  부트는 `implementation 'com.github.gavlyukovskiy:p6spy-spring-boot-starter:1.5.7'`를 추가하고 yml 파일을 수정한다.

```
logging.level:
  org.hibernate.type: trace
```

쿼리 파라미터를 로그로 남기는 외부 라이브러리는 시스템 자원을 사용하므로, 개발 단계에서는 편하
게 사용해도 된다. 하지만 운영시스템에 적용하려면 꼭 성능테스트를 하고 사용하는 것이 좋다.

