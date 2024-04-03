# 네트워크

## HTTP Method

<details>

<summary>HTTP Method 란?</summary>
<p>

HTTP 메서드란 클라이언트와 서버 사이에 이루어지는 요청(Request) 과 응답(Response) 데이터를 전송하는 방식

서버에 주어진 리소스에 수행하기를 원하는 행동, 서버가 수행해야 할 동작을 지정하는 요청을 보내는 방법

- REST 에서 자원에 대한 행위(Verb)를 의미

## 주요 메서드

- GET : 리소스 조회
- POST : 요청 데이터 처리, 주로 등록에 사용
- PUT : 리소스를 대체(덮어쓰기), 해당 리소스가 없으면 생성
- PATCH : 리소스 부분 변경 (PUT은 전체 변경, PATCH는 일부 변경)
- DELETE : 리소스 삭제

## 기타 메서드

- HEAD : GET 과 동일하지만, 메세지 부분(body) 을 제외하고, 상태 줄과 헤더만 반환
- OPTIONS : 대상 리소스에 대한 통신 가능 옵션(메서드)을 설명
- CONNECT : 대상 자원으로 식별되는 서버에 대한 터널을 설정
- TRACE : 대상 리소스에 대한 경로를 따라 메세지 루프백 테스트를 수행

</details>

<br>

<details>

<summary>HTTP Method - GET</summary>
<p>

- 리소스를 조회하는 메서드 (READ)
- 전달하고 싶은 데이터는 쿼리스트링을 통하여 전달
  - `GET /member/100?username=hi`
- 조회시 POST도 사용할 수 있지만, GET 메서드는 캐싱이 가능하기에 GET을 사용하는 것이 유리함

</details>

<br>

<details>

<summary>HTTP Method - POST</summary>
<p>

- 전달한 데이터를 처리/생성 요청하는 메서드 (CREATE)
- 메세지 바디(body)를 통해 서버로 요청 데이터를 전달하면, 서버는 요청 데이터를 처리하여 업데이트
- 전달된 데이터로 주로 신규 리소스 등록 및 프로세스를 처리
- Content-Type 헤더를 통하여 함께 전송되는 body의 형식을 지정할 수 있음

### Content-Type header

- `application/x-www-form-urlencoded`
  - form의 내용을 HTTP Body를 통하여 전송 (key=value, 쿼리스트링 형식)
  - 전송 데이터를 url encoding 처리
- `multipart/form-data`
  - 파일 업로드 같은 바이너리 데이터 전송 시 사용
  - 다른 종류의 여러 파일과 form의 내용을 함께 전송 가능
- `application/json`
  - JSON 데이터 전송 시 사용

</details>

<br>

<details>

<summary>HTTP Method - PUT</summary>
<p>

- 리소스를 대체(수정)하는 메서드 (UPDATE)
- 만일 요청 메시지에 리소스가 있으면 덮어쓰고, 없으면 새로 생성
- 구체적인 전체 경로를 지정하여 보내주어야 함
  - `PUT /members/100` : 100번째 멤버 수정

</details>

<br>

<details>

<summary>HTTP Method - PATCH</summary>
<p>

- 리소스의 일부 부분을 변경하는 메서드 (UPDATE)

</details>

<br>

<details>

<summary>HTTP Method - DELETE</summary>
<p>

- 리소스를 제거하는 메서드

</details>