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

#### 파이썬 이진 탐색 라이브러리
- bisect_left(a,x) : 정렬된 순서를 유지하면서 배열 a에 x를 삽입할 인덱스 (여러 곳이 존재하면 가장 왼쪽 위치)를 반환
- bisect_right(a,x) : 정렬된 순서를 유지하면서 배열 a에 x를 삽입할 인덱스 (여러 곳이 존재하면 가장 오른쪽 위치)를 반환

`code`
```py
from bisect import bisect_left, bisect_right

a = [1,2,4,4,8]
x = 4

print(bisect_left(a,x))
print(bisect_right(a,x))
```
```
2
4
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
n = int(input())
data = list(map(int, input().split()))
data.sort()
m = int(input())
request = list(map(int, input().split()))

def binary_search(data, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        if data[mid] == target:
            print("yes")
            return
        elif data[mid] > target:
            end = mid-1
        else:
            start = mid+1
    print("no")



for i in range(m):
    binary_search(data, request[i],0,n-1)
```

`code`
```py
# 모범답안 1 (이진 탐색)
# 이진 탐색 소스코드 구현 (반복문)
def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        # 찾은 경우 중간점 인덱스 반환
        if array[mid] == target:
            return mid
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        elif array[mid] > target:
            end = mid - 1
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 오른쪽 확인
        else:
            start = mid + 1
    return None

# N(가게의 부품 개수) 입력
n = int(input())
# 가게에 있는 전체 부품 번호를 공백을 기준으로 구분하여 입력
array = list(map(int, input().split()))
array.sort() # 이진 탐색을 수행하기 위해 사전에 정렬 수행
# M(손님이 확인 요청한 부품 개수) 입력
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백을 기준으로 구분하여 입력
x = list(map(int, input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    result = binary_search(array, i, 0, n - 1)
    if result != None:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```

```py
# 모범답안 2(계수 정렬)
# N(가게의 부품 개수) 입력
n = int(input())
array = [0] * 1000001

# 가게에 있는 전체 부품 번호를 입력 받아서 기록
for i in input().split():
    array[int(i)] = 1

# M(손님이 확인 요청한 부품 개수) 입력
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백을 기준으로 구분하여 입력
x = list(map(int, input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    if array[i] == 1:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```


```py
# 모범답안 3(집합 자료형)
# N(가게의 부품 개수) 입력
n = int(input())
# 가게에 있는 전체 부품 번호를 입력 받아서 집합(Set) 자료형에 기록
array = set(map(int, input().split()))

# M(손님이 확인 요청한 부품 개수) 입력
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백을 기준으로 구분하여 입력
x = list(map(int, input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    if i in array:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```

#### 기본 예제2
![2](https://user-images.githubusercontent.com/62474292/104382308-37c11c00-5571-11eb-84a2-f6224d1ebbba.JPG)

#### 예제2 풀이
- 원하는 조건을 만족하는 가장 알맞은 값을 찾는 문제에 주로 'parametric search'가 사용되는데 이 때 최적화 문제라면 이진 탐색으로 결정 문제를 해결하면서 범위를 좁혀갈 수 있다

`code`
```py
n,m = map(int, input().split())         # n : 떡의 개수 m : 요청한 길이

height = list(map(int, input().split()))

start = 0
end = max(height)

result = 0
while start <= end:
    total = 0
    mid = (start + end) // 2
    for x in height:
        if x > mid:
            total += (x-mid)
    if total < m:
        end = mid - 1
    else:
        result = mid
        start = mid + 1
print(result)
```
