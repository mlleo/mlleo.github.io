---
title: "[ALGO] Sorting 2 (Quick Sort / Count Sort)"
categories: 
  - CS
last_modified_at: 2020-11-05 12:00:00
comments: true
use_math: true # MathJax On
---

#### Quick sort
- 피벗(pivot)을 사용해서 기준을 설정한 다음, 큰 수와 작은 수를 교환한 후 리스트를 반으로 나누는 방식으로 동작
- 피벗을 설정하고 리스트를 분할하는 방법에 따라서 여러 가지 방식으로 퀵 정렬을 구분
- 예제는 '리스트에서 첫 번째 데이터를 피벗으로 정한다'의 규칙을 따르는 Hoare Partition 방식을 기준
- 피벗을 설정한 뒤에는 왼쪽에서부터 피벗보다 큰 데이터를 찾고, 오른쪽에서부터 피벗보다 작은 데이터를 찾은 후, 두 데이터의 위치를 서로 교환
- 위 과정을 반복하면 '피벗'에 대하여 정렬이 수행
- 리스트의 데이터 개수가 1개인 경우 퀵 정렬 종료

EX. N = 10
1. 분할(Divide) / 파티션(Partition)
- 피벗의 왼쪽에는 피벗보다 작은 데이터가 위치하고, 오른쪽에는 피벗보다 큰 데이터가 위치하도록 하는 작업



2. 왼쪽 리스트에서 퀵 정렬 진행 (동일한 방식)
3. 오른쪽 리스트에서 퀵 정렬 진행 (동일한 방식)

`code`
```py

# quick sort source code

array = [5,7,9,0,3,1,6,2,4,8]

def quick_sort(array, start, end):
  if start >= end:        # 원소가 1개인 경우 종료
    return
  pivot = start           # 피벗은 첫 번째 원소
  left = start + 1
  right = end
  while left <= right:
    while left <= end and array[left] <= array[pivot]:    # 피벗보다 큰 데이터를 찾을 때까지 반복
      left += 1
    while right > start and array[right] >= array[pivot]:  # 피벗보다 작은 데이터를 찾을 때까지 반복
      right -= 1
    if left > right:    # 엇갈렸다면 작은 데이터와 피벗 교체
      array[right], array[pivot] = array[pivot], array[right]
    else:    # 엇갈리지 않았다면 작은 데이터와 큰 데이터를 교체
      array[left], array[right] = array[right], array[left]
  quick_sort(array, start, right-1)
  quick_sort(array, right+1, end)
  
quick_sort(array, 0, len(array)-1)
print(array)
```
```
[0,1,2,3,4,5,6,7,8,9]
```
`code`
```py

# 파이썬의 장점을 살린 quick sort source code

array = [5,7,9,0,3,1,6,2,4,8]

def quick_sort(array):
  if len(array) <= 1:    # 리스트가 하나 이하의 원소만을 담고 있다면 종료
    return array
  
  pivot = array[0]       # 피벗은 첫 번째 원소
  tail = array[1:]       # 피벗을 제외한 리스트
  
  left_side = [x for x in tail if x <= pivot]        # 분할된 왼쪽 부분
  right_side = [x for x in tail if x > pivot]        # 분할된 오른쪽 부분
  
  return quick_sort(left_side) + [pivot] + quick_sort(right_side)
  
print(quick_sort(array))
```
```
[0,1,2,3,4,5,6,7,8,9]
```

#### Big-O of Quick sort
- avg : O(NlogN)
- Worst : O(N^2) : 이미 데이터가 정렬되어 있는 경우
- Worst 과정을 피하기 위해 기본 정렬 라이브러리를 이용하여 피벗값 설정 로직 추가

#### Count sort












<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
