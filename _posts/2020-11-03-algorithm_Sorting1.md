---
title: "[ALGO] Sorting 1 (Selection Sort / Insertion Sort / Bubble Sort)"
categories: 
  - CS
tags:
  - ALGORITHM
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
![Selection_sort](https://user-images.githubusercontent.com/62474292/102009119-a5aed380-3d78-11eb-9b8c-75ad45c01b69.png)
![Selection_sort2](https://user-images.githubusercontent.com/62474292/102009123-a7789700-3d78-11eb-86dd-10203c1d84be.png)

`code`
```py 
# selection sort source code

array = [7,5,9,0,3,1,6,2,4,8]

for i in range(len(array)):       # 앞에서부터 차례대로 반복
  min_index = i                   # 가장 작은 원소의 인덱스를 저장할 변수
  for j in range(i+1, len(array)):    # 가장 작은 원소의 인덱스를 찾는 반복
    if array[min_index] > array[j]:
      min_index = j
  array[i], array[min_index] = array[min_index], array[i]     # swap
  
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
- 특정한 데이터를 적절한 위치에 '삽입'
- 필요할 때만 위치를 바꾸므로 '데이터가 거의 정렬되어 있을 때' 매우 효율적
- 특정한 데이터가 적절한 위치에 들어가기 이전에, 그 앞까지의 데이터는 이미 정렬되어 있다고 가정
- 첫 번째 데이터는 그 자체로 정렬되어 있다고 판단하므로 두 번재 데이터부터 시작
- 특정한 데이터가 삽입될 위치를 정할 때(삽입될 위치를 찾기 위하여 왼쪽으로 한 칸씩 이동할 때), 삽입될 데이터보다 작은 데이터를 만나면 그 위치에서 멈추고 삽입

EX. N = 10
![insertion_sort](https://user-images.githubusercontent.com/62474292/102010468-941df980-3d81-11eb-82eb-78c602d1af91.png)
![insertion_sort2](https://user-images.githubusercontent.com/62474292/102010470-954f2680-3d81-11eb-9af4-64325fdc270e.png)

`code`
```py
# Insertion sort source code

array = [7,5,9,0,3,1,6,2,4,8]

for i in range(1,len(array)):
  for j in range(i,0,-1):                                # 인덱스 i부터 1까지 감소하며 반복
    if array[j] < array[j-1]:
      array[j], array[j-1] = array[j-1], array[j]        # 한 칸씩 왼쪽으로 이동
    else:       # 자기보다 작은 데이터를 만나면 그 위치에서 멈춤
      break
```
```
[0,1,2,3,4,5,6,7,8,9]
```

#### Big-O of Insertion Sort
- Best : O(N), Worst : O(N^2)
- 거의 정렬되어 있는 상황이라면 매우 강력한 정렬 알고리즘

#### Bubble Sort
-  서로 인접한 두 원소를 검사하여 정렬하는 알고리즘
-  인접한 두 원소를 비교하여 크기가 순서대로 되어 있지 않은 경우 교환

![bublle](https://user-images.githubusercontent.com/62474292/109023990-9a750e00-7700-11eb-99ab-6ab387eccf6a.JPG)

`code`
```py
def BubbleSort(a):  # a: 정렬할 리스트
  for i in range(len(a)-1, 0, -1):
    for j in range(0,i):
      if a[j] > a[j+1]:
        a[j], a[j+1] = a[j+1], a[j]
```

#### Big-O of Bubble Sort
- O(N^2)

<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
