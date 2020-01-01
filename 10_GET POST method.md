# GET / POST



### 1. 요청(request) / 응답(response)

- 요청: 클라이언트가 서버에게 웹페이지를 보여달라고 하는 것

- 응답: 서버가 요청에 대한 응답으로 웹페이지 내용을 html 문서로 주는 것



### 2. HTTP 패킷

> 패킷: 인터넷을 통해 보내는 데이터. (inspect - network - headers - name)

- 헤더: 사용 메소드, 클라이언트 정보, 브라우저 정보, URL 등이 담겨 있음
  - Content-Type
- 바디: 보통 비어있으나 특정 데이터를 담아서 서버에 요청을 보낼 수 있음

![github_img](https://www.csestack.org/wp-content/uploads/2018/05/HTTP-header-in-Chrome-Inspect.png)



### 3. GET 방식 / POST 방식

> 공통점은 두 방식 모두 서버에 "요청"을 보내는 메소드. 예를 들어 로그인 할 때 클라이언트는 id와 pw를 작성하여 서버에 요청하고, 서버는 해당 id와 pw가 올바른 것인지 확인. 즉 로그인이라는 요청에 대한 정보를 담아 서버에 전송.

![github_img](https://t1.daumcdn.net/cfile/tistory/99D83C395BCB27A001)

- **GET**

  ```www.sample.com?key1=value1&key2=value2 
  www.sample.com?key1=value1&key2=value2
  ```

  - 위와 같은 URL 형식으로 서버에 데이터 전송하여 해당 URL을 요청
  - 물음표 뒤에 key-vlaue 입력 (&는 구분자 역할)
  - URL에 담은 것이기 때문에 HTTP 패킷 중 헤더에 포함 (바디는 비어있음)

  

- **POST**

  - 데이터를 HTTP 패킷 중 바디에 담아 전송
  - Header Content-Type에 데이터 타입을 명시해주어야 함

