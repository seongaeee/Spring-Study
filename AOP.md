### 핵심 업무, 공통 업무

- 전체 어플리케이션 구현 기능을 두 가지로 구분
> 1. **핵심 업무(core)** <br>
> 2. **공통 업무(cross cutting)**: 핵심 업무를 도와주는 반복적이고 부가적인 업무 <br>

![image](https://user-images.githubusercontent.com/62600984/116332303-7622d400-a80c-11eb-9f82-48d5a351c83d.png)

### OOP

- 핵심 업무 코드 중에 공통 업무 호출하는 부분이 추가됨
- 공통 업무가 필요없을 때 직접 삭제하거나, 필요하면 삽입 필요

### AOP

- Aspect-Oriented Programming, 관점 지향 프로그래밍
- AOP 프레임 워크가 동적으로 공통 업무를 핵심 업무 사이에 넣어줌
- 코드에는 공통 업무가 없다

### AOP 용어 정리

1. Joinpoint: 특정 작업이 시작되는 시점
2. Pointcut: 여러 개의 Joinpoint를 하나로 겹합
```
왜 결합할까? 적용시켜야하는 공통 기능이 같기 때문에
```
3. Advice: Joinpoint(Pointcut)에 삽입되어져 동작할 수 있는 코드(=공통기능)
4. Weaving: Adivce를 핵심 로직 코드에 삽입
5. Target: 핵심 로직을 구현하는 클래스
6. Aspect: 여러 객체에 공통으로 적용되는 공통 관점 사항

![image](https://user-images.githubusercontent.com/62600984/116334902-f2b7b180-a810-11eb-8fbe-8c1bf00d8fec.png)

### Spring AOP

- Proxy기반의 AOP
- Advice Type
```
1. Before: Target의 핵심 메소드 실행 전
2. After: Target의 핵심 메모드 실행 후
3. AfterReturning: Targer의 핵심 메소드 실행 하고 값을 리턴한 후
4. Round: Targer의 핵심 메소드 실행 전/후
5. AfterThrowing: Targer의 핵심 메소드 실행 중 예외 발생 시
```

### Advice Type: Before

### Pointcut 표현식

```
ex1. execution(* com.spring.aoq.test1.*Service.find*(..) )

필수- execution: 지정어
필수- *: 리턴 타입
- com.spring.aoq.test1: 패키지
- *Service: 클래스 타입
필수- find*: find로 시작하는 메소드
필수- (..): 메소드 파라메터 
```
```
ex2.excution (*send(*)):

- return: 아무거나
- send: send 함수
- (*): single parameter
```
```
ex3.excution(*send(int,..))

- return: 아무거나
- send: send 함수
- (int,..): int, 0~여러개
```
 
