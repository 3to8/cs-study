# Operating System

### Interrupt

<details>
<summary>Interrupt란?</summary>
<br>
<div>
CPU가 프로그램을 실행중일 때 여러 하드웨어 장치에서 예외상황이 발생해 처리가 필요한 경우
CPU에게 알려 처리할 수 있도록 하는 것입니다.

인터럽트가 발생한 시점의 레지스터와 Program Counter를 저장한 후 CPU의 제어를 인터럽트 처리 루틴으로 전달합니다.

</div>

</details>

<br>

<details>
<summary>Interrupt 종류</summary>

<br>

<div>
하드웨어 인터럽트와 소프트웨어 인터럽트가 있습니다.

하드웨어 인터럽트는 입출력 장치나 CPU에 연결된 주변기기에서 인터럽트가 발생하는 것이고,
소프트웨어 인터럽트는 프로그램 처리 중 명령의 요청에 의해서 발생합니다.
</div>
</details>

<br>

<details>
<summary>Interrupt의 동작 순서</summary>

<br>

<div>
인터럽트 요청이 발생하면 현재 실행중인 프로그램을 중단합니다.
현재 실행중인 프로그램의 상태를 저장합니다.

<br>

인터럽트 요청이 발생한 장치를 식별한 후 인터럽트 서비스 루틴을 호출해 처리합니다.

인터럽트 처리가 끝나 상태복구 명령어가 실행되면, 저장된 Program Counter값을 통해 이전 실행 위치로 돌아가 수행중이던 프로그램을 재개합니다.

</div>
</details>

<br>

<details>
<summary>Interrupt와 Polling의 차이</summary>
<br>

<div>
Polling이란 CPU가 주변 기기들의 변화를 지속적으로 읽어 처리되어야할 작업을 찾는 과정입니다.

Polling은 CPU가 특정 이벤트를 처리하기위해 해당 이벤트가 발생할 때까지 주기적으로 확인해야합니다.
Interrupt는 다른 작업을 처리하다가 이벤트가 발생하면 인터럽트 핸들러를 호출해 작업을 처리합니다.
</div>

</details>

<details>
<summary>Interrupt Handler</summary>

<br>

<div>
인터럽트가 발생했을 때 인터럽트에 대응하여 이벤트를 처리하는 루틴입니다.
인터럽트 서비스 루틴이라고 부르기도 합니다.

CPU가 인터럽트 발생을 감지했을 때 CPU로부터 제어권을 넘겨받아 인터럽트를 처리합니다.
</div>
</details>

