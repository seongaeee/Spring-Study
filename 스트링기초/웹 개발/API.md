๐ฏ **API ์ฌ์ฉ ๋ฐฉ๋ฒ** <br>

<br>

โ๏ธ **@RespnseBody** <br>

- ํด๋น http์ <body>๋ถ๋ถ์ ๊ทธ๋๋ก ๊ฐ์ ๋ฃ์ <br>

<br>

โ๏ธ **@RespnseBody ๊ฐ ์ข๋ฅ** <br>

1. String
```java
@GetMapping("hello-string")
@ResponseBody
public String helloString(@RequestParam("name") String name){
    return  "hello"+name; //"hello spring"
}
```

2. Json
```java
@GetMapping("hello-api")
@ResponseBody
public Hello helloApi(@RequestParam("name") String name){
    Hello hello = new Hello();
    hello.setName(name);
    return  hello;
}

static class Hello{
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```
![image](https://user-images.githubusercontent.com/62600984/116550534-dd867400-a931-11eb-914b-9d86d339140d.png)
