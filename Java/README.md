<details>
<summary>'=='과 equals 차이점</summary>
<div>

### 배경
- primitive 타입의 비교는 == 이라는 연산자를 사용한다. 하지만 String 같은 class의 값을 비교할때는 == 이 아닌 equals()라는 메서드를 사용해서 비교합니다.

#### String 생성시 주소 할당 방법
- 리터럴
- new 연산자

#### 리터럴 사용시 Heap안의 String constant pool이라는 영역에 존재하며, new로 생성시 Heap 영역에 존재

### 차이점
- '==' 연산자는 같은 메모리를 참조하는가를 비교
  - 리터럴 생성시 같은 Heap안의 String pool에 저장되기 때문에 주솟값이 같지만 new 연산시 다른 Heap 영역에 저장됨으로 같다고 비교하지 않는다.
- equals()는 두 비교대상의 주소 값이 아닌 데이터 값을 비교
</div>
</details>