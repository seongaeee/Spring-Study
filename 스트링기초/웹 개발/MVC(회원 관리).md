๐ฏ **MVC๋ฅผ ํ์ฉํด์ ํ์ ๊ด๋ฆฌ ์ฑ์ ๋ง๋ค์ด๋ณด์**

<br>

๐ **Controller**

1. GetMapping
- ์ฌ์ฉ์๊ฐ ์ฃผ์์ฐฝ์ ์ง์  ํ์ดํํ์ฌ ๋ค์ด๊ฐ ๋
```java
@GetMapping("members/new")
public String createForm() {
    return "members/createMemberForm";
}
```
2. PostMapping
- Form์ ํตํด ํ์ด์ง ์ด๋ํ  ๋
- Form์์ ๋ณด๋ธ ์ ๋ณด๋ฅผ controller์์ ๊ฐ์ฒด๋ฅผ ์ด์ฉํด์ ๋ฐ์๋ค.
- ์ด ๋, Form์ name๊ณผ ๊ฐ์ฒด์ ๋ณ์ ์ด๋ฆ์ด ๊ฐ๋ค๋ฉด ์๋์ผ๋ก ๊ฐ์ฒด์ ์ ๋ณด๊ฐ ์ ์ฅ๋๋ค.
```
<form action="/members/new" method="post">
    <input type="text" id="name" name="name" placeholder="์ด๋ฆ ์๋ ฅ">
</form>
```
```java
public class MemberForm {
    private String name;
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
```
```java
@PostMapping("/members/new")
public String create(MemberForm form) {
    Member member = new Member();
    member.setName(form.getName());
    memberService.join(member);
    return "redirect:/";
}
```

3. return
- ์ด๋ํ  view ์ ๋ฌ
- `redirect:/`: request, responese ์๋กญ๊ฒ ์์ฑ

<br>

๐ **Model**

- controller์์ ํ์ด์ง ์ด๋์ ํ  ๋
- Model์ ์ ๋ณด๋ฅผ ๋ด์ผ๋ฉด html๋ก ์ ๋ฌ ๊ฐ๋ฅํ๋ค.
- `addAttribute`ํจ์๋ฅผ ์ด๋ค.
```java
@GetMapping("/members")
public String list(Model model) {
    List<Member> members = memberService.findMembers();
    model.addAttribute("members", members);
    return "members/memberList";
}
```

<br>

๐ **View**

- Model์ ํตํด ๋ฐ์ ์ ๋ณด๋ฅผ
- `${}`์ ์ด์ฉํ์ฌ ๊บผ๋ด์ ์ฌ์ฉํ๋ค.
```
<tr th:each="member : ${members}">
    <td th:text="${member.id}"></td>
    <td th:text="${member.name}"></td>
</tr>
```
