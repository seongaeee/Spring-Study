📝 **SpringBoot 특징**

- Spring의 경우 사전에 많은 작업을 해야했다.
- `dependency`는 자동 설정한다.
- `서버`는 자동 시작한다.
- `xml`이 사라지고 java가 대신한다.
- WAS가 아닌 Jar파일로 실행 가능하기 때문에, 내장 서버가 있고 WAS(tomcat) 필요가 없다.
- `자동 설정`이 가장 큰 특징이다.
<br>

https://start.spring.io/

<br>

✏️ **SpringBoot 클래스**

1. SpringbootApplication
- `@SpringBootApplication`: 설정 파일
```
- @SpringBootConfiguration: =@Configuration. xml문서를 대신해서 설정 정보를 가지고 있는 클래스
- @EnableAutoConfiguration: 자동 설정 작업을 활성. 생성자가 필요로 하는 빈을 예상하고 생성 & 설정
- @ComponentScan: 사용자가 만든 것을 현재 package부터 시작해서 하위 패키지를 스캔 한 후 객체 생성 & 주입
```
- 시작 클래스, main으로 실행 가능

<br>

2. application.properties
- properties 설정
- ex. 포트 번호, Mysql, MyBatis 설정 
```
ex. Mysql Data base setting
spring.datasource.driver-class-name=
spring.datasource.url=
spring.datasource.username=
spring.datasource.password=
```
```
ex. MyBatis
mybatis.type-aliases-package=
mybatis.mapper-locations=
```

3. interceptor 추가하기
```
@Configuration
public class WebConfiguration extends WebMvcConfigurerAdapter {

  @Autowired
  private Confirminterceptor confirminterceptor
  
  @Override
  public void addInterceptor() {
    
  }
}

```
