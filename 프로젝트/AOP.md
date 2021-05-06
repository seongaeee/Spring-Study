참고 블로그: https://sabarada.tistory.com/95

<br>

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
