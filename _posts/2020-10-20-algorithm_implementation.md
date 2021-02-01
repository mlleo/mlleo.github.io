---
title: "[ALGO] IMPLEMENTATION"
categories: 
  - CS
last_modified_at: 2020-10-20 12:00:00
comments: true
use_math: true # MathJax On
---

### 구현 중심 알고리즘

- 풀이를 떠올리는 것은 쉽지만 소스코드로 옮기기 어려운 문제 (완전탐색, 시뮬레이션 2개를 예시로 다룰 예정)
- 완전 탐색 : 모든 경우의 수를 주저 없이 다 계산하는 해결 방법
- 시뮬레이션 : 문제에서 제시한 알고리즘을 한 단계씩 차례대로 직접 수행하는 방법

#### 구현 시 메모리 제약사항 (파이썬 기준)
- 파이썬에서는 프로그래머가 직접 자료형을 지정할 필요가 없으며 매우 큰 수의 연산 또한 기본으로 지원
- 다만, 실수형 변수는 다른 언어와 마찬가지로 유효숫자에 따라서 연산 결과가 달라질 수 있음
- 파이썬 리스트 사용 시 (int 자료형 데이터의 개수에 따른 메모리 사용량)
  - 데이터의 개수(리스트의 길이) : 1,000        -> 메모리 사용량 : 약 4KB
  - 데이터의 개수(리스트의 길이) : 1,000,000    -> 메모리 사용량 : 약 4MB
  - 데이터의 개수(리스트의 길이) : 10,000,000   -> 메모리 사용량 : 약 40MB
- 일반적으로 1초에 2,000만 번의 연산을 수행한다고 가정하면 됨
  - 시간 제한이 1초이고, 데이터의 개수가 100만 개인 문제라면 시간복잡도 O(NlogN) 이내의 알고리즘으로 해결해야 함
  
#### 기본 예제1
![상하좌우](https://user-images.githubusercontent.com/62474292/100416920-feb51100-30c2-11eb-81af-461f82fb65fb.JPG)
  
#### 예제1 풀이
- 상,하,좌,우 움직임을 x축 방향과 y축 방향으로 나누어서 표현

`code`
```py
n = int(input())
data = input().split()
x,y = 1,1

dx = [0,0,-1,1]
dy = [1,-1,0,0]
move = ['L','R','U','D']

for x in data:
	for j in range(len(move)):
		if x == move[j]:
			nx = x + dx[j]
			ny = y + dy[j]
	if nx <1 or ny <1 or nx > n or ny > n:
		continue
	x,y = nx, ny

print(x,y)
```

#### 기본 예제2
![시각](https://user-images.githubusercontent.com/62474292/100416927-01b00180-30c3-11eb-8cab-294e26c4ea42.JPG)

#### 예제2 풀이
- 3중 반복문을 통해 시, 분, 초를 모두 확인하면서 전체 문자열에 '3'이 들어간 경우만 count 증가

`code`
```py
n = int(input())

count = 0

for i in range(n+1):
  for j in range(60):
    for k in range(60):
      if '3' in str(i) + str(j) + str(k):
        count += 1
        
print(count)
```

#### 기본 예제3
![왕실의나이트](https://user-images.githubusercontent.com/62474292/100419056-15f5fd80-30c7-11eb-9514-f727c84f44e5.JPG)
![왕실의나이트2](https://user-images.githubusercontent.com/62474292/100419059-18f0ee00-30c7-11eb-8148-d64c732677e1.JPG)

#### 예제3 풀이
- 알파벳 문자열을 아스키 코드 값을 이용해서 자연수에 순차적으로 대응시키는 방법 주의!
- ord는 문자의 아스키 코드 값을 반환
- 이동할 수 있는 모든 경우의 수를 좌표로 표현

`code`
```py
pos = input()
column = int(pos[0])-int(ord('a'))+1
row = int(pos[1])

steps = [(-2,-1),(-2,1),(-1,-2),(-1,2),(2,-1),(2,1),(1,-2),(1,2)]

count = 0

for step in steps:
	next_row = row + step[0]
	next_col = column + step[1]
	
	if next_row >= 1 and next_row <= 8 and next_col >= 1 and next_col <= 8:
		count += 1

print(count)
```

#### 기본 예제4
![게임개발](https://user-images.githubusercontent.com/62474292/100419350-bb10d600-30c7-11eb-9081-998cf1d84ad4.JPG)

#### 예제4 풀이
- 방문한 위치 기록할 수 있는 2차원 리스트 생성
- 방향에 대한 좌표값 생성
- 왼쪽으로 회전하는 함수 디자인
- 조건문을 활용하여 주어진 시나리오 시뮬레이션 시작!

`code`
```py
n, m = map(int, input().split())

visited = [[0] * m for _ in range(n)]	# 방문한 위치 기록하기 위한 맵 생성

x,y,direction = map(int, input().split())

visited[n][m] = 1	# 현재 좌표 방문 기록

# 전체 맵 정보 입력 받기

array = []
for i in range(n):
	array.append(list(map(int, input().split())))

# 방향 정의 (북, 동, 남, 서)

dx = [-1, 0, 1, 0]
dy = [0, 1, 0, -1]

# 왼쪽으로 회전하는 함수

def turn_left():
	global direction
	direction -= 1
	if direction == -1:
		direction = 3


# 시뮬레이션 시작

count = 1	
turn_time = 0
while True:
	# 왼쪽으로 회전
	turn_left()
	nx = x + dx[direction]
	ny = y + dy[direction]
	if visited[nx][ny] == 0 and array[nx][ny] = 0: 	# 왼쪽으로 회전했을 때 가보지 않았으면서 + 육지인 곳 존재하는 경우
		visited[nx][ny] = 1
		x = nx
		y = ny
		count += 1
		turn_time += 0
		continue
	else:     # 왼쪽 방향에 가보지 않은 칸이 없는 경우
		turn_left()
		turn_time += 1

	if turn_time == 4:        # 모든 방향에 가보지 않은 칸이 없는 경우
		nx = x - dx[direction]
		ny = y - dy[direction]
		
		if array[nx][ny] = 0:   # 뒤로 가려고 하는데 뒤가 육지인 경우
			x = nx
			y = ny
		else:                   # 뒤로 가려고 하는데 뒤가 바다인 경우
			break
		turn_time = 0

print(count)
```
<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
