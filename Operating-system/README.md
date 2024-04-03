# 운영체제

## Lock

[reference](https://hyeo-noo.tistory.com/105)

<details>

<summary>Lock 이 필요한 이유?</summary>
<p>

2개 이상의 Thread가 동시에 공유 자원에 접근할 경우 race condition(병행성 문제)가 발생하여 결과를 예측할 수 없게 됨

- 따라서 공유 자원에 대한 동기화 메커니즘이 필요한데, 그중 가장 일반적인 매커니즘이 Lock 이다

</details>

<br>

<details>

<summary>Critical Section ?</summary>
<p>

- 공유 자원에 접근하는 코드의 조각

</details>

<br>

<details>

<summary>Mutual Exclusion ?</summary>
<p>

**Mutual Exclusion 은 병행성 해결 이라는 뜻**

- Critical Section 은 하나의 부분인 것처럼 실행되어야 함 (Atomically)
- Critical Section 은 한 번에 하나의 쓰레드만 실행이 가능함
- 다른 모든 쓰레드들은 Critical Section 에 진입하기 위해서 현재 사용 중인 쓰레드가 종료될 때까지 entry 에서 기다려야 함

</details>

<br>

<details>

<summary>Lock의 기본 개념</summary>
<p>

- Critical Section 에 진입하기 전에 lock 을 얻고, critical section이 끝나는 경우에 lock 을 반납

</details>

<br>

<details>

<summary>Lock이 제공해야 하는 기능</summary>
<p>

## Correctness, Fairness, Performance

### Correctness

- Mutual Exclusion : 한 번에 하나의 쓰레드만 Critical Section에 진입할 수 있게 해야 함
- Progress : Dead-lock 상태(모두가 Lock을 얻지 못하고, Critical Section 에 진입할 수 없는 상태)가 발생해서는 안됨
- Bounded : 일정 시간 이상 기다리면, lock 을 얻을 수 있게 보장해야 함 (starvation-free)

### Fairness

- 모든 쓰레드는 lock 을 얻는 데 공평한 기회를 가져야 함

### Performance

- lock 을 얻으려는 쓰레드 수에 따른 Time overhead 에 관한 내용

</details>

<br>