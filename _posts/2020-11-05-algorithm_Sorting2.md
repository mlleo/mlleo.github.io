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
- 피벗보다 작은 데이터의 위치와 피벗보다 큰 데이터의 위치가 엇갈린 경우, 작은 데이터와 피벗의 위치를 서로 교환
- 리스트의 데이터 개수가 1개인 경우 퀵 정렬 종료

EX. N = 10
1. 분할(Divide) / 파티션(Partition)
- 피벗의 왼쪽에는 피벗보다 작은 데이터가 위치하고, 오른쪽에는 피벗보다 큰 데이터가 위치하도록 하는 작업
![pivot_sort](https://user-images.githubusercontent.com/62474292/102049811-f1b75200-3e24-11eb-84f7-3de7327003b9.png)

2. 왼쪽 리스트에서 퀵 정렬 진행 (동일한 방식)
3. 오른쪽 리스트에서 퀵 정렬 진행 (동일한 방식)
![quick_sort2](https://user-images.githubusercontent.com/62474292/102050315-f29cb380-3e25-11eb-9d1d-0448da9660bd.png)

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
- avg : O(NlogN) : 분할이 절반씩 일어나는 경우
- Worst : O(N^2) : 이미 데이터가 정렬되어 있는 경우
- Worst 과정을 피하기 위해 기본 정렬 라이브러리를 이용하여 피벗값 설정 로직 추가

#### Count sort
- 특정한 조건이 부합할 때만 사용할 수 있지만 매우 빠른 알고리즘
- 데이터의 크기 범위가 제한되어 정수 형태로 표현할 수 있을때만 사용가능
- 일반적으로 가장 큰 데이터와 가장 작은 데이터의 차이가 1,000,000을 넘지 않을 때 효과적으로 사용 가능
- 데이터의 개수가 N, 데이터 중 최대값이 K일 때, 최악의 경우에도 O(N+K) 보장 (모든 데이터가 양의 정수라 가정)
- 일반적으로 별도의 리스트를 선언하고 그 안에 정렬에 대한 정보를 담는 방식 (데이터의 개수가 매우 많더라도 빠르게 동작)

EX. 최소값이 0, 최댓값이 9인 경우 -> 크기가 10인 리스트 선언 (7 5 9 0 3 1 6 2 9 1 4 8 0 5 2)
![count_sort](https://user-images.githubusercontent.com/62474292/102032347-da17a380-3dfb-11eb-9101-133b172b661f.png)


- 생성된 Count 리스트를 기반으로 첫번째 데이터(0의 갯수)부터 하나씩 그 값만큼 인덱스를 출력

`code`
```py

# Count sort source code

array = [7,5,9,0,3,1,6,2,9,1,4,8,0,5,2]    # 모든 원소의 값이 0보다 크거나 같다고 가정
count = [0] * (max(array)+1)               # 모든 범위를 포함하는 리스트 선언

for i in range(len(array)):
  count[array[i]] += 1                     # 각 데이터에 해당하는 인덱스의 값 증가

for i in range(len(count)):
  for j in range(count[i]):
    print(i, end = ' ')                    # 띄어쓰기를 구분으로 등장한 횟수만큼 인덱스 출력
```
```
0 0 1 1 2 2 3 4 5 5 6 7 8 9 9
```

`code`
```py
# Count sort source code (실제 동작 원리)

def countsort(a,b):             # a: 입력 배열, b: 정렬이후 저장할 배열
    max_num = max(a)
    c = [0] * (max_num+1)

    for i in range(len(a)):
        c[a[i]] += 1

    for i in range(1,len(c)):
        c[i] += c[i-1]

    for i in range(len(b)-1, -1, -1):          # 마지막 인덱스부터 0까지 확인
        b[c[a[i]]-1] = a[i]
        c[a[i]] -= 1

    return b

a = [2,5,7,89,9,3,4]
b = [0] * 7

print(countsort(a,b))

```

#### Big-O of Count sort

- 현존하는 정렬 알고리즘 중에 Radix sort와 더불어 가장 빠름
- 앞에서부터 데이터를 하나씩 확인하면서 리스트에서 적절한 인덱스의 값을 1씩 증가시킬 뿐만 아니라, 추후에 리스트의 각 인덱스에 해당하는 값들을 확인할 때 데이터 중 최댓값의 크기만큼 반복을 수행
- O(N+K)
- 데이터의 크기가 한정되어 잇고, 데이터의 크기가 많이 중복되어 있을수록 유리하며 항상 사용할 수는 없다

#### 파이썬의 정렬 라이브러리
- sorted() : 퀵 정렬과 동작 방식이 비슷한 병합 정렬을 기반으로 만들어짐, 최악의 경우에도 O(NlogN)
- sort() : 리스트의 경우 리스트 객체의 내장 함수 이용 가능

`code`
```py
array = [7,5,9,0,3,1,6,2,4,8]

result = sorted(array)
print(result)
```
```
[0,1,2,3,4,5,6,7,8,9]
```
```
array = [7,5,9,0,3,1,6,2,4,8]

array.sort()
print(array)
```
```
[0,1,2,3,4,5,6,7,8,9]
```
```
array = [('바나나',2), ('사과',5), ('당근',3)]

def setting(data):
  return data[1]

result = sorted(array, key=setting)
print(result)
```
```
[('바나나',2), ('당근',3), ('사과',5)]
```








<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
