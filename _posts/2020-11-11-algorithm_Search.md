---
title: "[ALGO] Search"
categories: 
  - CS
last_modified_at: 2020-11-11 12:00:00
comments: true
use_math: true # MathJax On
---

#### Search

#### Sequential Search
- 리스트 안에 있는 특정한 데이터를 찾기 위해 앞에서부터 데이터를 하나씩 차례대로 확인하는 방법
- 보통 정렬되지 않은 리스트에서 데이터를 찾아야 할 때 사용
- 리스트 내에 데이터가 아무리 많아도 시간만 충분하면 항상 원하는 데이터를 찾을 수 있음
- 시간 복잡도 : O(N)

`code`
```py
def sequential_search(n, target, array):
    for i in range(n):  # 각 원소를 하나씩 확인
        if array[i] == target:  # 현재의 원소가 찾고자 하는 원소와 동일한 경우
            return i+1 # 현재의 위치 반환(인덱스는 0부터 시작하므로 더하기 1)

print("생성할 원소 개수 입력 후 찾을 문자열 입력하세요")
input_data = input().split()
n = int(input_data[0])
target = input_data[1]

print("원소 개수만큼 문자열을 입력하세요")
array = input().split()

print(sequential_search(n,target,array))
```

#### Binary Search
- 배열 내부의 데이터가 정렬되어 있어야만 사용 가능한 알고리즘
- 탐색 범위를 절반씩 좁혀가며 데이터를 탐색
- 위치를 나타내는 변수 3개 사용(탐색하고자 하는 범위의 시작점, 끝점, 중간점)
- 찾으려는 데이터와 중간점 위치에 있는 데이터를 반복적으로 비교해서 원하는 데이터를 찾음
- 데이터의 개수나 값이 1000만 단위 이상으로 넘어가면 이진 탐색과 같이 O(logN)의 속도를 내야 하는 알고리즘을 떠올려야 함
- 시간 복잡도 : O(logN)

![binary](https://user-images.githubusercontent.com/62474292/104382306-37288580-5571-11eb-8767-74d33abc7f4a.png)

`code`
```py
# 재귀 함수로 구현한 이진 탐색 코드
def binary_search(array, target, start, end):
    if start > end:
        return None
    mid = (start + end) // 2
    if array[mid] == target:
        return mid
    elif array[mid] > target:
        return binary_search(array, target, start, mid-1)
    else:
        return binary_search(array, target, mid+1, end)

```

`code`
```py
# 반복문으로 구현한 이진 탐색 코드
def binary_search(array, target, start, end):
    while start >= end:
        mid = (start + end) // 2
        if array[mid] == target:
            return mid
        elif array[mid] > target:
            end = mid - 1
        else:
            start = mid + 1
    return None
```

#### Tree (Data Structure)
![tree](https://user-images.githubusercontent.com/62474292/104382301-35f75880-5571-11eb-91cf-4016eb19fcf3.png)

#### Binary Search Tree
- 이진 탐색이 동작할 수 있도록 고안된 효율적인 자료구조
- 부모 노드보다 왼쪽 자식 노드가 작다
- 부모 노드보다 오른쪽 자식 노드가 크다

#### How to speed up input()

`code`
```py
import sys
input_data = sys.stdin.readline().rstrip()  # 엔터(줄 바꿈 기호)를 제거하기 위해 rstrip() 호출
```

#### 기본 예제1
![1](https://user-images.githubusercontent.com/62474292/104382310-37c11c00-5571-11eb-978a-9c8357c03b99.JPG)
`code`
```py

``

#### 기본 예제2
![2](https://user-images.githubusercontent.com/62474292/104382308-37c11c00-5571-11eb-84a2-f6224d1ebbba.JPG)

`code`
```py

``
