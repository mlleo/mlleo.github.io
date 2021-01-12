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
