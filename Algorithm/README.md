# Algorithm

---

### Bubble Sort

<details>
<summary>Bubble Sort란?</summary>
<br>
<div>
배열의 인접한 두 수를 비교해 순서대로 정렬되어 않다면 두 수의 위치를 변경하며 정렬하는 방법입니다.

<br>

배열의 정렬 여부와는 상관없이 2개의 원소를 비교하기 때문에 평균, 최악, 최선의 경우 모두 O(n^2)의 시간 복잡도를 가집니다.
</div>

* 구현 방법
```java
    void bubbleSort(int[] arr) {
        int temp = 0;
    
        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = 0; j < arr.length - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
```
</details>

<br>

<details>
<summary>Bubble Sort의 특징</summary>
<br>
<div>
정렬할 배열 안에서 정렬이 이루어지기 때문에 다른 메모리 공간이 필요하지 않습니다. 이런 정렬 방식을 제자리 정렬이라고 합니다.

또한 동일한 값에 대한 순서가 정렬 후에도 유지 되기 때문에 안정 정렬 중 하나 입니다.
</div>
</details>

### Quick Sort

<details>
<summary>Quick Sort란?</summary>

<br>

<div>
퀵 정렬은 분할 정복 기법과 재귀 알고리즘을 통해 데이터를 정렬합니다.
기준점을 설정해 기준점보다 큰 데이터, 작은 데이터로 분할하여 재귀적으로 정렬을 진행합니다.
퀵 정렬의 시간복잡도는 평균 O(NlogN)이며 최악의 경우 O(N^2)의 시간복잡도를 가집니다.
</div>
</details>

<br>

<details>
<summary>Quick Sort 정렬과정</summary>

<br>

<div>
우선 배열 중 하나의 원소를 기준점으로 설정합니다. 여기서 기준점을 피벗(pivot)이라고 부릅니다.
피벗을 기준으로 피벗보다 작은 원소, 큰 원소를 모아 배열을 둘로 나눕니다. 이때 피벗은 정렬된 상태로 위치하게 됩니다.
이 과정을 파티션 이라고 합니다.
이후 나뉘어진 두 배열에 대해서 같은 작업을 재귀적으로 반복합니다.
</div>

* 재귀 호출이 한번 진행될 때마다 최소 하나의 원소의 위치가 정해지므로 정렬이 끝난다는것을 보장할 수 있습니다.
</details>

<br>

<details>
<summary>Quick Sort 특징</summary>

<br>

<div>
퀵 정렬은 동일한 값에 대해서 정렬 전의 순서를 보장하지 않는 불안정 정렬입니다.
평균 시간 복잡도가 O(logN)으로 다른 정렬 알고리즘보다 빠릅니다.
하지만 정렬된 리스트나 피벗의 값이 가장 작거나 큰 경우 오히려 수행시간이 더 오래걸릴 수 있습니다.
이때의 시간 복잡도는 O(N^2)입니다.
</div>

</details>





