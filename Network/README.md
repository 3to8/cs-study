# Network


### TCP

<details>
<summary>TCP란?</summary>

<br>

<div>
데이터를 안정적으로 전송하기 위한 프로토콜입니다.
신뢰성 있는 통신을 제공하며 흐름제어, 혼잡제어, 오류제어라는 특징을 가지고 있습니다.
</div>

* TCP 특징
1. 신뢰성 보장 
   * 데이터의 안전한 도착을 위해 확인 응답 기법을 사용합니다.
2. 흐름 제어
   * 수신자와 송신자간의 통신 속도를 제어하여 수신자가 처리할 수 있는 속도보다
   * 더 빠르게 전송되지 않도록 조절합니다.
3. 혼잡 제어
   * 혼잡 윈도우, 혼잡 상황 감지, 수신자의 응답을 통한 조절이 있습니다.
   * 혼잡 윈도우는 송신자가 네트워크에 전송할 수 있는 최대 데이터의 양을 나타냅니다.
   * 혼잡 상황 감지는 데이터 전송 중 패킷이 손실 되거나 전송이 지연된다면 혼잡 상황으로 감지합니다.
   * 수신자는 받은 패킷을 확인해 수용 가능한 양을 송신자에게 전달합니다.
     * 송신자는 데이터 전송 속도를 조절 해 혼잡 상황을 완화시킵니다.
4. 오류 제어
   * 훼손된 세그먼트를 감지해 재전송하거나 손실된 세그먼트를 재전송,
   * 순서가 맞지 않는 세그먼트를 저장하고 중복 세그먼트를 감지하고 폐기하는 메커니즘이 포함됩니다.
   * 각 세그먼트에 존재하는 checksum 필드를 확인해 검사를 진행합니다.
5. 전이중 통신 지원
   * 수신자와 송신자가 동시에 데이터를 송수신 할 수 있습니다.
</details>

<details>
<summary>세그먼트</summary>

<br>

<div>
세그먼트는 TCP에서의 데이터 전송의 기본 단위입니다.
세그먼트는 헤더와 페이로드로 구성됩니다.
</div>

#### 세그먼트
* 헤더
  * 데이터 전송에 필요한 제어 정보가 포함됩니다.
    * 송수신자 포트번호, 확인 응답 번호, 플래그가 포합됩니다.
    * 헤더의 정보를 통해서 데이터의 순서를 관리하고 오류 제어, 흐름 제어를 수행합니다.
* 페이로드
  * 송신자가 전송하는 실제 데이터가 포합됩니다.
</details>

### UDP

<details>
<summary>UDP란?</summary>

<br>

<div>
UDP는 보안과 신회성보다 전송 속도와 효율성이 더 중요한 경우 사용하는 프로토콜입니다.
또한 UDP는 비연결형 서비스로 송수신자가 연결을 설정하지 않아 빠른 속도로 전송할 수 있습니다.
하지만 연결을 확인하지 않기 때문에 패킷이 손실될 가능성이 있습니다.
</div>
</details>

<br>

<details>
<summary>UDP 특징</summary>

<br>

<div>
UDP는 일부 패킷이 누락되더라도 데이터를 전송하므로 패킷 손실로 인해 전체 전송이 중단되지 않습니다.
하지만 패킷이 목적지에 성공적으로 도달했는지 여부를 확인하지 않으며 전송 도중 패킷이 손실되어도 수신자는 확인하지 못합니다.
UDP 헤더의 CheckSum 필드를 통해 최소한의 오류만 검출합니다.
<br>

또한 UDP는 패킷의 도착 순서를 보장하지 않습니다.
</div>
</details>

<br>

<details>
<summary>TCP와 UDP의 차이</summary>

<br>

<div>
TCP는 연결형 서비스로 패킷을 교환하는 방식이고 UDP는 비연결형 서비스로 데이터그램을 전송하는 방식입니다.
또한 TCP는 패킷의 전송 순서를 보장하지만 UDP는 전송 순서를 보장하지 않아 순서가 변경될 수 있습니다.
TCP는 혼잡제어, 흐름제어, 오류제어를 통해 신뢰성을 보장하지만 UDP는 최소한의 오류만 검출하므로 신뢰성이 낮습니다.
</div>

* HTTP1, HTTP2는 TCP로 통신하였지만 HTTP3부터는 UDP가 기본 프로토콜로 지정되었습니다.
</details>

### 3way handshake

<details>
<summary>3way handshake란?</summary>

<br>

<div>
TCP/IP 프로토콜을 이용해 통신하기 전에 통신을 보장하기 위해 상대방과 가상의 회선을 수립하는 과정입니다.
</div>

#### SYN
* 연결을 설정합니다.
* Sequence Number를 랜덤으로 설정해 세션을 연결하는 데 사용됩니다.
  * Connnection시 Sequence Number를 랜덤하게 설정하는 이유는 포트의 수가 유한하기 때문에 이후에 다시 재사용합니다.
  * 그 경우 순차적인 번호를 사용하게 되면 이전 Connection에서 전송된 패킷으로 인식할 수 있기 때문에 랜덤한 값을 사용합니다.

#### ACK
* 응답을 확인합니다. 패킷을 전송받았다는 것을 의미합니다.
* 첫 번째 세그먼트를 제외하고 나머지 모든 세그먼트 들의 ACK 비트는 1로 설정됩니다.

#### FIN
* 연결을 종료할 때 사용하며 더이상 전송할 데이터가 없음을 의미합니다.
</details>

<br>

<details>
<summary>3way handshake 과정</summary>

<br>

<div>

1. Client가 Server로 SYN 플래그를 전송합니다.
2. Server는 Listen 상태에서 SYN 플래그를 받아 SYN-RECV 상태로 바뀌며 SYN + ACK 플래그를 전송합니다.
3. Client는 SYN + ACK 플래그를 받아 ACK 플래그로 응답하며 연결이 성립됩니다.

</div>

#### 서버 상태
* CLOSED : 포트가 닫혀 있는 상태
* LISTEN : 포트가 열려 연결 요청을 대기중인 상태
* SYN_RECV : SYNC 요청을 받고 상대의 응답을 기다리는 상태
* ESTABLISHED : 포트가 연결된 상태
* TIME-WAIT : FIN 플래그를 받은 후 일정 시간동안 잉여 패킷을 기다리는 상태
</details>

### 4way handshake

<details>
<summary>4way handshake</summary>

<br>

<div>
연결되어 있는 세션을 종료하기 위해 수행되는 절차입니다.

1. Client가 종료를 위해 FIN 플래그를 전송합니다.
   * Client의 상태가 FIN-WAIT-1로 변경됩니다.
2. 서버에서 ACK 응답을 보냅니다. 이후 서버는 CLOSE_WAIT, Client는 FIN-WAIT-2 상태로 변경됩니다.
3. 서버에서 FIN 플래그를 보냅니다.
4. Client가 ACK 응답을 보냅니다.
   * 의도치 않은 에러로 연결이 데드락에 빠지는것을 방지하기 위해 TIME-WAIT 상태로 변경됩니다.
   * 일정 시간이 지난 후 CLOSED 상태가 됩니다.
</div>
</details>

### Cookie

<details>
<summary>Cookie란?</summary>

<br>

<div>
서버가 사용자의 웹 브라우저에 전송하는 데이터입니다.
브라우저에 저장된 쿠키는 동일한 서버에 다시 요청 시 함께 전송합니다.
Stateless한 특성이 있는 HTTP에서 상태 정보를 기억하기 위해 사용합니다.
</div>
</details>

#### 전송 과정
* 서버에서 응답을 전송할 때 Set-Cookie 헤더에 데이터를 넣어 같이 전송합니다.
* 응답을 받은 브라우저는 쿠키 저장소에 Cookie를 Key-Value 형태로 저장합니다.
* 이 후 같은 서버로 요청을 보낼 때 요청의 Cookie 헤더에 데이터를 넣어 같이 전송합니다.


* Cookie는 HTTP 요청마다 쿠키를 넣어서 전송하므로 네트워크 트래픽에 부담을 줄 수 있습니다.
<br>

<details>
<summary>Cookie의 종류</summary>

<br>

<div>
쿠키는 세션쿠키와 영속적인 쿠키가 있습니다.

세션 쿠키는 수명이 지정되지 않은 쿠키로 브라우저가 종료될 때 같이 삭제됩니다.
영속적인 쿠키는 수명이 지정되어 있는 쿠키로 `Expire`, `Max-Age`에 명시된 기간 이후 삭제됩니다.
</div>
</details>

<details>
<summary>Cookie 옵션</summary>

<br>

<div>
Cookie의 옵션에는 범위를 지정할 수 있는 Domain, Path,
보안과 관련된 Secure, HttpOnly, 수명을 지정하는 Max-Age, Expire가 있습니다.
</div>

#### Domain
* 브라우저에 저장된 Cookie는 생성된 Domain과 일치하는 경우에만 전달합니다.
  * ex) ex1.hun.com에서 생성한 Cookie는 ex2.hun.com에 요청할 때 전송하지 않습니다.
  * Domain을 .hun.com으로 설정 시 두 도메인 모두 전송할 수 있습니다.

#### Path
* 같은 Domain에서 Path에 따라 Cookie를 전송할지 결정할 수 있습니다.
  * ex) path를 /public 으로 설정 시 /private 으로는 전송하지 않습니다.

#### Max-Age
* 쿠키의 수명을 초 단위로 설정할 수 있습니다.

#### Expire
* 쿠키의 수명을 특정요일로 설정할 수 있습니다.

<br>

* Max-Age와 Expire가 같이 설정되어 있을 경우 Max-Age의 값으로 설정됩니다.
  * 두 속성을 모두 사용하는 이유는 HTTP 1.0에서는 Max-Age를 지원하지 않으므로 하위 호환성을 위해서 같이 사용합니다.

#### Secure
* Secure 옵션을 통해 HTTPS 요청에만 전송하도록 설정할 수 있습니다.

#### HTTPOnly
* HTTP 뿐 아니라 Javascript에서도 Cookie를 조회, 수정이 가능합니다.
  * document.cookie
* HTTPOnly 옵션을 통해 Cookie의 값을 Javascript에서 조회, 수정을 막을 수 있어 쿠키가 위조를 방지할 수 있습니다.
</details>

### Session

<details>
<summary>Session 이란?</summary>

<br>

<div>
상태가 없는 HTTP에서 일정시간동안 여러 요청을 하나의 상태로 유지시키는 기술입니다.
브라우저에 저장되는 Cookie와는 다르게 서버에 저장됩니다.
클라이언트를 구분하기 위해 SESSION ID를 부여해 브라우저를 종료할 때 까지 인증 상태를 유지합니다.
</div>

#### Session 동작방식
1. SESSIONID 발급
2. 클라이언트가 요청 시 SESSIONID를 서버에 전달해서 요청 
3. SESSIONID에 일치하는 데이터를 가져와 응답


* Session은 정보를 서버에 저장하므로 사용자가 많아질수록 많은 메모리를 차지하게 됩니다.
</details>

<br>

<details>
<summary>Cookie, Session 차이</summary>

<br>

<div>
Session도 Cookie를 사용하므로 동작은 비슷하지만 Cookie는 정보를 브라우저에 저장하고 Session은 서버에 저장합니다.
보안 면에서는 Cookie보다 Session이 우수하지만 요청 속도는 Cookie가 더 빠릅니다.
</div>
</details>

