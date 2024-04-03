# 자료구조

### 해시 테이블(Hash Table)

<details>

<summary>해시 테이블이란?</summary>
<p>


해시 테이블은 key-value 쌍으로 값을 저장하는 자료구조로, 검색 시간 복잡도 `O(1)` 을 가지고 있는 것이 특징입니다.
</details>

<br>

<details>
<summary>해시 테이블의 검색 시간 복잡도가 어떻게 O(1)을 유지할 수 있나요?</summary>
<div>
<p>

### 내부적으로 버킷(배열)을 사용하여 데이터를 저장하기 때문입니다

해시 테이블은 각각의 key 값에 hash function 을 적용해 배열의 고유한 index 를 생성하고, 이 index 를 활용하여 값을 저장하거나 검색합니다.

여기서 실제 값이 저장되는 장소를 버킷 또는 슬롯 이라고 합니다.
</div>
</details>

<br>

<details>
<summary>해시 함수에는 어떤 것들이 있나요?</summary>
<div>
<p>

#### hash function 에서 가장 중요한 것은 고유한 인덱스 값을 설정하는 것이며, 대표적으로 다음과 같은 해시 함수가 있습니다

- Division Method : 나눗셈을 이용하는 방법으로, 입력값을 테이블의 크기로 나누어 계산 (주소 = 입력값 % 테이블의 크기)
- Digit Folding : 각 Key의 문자열을 ASCII 코드로 바꾸고 값을 합한 데이터를 테이블 내의 주소로 사용
- Multiplication Method : 숫자로 된 Key 값 `K` 와, 0과 1 사이의 실수 `A`, 보통 2의 제곱수인 `m` 을 사용하여 `h(k) = (kAmod1) * m`
- Univeral Hashing : 다수의 해시 함수를 만들어 집합 H에 넣어 놓고, 무작위로 해시 함수를 선택해 해시값을 만드는 기법
</div>
</details>

<br>

<details>
<summary>Hash Collision 에 대하여 알고 있나요?</summary>
<div>
<p>

Hash table 에서 key 값은 무한하지만, Hash function 을 통해 나온 hash 값은 유한합니다.
따라서 특정 hash 값(index) 이 겹치는 key 가 존재할 수 밖에 없습니다.
이렇게 서로 다른 key에 대해서 같은 hash 값을 갖는 경우를 hash collision 이라고 합니다.


이를 해결하는 방법은 chaining 방식, open addressing 방식 등이 있습니다.

### Chaining

버킷 내에 연결 리스트(Linked List)를 할당하여, 버킷에 데이터를 삽입하다가 해시 충돌이 발생하면 연결 리스트로 데이터들을 연결하는 방식

### Open Addressing

체이닝의 경우 버킷이 꽉 차더라도 연결리스트로 계속 늘려가기에, 데이터의 주소값은 바뀌지 않는다. (Closed Addressing)

하지만, 개방 주소법의 경우에는 해시 충돌이 일어나면 다른 버킷에 데이터를 삽입하는 방식이다.

Open Addressing 에는 대표적으로 3가지가 있다

### Linear Probing(선형 탐색)

해시 충돌시 다음 버켓, 혹은 몇 개를 건너뛰어 데이터를 삽입

### Quadratic Probing(제곱 탐색)

해시 충돌시 제곱만큼 건너뛴 버켓에 데이터를 삽입 (1, 4, 9, 16 ...)

### Double Hashing(이중 해시)

해시 충돌시 다른 해시함수를 한번 더 적용한 결과를 이용

</div>
</details>
