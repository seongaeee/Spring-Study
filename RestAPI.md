✏️ **OPEN API**

<br>

✏️ **REST**

1. REST란?
- `URI + POST/GET/PUT/DELETE(CRUD)`
- URI을 통해 자원을 명시하고, Method를 통해 자원을 제어하는 명령을 내리는 방식

2. REST 구성
- 자원: URI
- 행위: HTTP Method
- 표현

3. 기존 Service와의 차이?
- 기존 Service는 data를 적절히 처리하여 특정 플랫폼에 적합한 View를 만들어 넣는다.
- 하지만, REST Service는 `View에 신경 쓸 필요 없다.`

![image](https://user-images.githubusercontent.com/62600984/116837521-c5e70e00-ac05-11eb-8d5f-4ada523db477.png)

사진출처 https://www.joinc.co.kr/w/man/12/rest/about 

4. REST API
- JSON 변환
- XML 변환

5. 어노테이션
- `@ResponseBody`: 뷰로 전달되는 것이 아닌 데이터 자체 전달
- `@RestController`: Controller가 REST방식을 처리
- `@PathVariable`: URL에 있는 값을 추출
