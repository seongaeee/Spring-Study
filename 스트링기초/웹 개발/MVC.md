๐ฏ **MVC์ ๊ฐ๋๊ณผ ๋์ ๊ณผ์ **

<br>
<br>

โ๏ธ **MVC๋?** <br>
Model, View, Controller๋ก ๋๋์ด ์์ฒญ ํ์ด์ง ์ฒ๋ฆฌ

<br>

โ๏ธ **MVC์ ๋์ ๊ณผ์ ** <br>
- `์คํ๋ง ๋ถํธ`๋ `์คํ๋ง ์ปจํ์ด๋`์์ http ํ์ด์ง์ `Controller`๋ฅผ ์ฐพ๋๋ค. <br>
- ์ปจํธ๋กค๋ฌ์์ ๋ฆฌํด๋ view ์ด๋ฆ๊ณผ model ๊ฐ์ `viewResolver`๊ฐ ๋ฐ๊ณ 
- thymeleaf ํ๋ธ๋ฆฟ ์์ง ์ฒ๋ฆฌ๋ฅผ ํ์ฌ view๋ฅผ ๋ฆฌํดํด์ค๋ค. <br>

<br>

**์ฌ์ฉ์์๊ฒ ์๋ ฅ๊ฐ์ ๋ฐ์ ๋**
```java
public String helloMvc(@RequestParam("name") String name, Model model){
    model.addAttribute("name", name);
    return "hello-template";
}
```
