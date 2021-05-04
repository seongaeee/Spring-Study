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
- `@SpringBootApplication`: 서버 시작 (메인 클래스, 부트스트랩 클래스 시작 클래스)
```
@SpringBootApplication 구성 요소
- @SpringBootConfiguration: =@Configuration. xml문서를 대신해서 설정 정보를 가지고 있는 클래스
- @EnableAutoConfiguration: 자동 설정 작업을 활성. 생성자가 필요로 하는 빈을 예상하고 생성 & 설정
- @ComponentScan: 사용자가 만든 것을 현재 package부터 시작해서 하위 패키지를 스캔 한 후 객체 생성 & 주입
```
- `@MapperScan`: java mapper(Dao)를 ServiceImpl
```
@MapperScan(basePackages = {"com.mvc.dao"})
```
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

<br>

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

<br>

✏️ **Swagger**

- API의 추가 또는 변경 시 문서에 적용해야 하는 불편함 해소
- 간단한 설정으로 API 목록을 `웹에서 확인과 테스트` 가능하게 해준다.
> API? Application Programing Interface, 응용프로그램에서 데이터를 주고 받기 위한 방법

<br>

1. 라이브러리 추가
```
<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui -->
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>2.9.2</version>
</dependency>

<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger2 -->
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>2.9.2</version>
</dependency>
```
<br>

2. SwaggerConfiguration.java 추가

3. Controller에 `@ApiOperation` 추가
```java
@ApiOperation(value = " " , notes = " ")
```
