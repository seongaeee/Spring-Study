### IoC 패턴

- 스프링에서의 의존성 주입

---

:seedling: **기본 인터페이스 사용**

- info 메서드를 사용하기 위해서는 Coffee 타입을 가진 클래스의 인스턴스 생성(new)이 필요

1.인터페이스
```java
public interface Coffee {
	public void info();
}
```
2.클래스
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
3.코드
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

1. 스트링 라이브러리 추가
```
- SPRING-MVC, SPRING-JDBC, SPRING-Context
- SPRING-Core: 위의 모듈이 공통으로 사용하는 라이브러리
```

2. 스프링 applicationContext.xml

1) applicationContext.xml 설정
```
- resources폴더에 xml 파일 생성
- bean 태그 id에는 "참조에 사용할 값"
- bean 태그 class에는 "실제 클래스 파일 경로"
- property는 다른 클래스 또는 인터페이스를 멤버 변수로 가지고 있는 경우에 쓰임
- 인터페이스에서 property가 쓰일 때 ref 태그를 사용해서 클래스 명시(bean id)함 
```
```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

	<bean id="menu1" class="com.coffee3.Americano"></bean>
	<bean id="menu2" class="com.coffee3.CaffeLatte"></bean>

	<bean id="myMenu1" class="com.coffee3.Coffee"
		<property name="info">
			<ref bean="menu1"/>
		</property>
	</bean>
	
	<bean id="myMenu2" class="com.coffee3.Coffee"
		<property name="info">
			<ref bean="menu2"/>
		</property>
	</bean>
</beans>
```

2) applicationContext.xml 사용
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
		
		context.close();
	}

}
```

