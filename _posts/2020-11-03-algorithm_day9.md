---
title: "[ALGO] Sorting 1 (Selection Sort / Insertion Sort)"
categories: 
  - CS
last_modified_at: 2020-11-03 12:00:00
comments: true
use_math: true # MathJax On
---

#### Sorting
- 데이터를 특정한 기준에 따라서 순서대로 나열하는 것

#### Selection Sort
- 매번 가장 작은 것을 선택해서 앞으로 보냄
- 가장 작은 데이터를 선택해 맨 앞에 있는 데이터와 바꾸고, 그다음 작은 데이터를 선택해 앞에서 두 번째 데이터와 바꾸는 과정을 반복
- 데이터의 개수를 N이라 하고, 아래 그림에서 파란색은 '현재 정렬되지 않은 데이터 중에서 가장 작은 데이터'이고 노란색은 '이미 정렬된 데이터'
- 가장 작은 데이터를 앞으로 보내는 과정을 N-1번 반복하면 정렬 완료

EX. N = 10


`code`
```py # selection sort source code
array = [7,5,9,0,3,1,6,2,4,8]

for i in range(len(array)):
  min_index = i
  for j in range(i+1, len(array)):
    if array[min_index] > array[j]:
      min_index = j
  array[i], array[min_index] = array[min_index], array[i]
  
print(array)
```
```
[0,1,2,3,4,5,6,7,8,9]
```

#### Big-O of Selection Sort
- 매번 가장 작은 수를 찾기 위해서 비교 연산이 필요
- (N-1) + (N-2) + ... + 2 + 1 = N * (N-1) / 2
- O(N^2)
- N > 10,000 일때부터 상당히 비효율적
- 결론 : 알고리즘 문제 풀이에 사용하기에 매우 느린 편

#### Insertion Sort