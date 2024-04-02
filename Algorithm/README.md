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
