# 퀵 정렬(Quick Sort)
## 목표
- Quick Sort에 대해 설명할 수 있다.
- Quick Sort 과정에 대해 설명할 수 있다.
- Quick Sort을 구현할 수 있다.
- Quick Sort의 시간복잡도와 공간복잡도를 계산할 수 있다.
- Quick Sort의 최악인 경우를 개선시킬 수 있다.

## 개념
Quick Sort은 분할 정복(divide and conquer)방법을 통해 주어진 배열을 정렬한다.
Quick Sort은 불안정 정렬에 속하며, 다른 원소와의 비교만으로 정렬을 수행하는 비교 정렬에 속한다. 또한 Merge Sort와 달리 Quick Sort는 배열을 비균등하게 분할한다.

## 과정
- 기준이 되는 데이터인 pivot을 하나 선택한다.
  - 일반적으로 가장 많이 사용되는 것은 주어진 array의 첫 번재 요소이다.(array[0])
- pivot을 기준으로 pivot 보다 작은 데이터와 pivot보다 큰 데이터로 구분한다.
- pivot을 pivot보다 작은 데이터와 pivot보다 큰 데이터 사이에 위치시키면 pivot의 위치가 결정된다.
  - [pivot 이하][pivot][pivot 초과]

## Python Code
```python
def quick_sort(array, start, end):
  if start >= end: return # 원소가 1개인 경우
  pivot = start # 피벗은 첫 요소
  left, right = start + 1, end

  while left <= right:
    # 피벗보다 큰 데이터를 찾을 때까지 반복
    while left <= end and array[left] <= array[pivot]:
      left += 1
    # 피벗보다 작은 데이터를 찾을 때까지 반복
    while right > start and array[right] >= array[pivot] :
      right -= 1
    if left > right: # 엇갈렸다면 작은 데이터와 피벗을 교체
      array[right], array[pivot] = array[pivot], array[right]
    else: # 엇갈리지 않았다면 작은 데이터와 큰 데이터를 교체
      array[left], array[right] = array[right], array[left]
  # 분할 이후 왼쪽 부분과 오른쪽 부분에서 각자 정렬 수행
  quick_sort(array, start, right -1)
  quick_sort(array, right + 1, end)
```
파이썬의 장점을 살린 방식
```python
def quick_sort(array):
  if len(array) <= 1: # 리스트가 하나 이하의 원소만을 담고 있다면 종료
    return array
  pivot = array[0]
  tail = array[1:]

  left_side = [x for x in tail if x<= pivot] # 분할된 왼쪽 부분
  right_side = [x for x in tail if x > pivot] # 분할된 오른쪽 부분

  return quick_sort(left_side) + [pivot] + quick_sort(right_side)
```

## 시간 복잡도
최선의 경우: O(nlog2n)
최악의 경우: O(n^2)
평균의 경우: O(nlog2n)

## 공간복잡도
주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)이다.

## 장점
- 불필요한 데이터의 이동을 줄이고 먼 거리의 데이터를 교환할 뿐만 아니라, 한 번 결졍된 피벗들이 추후 연산에서 제외되는 특성 때문에, 시간 복잡도가 O(nlog2n)를 가지는 다른 정렬 알고리즘과 비교했을 때도 가장 빠르다.
- 정렬하고자 하는 배열 안에서 교환하는 방식이므로, 다른 메모리 공간을 필요로 하지 않는다.

## 단점
- 불안정 정렬(Unstable Sort)이다.
- 정렬된 배열에 대해서는 Quick Sort의 불균형 분할에 의해 오히려 수행시간이 더 많이 걸린다.
  
