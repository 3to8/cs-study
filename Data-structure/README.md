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
내부적으로 버킷(배열)을 사용하여 데이터를 저장하기 때문입니다

해시 테이블은 각각의 key 값에 hash function 을 적용해 배열의 고유한 index 를 생성하고, 이 index 를 활용하여 값을 저장하거나 검색합니다.

여기서 실제 값이 저장되는 장소를 버킷 또는 슬롯 이라고 합니다.
</div>
</details>

<br>

<details>
<summary>해시 함수에는 어떤 것들이 있나요?</summary>
<div>
hash function 에서 가장 중요한 것은 고유한 인덱스 값을 설정하는 것
</div>
</details>

<br>

<details>
<summary>Hash Collision 에 대하여 알고 있나요?</summary>
<div>
Hash table 에서 key 값은 무한하지만, Hash function 을 통해 나온 hash 값은 유한합니다.
따라서 특정 hash 값(index) 이 겹치는 key 가 존재할 수 밖에 없습니다.
이렇게 서로 다른 key에 대해서 같은 hash 값을 갖는 경우를 hash collision 이라고 합니다.

<br>

이를 해결하는 방법은 chaining 방식, open addressing 방식이 있습니다.
chaining 은 인덱스의 버킷을 연결 리스트로 구현해 
</div>
</details>
