### MyBatis란?

- **Java Object와 SQL문 사이의 자동 Mapping기능**을 지원하는 ORM Framework (Object-Relation Mappring)
- SQL을 별도의 파일(XML)로 분리해서 관리
- table안에 들어잇는 레코드 1건에 대한 정보 = VO 객체 1개
- VO 객체를 변경하면 해당 레코드의 정보도 자동 변경됨

### sqlSession

- Query를 실행시킬 수 있는 메소드 <br>
- TX 관리 메소드(commit, rollback) <br>
- sqlSessionFactoryBuilder -(환경정보:build(.xml))-> sqlSessionFactory -(openSession(mapper file))-> sqlSession

### 참고 블로그
https://pangtrue.tistory.com/141
https://m.blog.naver.com/PostView.nhn?blogId=wwwkang8&logNo=220989381100&proxyReferer=https:%2F%2Fwww.google.com%2F
