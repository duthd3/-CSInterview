# 삽입 정렬(Insertion Sort)

## 목표
- Insertion Sort에 대해 설명할 수 있다.
- Insertion Sortr과정에 대해 설명할 수 있다.
- Insertion Sort을 구현할 수 있다.
- Insertion Sort의 시간복잡도와 공간복잡도를 계산할 수 있다.
- Insertion Sort와 Selection Sort 차이에 대해 설명할 수 있다.

## 개념
손 안의 카드를 정렬하는 방법과 유사하다.
Insertion Sort는 Selection Sort와 유사하지만, 좀 더 효율적인 정렬 알고리즘이다.
Insertion Sort는 2번째 원소부터 시작하여 그 앞(왼쪽)의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입 하여 정렬하는 알고리즘이다.

최선의 경우 O(N)이라는 엄청나게 빠른 효율성을 가지고 있어, 다른 정렬 알고리즘의 일부로 사용될 만큼 좋은 정렬 알고리즘이다.

## 과정
1. 정렬은 2번째 위치(index)의 값부터 시작한다.
2. (index) 이전에 있는 원소들과 비교하여 삽입해나간다.
3. '1'번으로 돌아가 다음 위치(index)의 값으로 반복한다.

## Python Code
```python
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(1, len(array)):
  for j in range(i, 0, -1):
    if array[j] < array[j-1]:
      array[j], array[j-1] = array[j-1], array[j]
    else:
      break
```

## 시간복잡도
최악의 경우(역으로 정렬되어 있을 경우) Selection Sort와 마찬가지로, `(n-1) + (n-2) + ... + 2 + 1 => n(n-1)/2` 즉, O(n^2) 이다.
하지만, 모두 정렬이 되어있는 경우, 한번씩 밖에 비교를 안하므로 O(n)의 시간복잡도를 가지게 된다. 최선의 경우는 O(n)의 시간복잡도를 갖고, 평균과 최악의 경우 O(n^2)의 시간복잡도를 갖게 된다ㅏ.

## 공간복잡도
주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)이다.

## 장점
- 알고리즘이 단순하다.
- 대부분의 원소가 이미 정렬되어 있는 경우, 매우 효율적일 수 있다.
- 정렬하고자 하는 배열 안에서 교환하는 방식이므로, 다른 메모리 공간을 필요로 하지 않는다. => 제자리 정렬
- 안정 정렬(Stable Sort) 이다.
- Selection Sort나 Bubble Sort과 같은 O(n^2) 알고리즘에 비교하여 상대적으로 빠르다.

## 단점
- 평균과 최악의 시간복잡도가 O(n^2)으로 비효율적이다.
- Bubble Sort와 Selection Sort와 마찬가지로, 배열의 길이가 길어질수록 비효율적이다.
