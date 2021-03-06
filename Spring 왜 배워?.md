## SPRING

- **enterprise application**에서 필요로 하는 기능을 제공하는 프레임워크
- 웹 애플리케이션 컨테이너와 상관없이 **독립적으로 객체를 관리하는 컨테이너** 프레임워크
- **IoC패턴**을 통한 모듈 간의 의존도 최소화

![image](https://user-images.githubusercontent.com/62600984/116487530-23f4b800-a8cb-11eb-8705-4bb1464b6bc5.png)

<br>

:star2: **CONTAINER**

- life cycle: **객체(bean)의 생성, 유지, 삭제 관리**
- 코드가 변화될때 컴파일을 다시 안하기 때문에 유연성 높음

:link: **XML**

- 컨테이너가 미리 생성해서 대기시켜 놓은 **객체들에 관한 정보**
- bean 설정 file

<br>

:star2: **IoC 패턴**

- Inverse of Control, 제어의 역전
- 기존의 클래스에서 객체를 만들때 "new"를 이용해서 만들었지만, IoC에서는 컨테이너가 만들어줘서 주기때문에 제어를 가져간다.
- DI(Dependency Injection, 의존성 주입): 컨테이너에서 받음(setter와 생성자로 만들어진것을 받음)
- DL(Dependecy Lookup): 컨테이너에서 찾아옴(커넥션풀)
- 쓰이는 이유? 
> 자바에서 인터페이스를 인스턴스화하기 위해서는, 반드시 객체 생성에 필요한 코드 작성 <br>
> 결합도 완전히 없애기 힘듬
- Ioc 패턴을 쓴다면?
> 누군가에게 의존성을 대신 주입하여, **자신이 해야하는 일들을 하지않고 통과할 수 있음**


