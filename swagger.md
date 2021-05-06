**0. pom.xml에 추가**
```
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

**1. config.java 파일 생성**

```java
@Configuration
@EnableSwagger2
public class SwaggerConfig {
	
	@Bean
	public Docket api() {
		return new Docket(DocumentationType.SWAGGER_2)
				    .select() //초기화
					.apis(RequestHandlerSelectors.basePackage("com.mvc.controller")) //basePackage를 대상으로 스웨거 문서로 만들어짐		
					.paths(regex("/customers/*.*")) //요청 경로(정규표현식)
					.build() //docket객체 생성
					.apiInfo(info()); //추가적인 정보
	}
	
	private ApiInfo info() {
		return new ApiInfoBuilder()
				.title("제목")
				.description("<h2>설명</h2>")
				.version("1.0")
				.build();
	}
}
```

<br>

**2. controller에서 어노테이션 추가**
```
@ApiOperation(notes = "설명", value = "제목")
```

<br>

**3. 결과 확인**
- Swagger 설정 확인: http://localhost/v2/api-docs
- Swagger-UI 확인: http://localhost/swagger-ui.html
