# Backend

## JWT

<details>

<summary>JWT 란?</summary>
<p>

JWT 는 Json Web Token 의 약자로, 인증에 필요한 정보를 암호화시킨 토큰입니다.

토큰 기반 인증에 사용되며, Claim 형식으로 토큰 자체에 사용자의 정보가 들어있는 것이 특징입니다

</details>

<br>

<details>

<summary>JWT 인증 방식</summary>
<p>

1. 사용자가 로그인 시 올바른 사용자임을 확인하고 Access Token(JWT) 발급

2. 클라이언트는 전달받은 토큰을 저장해 두고(static or local), 인증이 필요한 요청마다 토큰을 HTTP 헤더에 담아 보냄

3. 서버에서는 토큰을 Base64 Decoding -> 서명(Signature) 확인, expire 확인 등을 통하여 올바른 토큰인지 확인하는 과정(인증) 을 거침

4. 인증이 완료되면 서버는 요청에 응답

</details>

<br>

<details>

<summary>토큰 기반 인증 방식의 장/단점</summary>
<p>

## 장점

- Access Token 을 발급해 준 후, 요청이 들어오면 검증만 해주면 됨
  - 추가 저장소가 필요 없으므로 stateless
- 쿠키를 사용함으로 인해 발생하는 취약점 사라짐(쿠키 탈취 등)
- 확장에 용이함 (stateless)

## 단점

- 이미 발급된 토큰을 되돌릴 수 없음. 한번 발급되면 유효기간이 완료될 때까지는 계속 사용이 가능
- 길이가 길어서 인증이 필요한 요청이 많아지면, 서버의 자원 낭비가 발생

</details>

<br>

<details>

<summary>JWT의 구조에 대해 설명해 주세요</summary>
<p>

### JWT 의 구조는 총 세 부분으로 나눠집니다.

헤더(header), 페이로드(payload), 시그니처(signature)

- header: signature 의 해싱 알고리즘, 토큰의 type 이 포함되어 있습니다
- payload: 사용자의 claim 이 포함되어 있습니다. 총 3가지 종류의 claim 이 존재합니다. (registered claim, private claim, public claim)
- signature: 토큰의 유효성을 검증하는 데에 사용되며, 각각의 header, payload 를 BASE64 인코딩한 값을 합쳐서 header 의 비밀키 + 해싱 알고리즘으로 해쉬 하여 생성되며, 이 생성된 해쉬를 다시 BASE64 인코딩 한 값 

</details>

<br>

<details>

<summary>Access Token 과 Refresh Token은 무엇인가요?</summary>
<p>

- Access Token 은 특정 권한을 얻기 위하여 사용하는 토큰이며, Refresh Token 은 해당 토큰을 재발급 받기 위한 토큰입니다
- JWT 는 stateless 하기 때문에, 서버 측에서 이 토큰을 갖고 있는 클라이언트가 정말 클라이언트 본인이 맞는지 확인할 수 없기 때문에 사용합니다
  - 로그인 성공 시 두 토큰을 서버로부터 받아서 클라이언트에 저장
  - Access Token으로 요청을 보내다가, 유효 기간이 만료되면 `UnAuthorized` -> invalid token 임을 알 수 있음
  - 헤더에 Access Token 대신 Refresh Token 을 넣어 재 요청
  - 응답 쿼리 헤더에 새로운 Access Token 을 넣어 응답
  - Refresh Token 도 만료되었다면, `UnAuthorized` -> 재 로그인

</details>

<br>

<details>

<summary>Refresh Token 이 탈취된 경우에는?</summary>
<p>

- 데이터베이스에 사용자에 1대1 매핑되는 Access Token, Refresh Token 쌍을 저장
- 정상적인 사용자는 Access Token 으로 접근하며, 서버 측에서 데이터베이스에 저장된 Access Toekn과 비교하여 검증
- 공격자는 탈취한 Refresh Token 으로 새로 Access Token 생성, 하지만 데이터베이스에 저장된 Access Token 과 공격자로부터 받은 Access Token 이 다른 것임을 확인
- 데이터베이스에 Access Token 이 만료되지 않은 경우, 굳이 Access Token 을 새로 생성할 이유가 없는 경우 서버는 Refresh Token이 탈취되었다고 보고, 다시 재 로그인하도록 함
  - 서버는 토큰을 NoSQL 같은 데이터베이스에 저장하여 관리할 필요가 있음
  - 클라이언트는 http-only 속성이 부여된 쿠키에 저장

</details>

<br>