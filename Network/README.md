<details>
<summary>HTTP</summary>
<div>

## HTTP 란?
- 인터넷에서 데이터를 주고 받을 수 있는 프로토콜(규칙) 입니다.
- OSI 4계층 TCP/IP 위에서 작동
- Stateless 하다(통신간 연결 상태, 정보 저장을 관리할 필요가 없다)

### 단점
- HTTP는 서버에서 브라우저로 전송되는 정보가 암호화 되지않아 데이터가 쉽게 도난 당할 수 있습니다 따라서 보안을 강화하고자 나온게 HTTPS

### HTTPS 란?
- 보안 문제를 해결해주는 프로토콜이며, SSL 프로토콜을 사용한다.
- body message만 암호화, 헤더는 x

### SSL 이란?
- Secure Socket Layer로 인터넷을 통해 전달되는 정보를 보호하기 위한 통신 규약
- 공개키/ 개인키 대칭키 기반으로 사용함
  - 대칭키 - 동일한 키로 암호화 복호화 수행
  - 비대칭키(공개키) - 서로 다른 키로 암호화(공개키) 복호화(개인키) 수행

### SSL 통신 과정
- 공개키 방식으로 대칭키를 전달 그리고 이 대칭키로 암호화 복호화 수행후 서버와 브라우저간 통신

</div></details>

<br>
<details>
<summary>RESTful</summary>
<div>

### RESTful API 라는 말도 있는데 이건 무엇인가?
- API?
  - 두 애플리케이션이 서로 통신하는 방법을 정의
- REST 아키텍처 스타일로 요청과 응답하는 API

### REST란?
- URI만 봐도 무엇인지 한눈에 파악 가능
- ex
  - GET /student/class
  - GET /student/class/1
  - DELETE /student/class/1

### REST ful?
- REST의 제약을 준수했다.

## REST 정의
- REST(Representational State Transfer)
  - 서버와 클라이언트 간 통신 방식 중 하나
  - 자원을 이름으로 구분하고
  - 자원의 상태를 주고 받는다
### REST 구현?
- 자원: URI
  - /student/class
- 행위 또는 상태 : HTTP METHOD
  - GET/POST/PUT/DELETE
- 표현: 요청 ACCEPT HEADER
  - text/html,image/gif 등등
  - -> 클라이언트 어떤 타입으로 응답 받을지 정하는 것

### URI 규칙?
- 슬래시 구분자 통해 계층 관계나타냄
- 언더바 대신 하이픈
- 대문자 대신 소문자
- 마지막에는 슬래시 포함 안함
- 


### RESTful 하게 자원을 주고받는 법?
### HTTP method
- GET
  - 자원을 검색할 때
- POST
  - 자원을 생성할 때
- PUT
  - 자원을 업데이트할 때
  - 보내지않은 정보는 null
- PATCH
  - 자원을 업데이트할 때
  - 보내지않은 데이터는 기존 데이터 유지
- DELETE
  - 자원을 삭제할 때

### HTTP 상태 코드
- 1xx
  - 조건부 응답
- 2xx
  - 성공
- 3xx
  - 리다이렉션
- 4xx
  - 클라이언트 오류
- 5xx
  - 서버 오류

</div></details>

<br>

<details>
<summary>대칭키/공개키</summary>
<div>

### 대칭키
- 암호화와 복호화를 같은 키를 사용하는 방식
- 동일한 키를 주고 받기 때문에 매우 빠르지만 대칭키를 전달하는 과정에서 해킹 위험에 노출된다.
  - DES,3DES,SEED,ARIA

### 공개키
- 암호화와 복호화에 사용하는 암호키를 분리하는 알고리즘이다
- 자신이 가지고있는 고유한 비밀키로만 복호화할 수 있는 공개키를 대중에게 공개
- 대칭키의 단점을 해결했지만 암호화 복호화가 매우 복잡하다
  - RSA,DSA

### 두개가 쓰이는 예시?
- 두 방식을 적적히 혼합하면 SSL이 됩니다.
  - 대칭키를 주고받을 때만 공개키 암호화 방식을 사용하고 이후에는 계속 대칭키 암호화 방식으로 통신
</div></details>