참고 블로그: https://recordsoflife.tistory.com/448

<br>

1. jsp (form)

- method="post"
- enctype="multipart/form-data"
- type="file"
- name="upfile"
```
<form id="writeform" method="post" enctype="multipart/form-data" action="">
    <label for="subject">파일</label>
    <input type="file" class="form-control-file border" name="upfile" multiple="multiple">
</form>
```

<br>

2. FileDto
```java
private String saveFolder;
private String originFile;
private String saveFile;
```

3. controller
