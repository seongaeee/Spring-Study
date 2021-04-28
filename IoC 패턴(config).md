### config

XML을 사용하지 않고, 자바 코드만으로 컨테이너 설정


1. XML에서 annotation기능 활성화
```
<context:component-scan base-package="패키지명"/>
```

2. 클래스 bean 만들기
- @Component: xml문서에서 <bean>태그를 대신해서 객체를 생성

```java
@Component
public class CoffeeBean implements CoffeeShop{
}
```

3. 의존성 주입
- @Autowired: xml문서에서 생선된 객체 중에 '타입'을 기준으로 자동 주입(Americano타입을 찾아 자동 주입)
- @Resource: xml문서에서 생성된 객체 중에 'name'을 기준으로 자동 주입(name이 ame인 것)
```java
@Component
public class CoffeeBean implements CoffeeShop{
	
	@Resource
	Americano ame; 
	
	@Resource
	CaffeLatte latte;
}
```
