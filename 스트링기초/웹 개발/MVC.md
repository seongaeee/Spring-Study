🐯 **MVC의 개념과 동작 과정**

<br>
<br>

✏️ **MVC란?** <br>
Model, View, Controller로 나누어 요청 페이지 처리

<br>

✏️ **MVC의 동작 과정** <br>
- `스프링 부트`는 `스프링 컨테이너`에서 http 페이지의 `Controller`를 찾는다. <br>
- 컨트롤러에서 리턴된 view 이름과 model 값을 `viewResolver`가 받고
- thymeleaf 템블릿 엔진 처리를 하여 view를 리턴해준다. <br>

<br>

**사용자에게 입력값을 받을 때**
```java
public String helloMvc(@RequestParam("name") String name, Model model){
    model.addAttribute("name", name);
    return "hello-template";
}
```
