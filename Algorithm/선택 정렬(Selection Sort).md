# 선택 정렬(Selection Sort)

## 목표
- Selection Sort에 대해 설명할 수 있다.
- Selection Sort 과정에 대해 설명할 수 있다.
- Selection Sort을 구현할 수 있다.
- Selection Sort의 시간복잡도와 공간복잡도를 계산할 수 있다.

## 개념
Selection Sort는 Bubble Sort과 유사한 알고리즘으로, `해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘이다.`
Selection Sort와 Insertion Sort를 헷갈려하는 사람들이 종종 있는데, Selection Sort는 배열에서 `해당 자리를 선택하고 그 자리에 오는 값을 찾는 것`이라고 생각하면 편하다.

## 과정
1. 주어진 배열 중에 최소값을 찾는다.
2. 그 값을 맨 앞에 위치한 값과 교체한다.
3. 맨 처음 위치를 뺀 나머지 배열을 같은 방법으로 교체한다.

## Python Code
```python
arr = [64, 25, 12, 22, 11]
for i in range(len(arr)):
  min_idx = i
  for j in range(i + 1, len(arr)):
    if arr[min_idx] > arr[j] :
      mind_idx = j
  arr[i], arr[min_index] = arr[min_index], arr[i]
```

## 시간복잡도
데이터의 개수가 n개라고 했을때, `(n-1) + (n-2) + ... + 2 + 1 => n(n-1)/2
최선, 평균, 최악의 경우 시간복잡도는 O(n^2)으로 동일하다.
## 공간복잡도
주어진 배열 안에서 교환(swap)을 통해 정렬이 수행되므로 O(n) 이다.
## 장점
- Bubble Sort와 마찬가지로 알고리즘이 단순하다.
- 정렬을 위한 비교 횟수는 많지만, Bubble Sort에 비해 실제로 교환하는 횟수는 적기 때문에 많은 교환이 일어나야 하는 자료 상태에서 비교적 효율적이다
- Bubble Sort와 마찬가지로 정렬하고자 하는 배열 안에서 교환하는 방식이므로, 다른 메모리 공간을 필요로 하지 않는다. => 제자리 정렬
## 단점
- 시간복잡도가 O(n^2)으로 비효율적이다.
- 불안정 정렬(Unstable Sort)이다.
