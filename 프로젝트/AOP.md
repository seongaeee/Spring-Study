참고 블로그: https://sabarada.tistory.com/95

<br>

**0.pom.xml 추가**
```
<!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->		
		
<dependency>
  <groupId>javax.annotation</groupId>
  <artifactId>javax.annotation-api</artifactId>
  <version>1.3.2</version>
</dependency>

<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-aop</artifactId>
    <version>3.0.7.RELEASE</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.aspectj/aspectjrt -->
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjrt</artifactId>
    <version>1.7.3</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.aspectj/aspectjweaver -->
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.6.7</version>
</dependency>
```

**1. application.java에서 aspect 활성화**
```java
@EnableAspectJAutoProxy
```

<br>

**2. aspect 만들기**
- aspect 선언
```java
@Aspect
@Component
```

- pointcut 선언(ex)
```java
@Before("execution(void set*(*))")
```
