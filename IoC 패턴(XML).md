### IoC 패턴

- 스프링에서의 의존성 주입

---

:seedling: **기본 인터페이스 사용**

- info 메서드를 사용하기 위해서는 Coffee 타입을 가진 클래스의 인스턴스 생성(new)이 필요

**1.인터페이스**
```java
public interface Coffee {
	public void info();
}
```
**2.클래스**
```java
public class Americano implements Coffee {
	public void info() {
		System.out.println("에스프레소 샷과 뜨거운 물이 조합된 음료");
	}
}
```
```java
public class CaffeLatte implements Coffee {
	public void info() {
		System.out.println("에스프레소 샷과 따뜻한 우유와 거품이 조합된 음료");
	}
}
```
**3.서비스코드**
```java
public class CoffeeService {
	Coffee coffee;
	public void setCoffee(Coffee coffee) {
		this.coffee=coffee;
	}
	public void askCoffee() {
		System.out.print(coffee.info());
	}
}
```
**4.실행코드**
```java
public class CoffeeShop {
	public static void main(String[] args) {
		Coffee cof;
		cof = new Americano();
		cof.info();
		cof = new CaffeLatte();
		cof.info();
	}
}

//결과
//Americano:강렬한 에스프레소 샷과 뜨거운 물의 조화
//CaffeLatte:에스프레소 샷과 따뜻한 우유와 거품으로 마무리된 음료
```

---

:seedling: **스트링 XML 설정**

- 스트링 컨테이너에 클래스 등록하면, 스트링이 클래스의 인스턴스 관리
- 스트링 컨테이너에 빈을 등록하고 설정하는 방법: XML, 어노테이션

<br>

**1. 스트링 라이브러리 추가**
```
- SPRING-MVC, SPRING-JDBC, SPRING-Context
- SPRING-Core: 위의 모듈이 공통으로 사용하는 라이브러리
```

**2. 스프링 applicationContext.xml**

**2-1. applicationContext.xml 설정**
```
- resources폴더에 xml 파일 생성
- bean 태그 id에는 "참조에 사용할 값" (xml내에서 참조하기 위한 것, 없어도됨)
- bean 태그 class에는 "실제 클래스 파일 경로"
- 생성자 주입: <constructor-arg name=" " value=" "/>, 꼭 넣어야됨
- setter 주입: <property name=" " value=" "></property> 
- ref 태그: 객체 참조
- value 태그: 값  
```
```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

	<bean id="menu1" class="com.coffee3.Americano"></bean>
	<bean id="menu2" class="com.coffee3.CaffeLatte"></bean>

	<bean id="myMenu1" class="com.coffee3.CoffeeService">
		<property name="coffee">
			<ref bean="coffee1"/>
		</property>
	</bean>
	
	<bean id="myMenu2" class="com.coffee3.CoffeeService">
		<property name="coffee">
			<ref bean="coffee2"/>
		</property>
	</bean>
</beans>
```

**2-2. applicationContext.xml 사용**
```
getBean을 사용할 때, bean id와 bean의 (상속)클래스명 입력
```
```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class CoffeeShop {

	public static void main(String[] args) {
	
		ApplicationContext context=new ClassPathXmlApplicationContext("coffee.xml");
		
		Coffee cof=context.getBean("menu1", Coffee.class);
		cof.info();
		
		CoffeeService mycoffee1=context.getBean("myMenu1", CoffeeService.class);
		mycoffee1.askCoffee();
		CoffeeService mycoffee2=context.getBean("myMenu2", CoffeeService.class);
		mycoffee2.askCoffee();
		
		context.close();
	}

}
```

**3. 빈 생명주기 제어**

- 빈의 생성 여부와 소멸 여부를 직접 파악하기 위해 콜백 메서드 등록

**3-1.init-method**

- 처음 초기화되면 호출될 메서드
```java
public class Americano implements Coffee {
	public void info() {
		System.out.println("에스프레소 샷과 뜨거운 물이 조합된 음료");
	}
	public void onCreated() {
		System.out.println("Americano 생성");
	}
}
```
```java
<bean id="coffee1" class="com.coffee3.Americano" init-method="onCreated"></bean>
```

**3-2.destroy-method**

- 종료시 호출될 메서드

```java
<bean id="coffee1" class="com.coffee3.Americano" init-method="onCreated" destroy-method="onDestroyed"></bean>
```
```java
public class CoffeeApp {
	public static void main(String[] args) {
		GenericXmlApplicationContext context=new GenericXmlApplicationContext("classpath:coffee.xml");
		Coffee cof=context.getBean("coffee1", Coffee.class);
		Coffee cof3=context.getBean("coffee1", Coffee.class);
		CoffeeService mycoffee1=context.getBean("myMenu1", CoffeeService.class);
		
		Coffee cof2=context.getBean("coffee2", Coffee.class);
		CoffeeService mycoffee2=context.getBean("myMenu2", CoffeeService.class);
		context.close();
	}
}

//결과
//Americano 생성
//CaffeLatte 생성
//Americano 소멸
//CaffeLatte 
```
