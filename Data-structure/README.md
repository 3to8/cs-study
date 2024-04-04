# Data Structure

### Stack

<details>
<summary>Stack 이란?</summary>

<br>

<div>
Stack은 선형 자료구조로 가장 마지막에 저장된 데이터를 먼저 가져오는 LIFO 방식의 자료구조입니다.
스택의 가장 위에서 데이터의 삽입, 삭제, 조회가 이루어 집니다.
</div>
</details>

### Queue

<details>
<summary>Queue란?</summary>

<br>

<div>
Queue는 선형 자료구조로 가장 먼저 저장된 데이터를 먼저 가져오는 FIFO 방식의 자료구조입니다.
</div>
</details>

### Heap

<details>
<summary>Heap이란?</summary>

<br>

<div>
Heap이란 최대 값이나 최솟값을 찾아내는 연산을 빠르게 하기 위해 고안 된 완전 이진 트리를 기본으로 한 자료구조 입니다.
Heap에는 최소 Heap과 최대 Heap이 있습니다. Heap의 삽입과 삭제의 시간 복잡도는 O(log N)입니다.
Heap은 우선순위 큐나 힙 정렬에 사용되며 최대/최솟값 검색 작업을 효율적으로 처리할 수 있습니다.
</div>
</details>

<br>

<details>
<summary>최대 힙, 최소 힙</summary>

<br>

<div>
최대 힙은 부모 노드의 키 값이 자식 노드의 키 값보다 크거나 같은 완전 이진 트리입니다.
반대로 최소 힙은 부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리입니다.
</div>
</details>

<br>

<details>
<summary>Heap의 삽입 연산</summary>

<br>

<div>
완전 이진 트리를 유지하기 위해 삽입되는 데이터는 왼쪽 최하단 노드부터 채워집니다.
이후 채워진 위치에서 부모 노드의 값을 확인 해 정렬하는 과정을 반복합니다.
삽입 연산의 시간 복잡도는 O(log N) 입니다.
</div>
</details>

<br>

<details>
<summary>Heap의 삭제 연산</summary>

<br>

<div>
heap의 표준 삭제 연산은 힙의 루트 노드를 삭제합니다.
최대 힙인 경우 최댓값을 삭제 하고 최소 힙인 경우 최솟값을 삭제합니다.
루트 노드의 값을 마지막 노드의 위치를 변경해 삭제한 후 정렬하는 과정을 반복합니다.
삭제 연산의 시간 복잡도는 O(log N)입니다.
</div>
</details>

### Priority Queue

<details>
<summary>Priority Queue란?</summary>

<br>

<div>
우선순위 큐란 우선순위를 가진 항목을 저장하는 큐로 FIFO 구조가 아닌
우선순위가 높은 데이터가 먼저 나오는 자료구조입니다.

일반적으로 힙을 이용해 구현하며, 배열과 연결리스트를 이용해 구현할 수 있습니다.

</div>

#### 우선순위 큐 시간 복잡도
* 힙으로 구현이 된 경우 삽입과 삭제에 O(log N)입니다.
* 정렬된  배열과 정렬된 연결리스트에서 삽입은 O(n), 삭제는 O(1) 입니다.
</details>