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

<br>

<details>
<summary>어노테이션</summary>
<div>

### 어노테이션 이란?
- 인터페이스를 기반으로 주석처럼 코드에 달아 클래스에 특별한 의미를 부여 또는 기능을 주입

### 어떻게 선언하나?
- 메타 어노테이션이라는 어노테이션을 선언할 때 사용하는 어노테이션을 사용
  - @Retention
    - 유지 범위 지정 (소스,클래스, 런타임)
  - @Inherit
    - 어노테이션을 하위 클래스까지 전달할지 여부 지정
  - @Target
    - 어디에 사용할것인지(타입, 필드, 메서드, 파라미터, 생성자, 로컬 변수, 어노테이션 타입)

</div>
</details>

<br>

<details>
<summary>GC</summary>
<div>

### GC(Garbage Collector)
- 동적으로 할당한 메모리 영역중 사용하지 않는 영역을 탐지해 해제하는 기능

#### Heap 영역
- 모든 Object 타입의 데이터가 할당, Heap 영역의 Object를 가리키는 참조 변수는 stack에 할당

### 어떤 객체가 Garbage?
- 유효한 참조가 존재하는 객체는 Reachable 상태
- 그렇지 않다면 Unreachable 상태
  - 이것이 GC의 수거 대상
- Root set과의 참조 관계로 reachable,unreachable 구분
- Root set?
  - stack 영역의 지역변수, 파라미터
  - Method 영역의 정적 변수
  - JNI에 의해 생성된 객체

### 그럼 어떻게 작동하는건가? Mark and Sweep
- Root set으로부터 Heap 영역의 모든 객체를 스캔해 Reachable한 객체를 찾는다
  - MARK
- Unreachable한 객체는 Heap영역에서 제거
  - SWEEP

### JVM Heap 메모리 영역에 대해 설명해봐라
- Heap은 young generation, old generation으로 분류된다.
  - 두개로 나뉘는 이유?
    - 하나의 메모리 영역이라면 너무 많아 부하가 발생할 수 있음
    - 대부분 오랫동안 참조되지않으면 금방 Garbage 대상이 된다
    - 그럼으로 효율적인 처리 가능
    - 영역을 나누어 스캔하니까

### 그럼 언제 GC가 발생하는가?
- young generation -> Minor Gc
- old generation -> Major Gc
- young generation 3개로 나뉨
  - Eden - 새로운 객체가 저장되는 영역
  - Survivor0 - eden 영역에서 살아 남은 객체가 저장되는 영역
  - Survivor1
- Eden이 가득차면 Minor Gc 발생하고 Mark and Sweep이 일어나며 Unreachable한 객체는 해제된다.
- 여기서 살아 남은 객체는 비어있는 Survivor로 옮겨진다(옮겨진 객체의 age는 1 증가)
- 계속 반복하며 age가 특정값 이상되면, old generation으로 이동(promotion)(기본적으론 31)
- old generation이 가득차면 여기서 마찬가지로 GC가 발생하며 이를 Major Gc라 한다

</div>
</details>