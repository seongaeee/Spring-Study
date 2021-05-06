📝 **FileUpload**

<br>

0. pom.xml
```
<dependency>
    <groupId>commons-fileupload</groupId>
    <artifactId>commons-fileupload</artifactId>
    <version>1.4</version>
</dependency>
```

1. servlet-context.xml
- `maxUploadSize`: 한번에 올릴 수 있는 파일의 용량

2. jsp(form 설정)
- `method="post"`: 파일 업로드는 반드시 post방식
- `enctype="multipart/form-data"`: 파일을 서버에 전송
- `type=file`: 파일을 자동으로 찾아줌

3. FileDto
- 저장 날짜
- 저장 이름: 서버에 저장되기 때문에 파일 이름 그대로 저장되면 다른 사람과 겹침, 유일값을 만들어야된다. (uuid/현재날짜)
- 원본 이름
```
private String saveFolder; //저장 날짜
private String originFile; //원본 이름
private String saveFile; //저장 이름
```

```
mfile.tranferTo: 서버에 전송
```

2. ServiceImpl
- `@Transacrtion`: 중간에 오류가 생기면 롤백해줌
- `fileRegister`: 파일에 대한 정보를 DB에 넣기

3. Mapper - upload
- `selectKey`: 방금 쓴 글 번호를 리턴
- `foreach`: 업로드 파일이 여러 개 있을 때 동적으로 쿼리 만들기

4. Mapper - select
- `resultType`: 결과물을 해당 타입으로 넣음

