### Mybatis

1. 명령어 중간에 '<' , '>'가 들어가면?

- CDATA 사용
- https://epthffh.tistory.com/entry/Mybatis-%EC%97%90%EC%84%9C-CDATA-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0

2. 마지막 값을 얻어올려면?

```
<!-- 방금 쓴 글(AFTER)의 articleno를 얻어옴 -->
<selectKey resultType="int" keyProperty="articleno" order="AFTER">
    SELECT LAST_INSERT_ID()
</selectKey>
```

3. 동적 명령어 생성 할려면?

- foreach
```
<!-- fileinfos: list(collection), separator: for문이 돌때마다 ','을 넣어라 -->
<foreach collection="fileInfos" item="fileinfo" separator=" , ">
    (#{articleno}, #{fileinfo.saveFolder}, #{fileinfo.originFile}, #{fileinfo.saveFile})
</foreach>
```

- if
```
<if test="word != null and word != ''">
  <if test="key == 'subject'">
    where subject like concat('%', #{word}, '%')
  </if>
  <if test="key != 'subject'">
    where ${key} = #{word}
  </if>
</if>
```

4. Map을 만들어 return을 할려면? - 1개 리턴

- resultMap
```
<resultMap type="GuestBookDto" id="guestBookList">
  <result property="no" column="no"/>
  ...
  <collection property="fileInfos" column="articleno" javaType="list" ofType="FileInfoDto" select="fileInfoList"/>
</resultMap>
```

- select 구문(resultMap)
```
<select id="listArticle" parameterType="map" resultMap="guestBookList">
```

5. 여러 개 return 할려면?

- resultType을 dto로 설정하면 됨


### jsp

1. jsp에서 파일 리스트 띄우기
```
<c:if test="${!empty article.fileInfos}">
<tr>
  <td colspan="2">
<ul>
  <c:forEach var="file" items="${article.fileInfos}">
    <li>${file.originFile} <a href="#" class="filedown" sfolder="${file.saveFolder}" sfile="${file.saveFile}" ofile="${file.originFile}">[다운로드]</a>
  </c:forEach>
</ul>
</td>
</tr>
</c:if>
```
