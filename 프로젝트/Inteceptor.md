참고 블로그: https://aljjabaegi.tistory.com/531


![image](https://user-images.githubusercontent.com/62600984/117326009-37f07900-aecc-11eb-8780-d25b302b9492.png)

<br>

**1. 예외 코드 만들기**
```
@Configuration
```
```
extends HandlerInterceptorAdapter
```
✏️ 오버라이드 함수
- preHandle
- postHandle
```
@Override
public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler)
    throws Exception {

  HttpSession session=request.getSession();
  if(session.getAttribute("id") != null) { //로그인ok
    return true;
  }
  else {
    response.sendRedirect("loginForm.bod");
    return false;
  }
}
```

<br>


**2. 인터셉터 등록하기**

✏️ 등록 함수
- addInterceptor: 인터셉터 추가
- addPathPatterns: 동작할 url 패턴 등록
```
@Configuration 
public class WebMvcConfig implements WebMvcConfigurer{ 
    
    @Autowired 
    private LoginCheckInterceptor interceptor; 
    
    @Override 
    public void addInterceptors(InterceptorRegistry registry) { 
        registry.addInterceptor(interceptor) .addPathPatterns("/"); 
    }
}

```
