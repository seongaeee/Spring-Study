### IoC 패턴

- 스프링에서의 의존성 주입

---

:seedling: **기본 인터페이스 사용**

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

- info 메서드를 사용하기 위해서는 Coffee 타입을 가진 클래스의 인스턴스 생성(new)이 필요

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

2. 
