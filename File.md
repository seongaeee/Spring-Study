๐ **FileUpload**

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
- `maxUploadSize`: ํ๋ฒ์ ์ฌ๋ฆด ์ ์๋ ํ์ผ์ ์ฉ๋

2. jsp(form ์ค์ )
- `method="post"`: ํ์ผ ์๋ก๋๋ ๋ฐ๋์ post๋ฐฉ์
- `enctype="multipart/form-data"`: ํ์ผ์ ์๋ฒ์ ์ ์ก
- `type=file`: ํ์ผ์ ์๋์ผ๋ก ์ฐพ์์ค

3. FileDto
- ์ ์ฅ ๋ ์ง
- ์ ์ฅ ์ด๋ฆ: ์๋ฒ์ ์ ์ฅ๋๊ธฐ ๋๋ฌธ์ ํ์ผ ์ด๋ฆ ๊ทธ๋๋ก ์ ์ฅ๋๋ฉด ๋ค๋ฅธ ์ฌ๋๊ณผ ๊ฒน์นจ, ์ ์ผ๊ฐ์ ๋ง๋ค์ด์ผ๋๋ค. (uuid/ํ์ฌ๋ ์ง)
- ์๋ณธ ์ด๋ฆ
```
private String saveFolder; //์ ์ฅ ๋ ์ง
private String originFile; //์๋ณธ ์ด๋ฆ
private String saveFile; //์ ์ฅ ์ด๋ฆ
```

```
mfile.tranferTo: ์๋ฒ์ ์ ์ก
```

2. ServiceImpl
- `@Transacrtion`: ์ค๊ฐ์ ์ค๋ฅ๊ฐ ์๊ธฐ๋ฉด ๋กค๋ฐฑํด์ค
- `fileRegister`: ํ์ผ์ ๋ํ ์ ๋ณด๋ฅผ DB์ ๋ฃ๊ธฐ

3. Mapper - upload
- `selectKey`: ๋ฐฉ๊ธ ์ด ๊ธ ๋ฒํธ๋ฅผ ๋ฆฌํด
- `foreach`: ์๋ก๋ ํ์ผ์ด ์ฌ๋ฌ ๊ฐ ์์ ๋ ๋์ ์ผ๋ก ์ฟผ๋ฆฌ ๋ง๋ค๊ธฐ

4. Mapper - select
- `resultType`: ๊ฒฐ๊ณผ๋ฌผ์ ํด๋น ํ์์ผ๋ก ๋ฃ์

