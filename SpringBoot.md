π **SpringBoot νΉμ§**

- Springμ κ²½μ° μ¬μ μ λ§μ μμμ ν΄μΌνλ€.
- `dependency`λ μλ μ€μ νλ€.
- `μλ²`λ μλ μμνλ€.
- `xml`μ΄ μ¬λΌμ§κ³  javaκ° λμ νλ€.
- WASκ° μλ JarνμΌλ‘ μ€ν κ°λ₯νκΈ° λλ¬Έμ, λ΄μ₯ μλ²κ° μκ³  WAS(tomcat) νμκ° μλ€.
- `μλ μ€μ `μ΄ κ°μ₯ ν° νΉμ§μ΄λ€.
<br>

https://start.spring.io/

<br>

βοΈ **SpringBoot ν΄λμ€**

1. SpringbootApplication
- `@SpringBootApplication`: μλ² μμ (λ©μΈ ν΄λμ€, λΆνΈμ€νΈλ© ν΄λμ€ μμ ν΄λμ€)
```
@SpringBootApplication κ΅¬μ± μμ
- @SpringBootConfiguration: =@Configuration. xmlλ¬Έμλ₯Ό λμ ν΄μ μ€μ  μ λ³΄λ₯Ό κ°μ§κ³  μλ ν΄λμ€
- @EnableAutoConfiguration: μλ μ€μ  μμμ νμ±. μμ±μκ° νμλ‘ νλ λΉμ μμνκ³  μμ± & μ€μ 
- @ComponentScan: μ¬μ©μκ° λ§λ  κ²μ νμ¬ packageλΆν° μμν΄μ νμ ν¨ν€μ§λ₯Ό μ€μΊ ν ν κ°μ²΄ μμ± & μ£Όμ
```
- `@MapperScan`: java mapper(Dao)λ₯Ό ServiceImpl
```
@MapperScan(basePackages = {"com.mvc.dao"})
```
<br>

2. application.properties
- properties μ€μ 
- ex. ν¬νΈ λ²νΈ, Mysql, MyBatis μ€μ  
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

3. interceptor μΆκ°νκΈ°
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

βοΈ **Swagger**

- APIμ μΆκ° λλ λ³κ²½ μ λ¬Έμμ μ μ©ν΄μΌ νλ λΆνΈν¨ ν΄μ
- κ°λ¨ν μ€μ μΌλ‘ API λͺ©λ‘μ `μΉμμ νμΈκ³Ό νμ€νΈ` κ°λ₯νκ² ν΄μ€λ€.
> API? Application Programing Interface, μμ©νλ‘κ·Έλ¨μμ λ°μ΄ν°λ₯Ό μ£Όκ³  λ°κΈ° μν λ°©λ²

<br>

1. λΌμ΄λΈλ¬λ¦¬ μΆκ°
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

2. SwaggerConfiguration.java μΆκ°

3. Controllerμ `@ApiOperation` μΆκ°
```java
@ApiOperation(value = " " , notes = " ")
```
