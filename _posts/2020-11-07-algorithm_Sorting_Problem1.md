---
title: "[ALGO] Sorting PROBLEM 1"
categories: 
  - CS
last_modified_at: 2020-11-07 12:00:00
comments: true
use_math: true # MathJax On
---

#### 문제 1
![위에서아래로](https://user-images.githubusercontent.com/62474292/102011073-54591100-3d85-11eb-985e-effc11f58ced.JPG)

#### 문제1 풀이
- 리스트 내장 함수 sort 이용
- 파이썬 라이브러리 sorted 사용해도 됨

`code`
```py
n = int(input())

data = []

for _ in range(n):
	data.append(int(input()))

data.sort(reverse = True)

for i in data:
	print(i, end=' ')
```
#### 문제 2
![성적이낮은순서로](https://user-images.githubusercontent.com/62474292/102011071-54591100-3d85-11eb-9a90-7b0081811950.JPG)

#### 문제2 풀이
- 튜플 형태로 이름과 점수를 저장
- 파이썬 내장 라이브러리 sorted 사용해서 정렬, key값은 lambda 함수로 정의!

`code`
```py
n = int(input())

data = []

for _ in range(n):
	a,b = input().split()
	data.append((a,b))

result = sorted(data, key = lambda x: int(x[1]))

for i in result:
	print(i[0], end = ' ')
```
#### 문제 3
![두배열의원소교체](https://user-images.githubusercontent.com/62474292/102011068-5327e400-3d85-11eb-8cc0-dd7eacc12bcc.JPG)
![두배열의원소교체2](https://user-images.githubusercontent.com/62474292/102011075-54f1a780-3d85-11eb-914c-6ffc1e48537a.png)

#### 문제3 풀이
- k번 반복하는 동안 A의 최솟값과 B의 최댓값을 인덱스 값을 이용해서 swap

`code`
```py
n,k = map(int, input().split())
data_A = list(map(int, input().split()))
data_B = list(map(int, input().split()))



for _ in range(k):
	min_A = data_A.index(min(data_A))
	max_B = data_B.index(max(data_B))
	data_A[min_A], data_B[max_B] = data_B[max_B], data_A[min_A]

print(sum(data_A))
	
```

#### 모범답안

`code`
```py
n,k = map(int, input().split())
a = list(map(int, input().split()))
b = list(map(int, input().split()))

a.sort()
b.sort(reverse = True)

for i in range(k):
  if a[i] < b[i]:
    a[i] , b[i] = b[i], a[i]
  else:
    break
    
print(sum(a))
```

<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
