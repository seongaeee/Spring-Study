🐯 **MVC를 활용해서 회원 관리 앱을 만들어보자**

<br>

📝 **Controller**

1. GetMapping
- 사용자가 주소창에 직접 타이핑하여 들어갈 때
```java
@GetMapping("members/new")
public String createForm() {
    return "members/createMemberForm";
}
```
2. PostMapping
- Form을 통해 페이지 이동할 때
- Form에서 보낸 정보를 controller에서 객체를 이용해서 받았다.
- 이 때, Form의 name과 객체의 변수 이름이 같다면 자동으로 객체에 정보가 저장된다.
```
<form action="/members/new" method="post">
    <input type="text" id="name" name="name" placeholder="이름 입력">
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
- 이동할 view 전달
- `redirect:/`: request, responese 새롭게 생성

<br>

📝 **Model**

- controller에서 페이지 이동을 할 때
- Model에 정보를 담으면 html로 전달 가능하다.
- `addAttribute`함수를 쓴다.
```java
@GetMapping("/members")
public String list(Model model) {
    List<Member> members = memberService.findMembers();
    model.addAttribute("members", members);
    return "members/memberList";
}
```

<br>

📝 **View**

- Model을 통해 받은 정보를
- `${}`을 이용하여 꺼내서 사용한다.
```
<tr th:each="member : ${members}">
    <td th:text="${member.id}"></td>
    <td th:text="${member.name}"></td>
</tr>
```
