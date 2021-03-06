---
title: "[ALGO] IMPLEMENTATION PROBLEM"
categories: 
  - CS
tags:
  - ALGORITHM
last_modified_at: 2020-10-20 12:00:00
comments: true
use_math: true # MathJax On
---

#### 문제 1
![1_럭키스트레이트](https://user-images.githubusercontent.com/62474292/101722501-b4358a80-3aed-11eb-885f-a9194df8fd07.JPG)

#### 문제 1 풀이
- 정수를 문자열로 받아서 리스트에 저장
- 앞 절반의 합을 front에 저장, 뒤 절반의 합을 back에 저장

`code`
```py
n = list(input())
front = 0
back = 0
for i in range(len(n)):
    if i<len(n)//2:
        front += int(n[i])
    else:
        back += int(n[i])
if front == back:
    print("LUCKY")
else:
    print("READY")
```
```py
n = input()
front = list(map(int, n[:len(n)//2]))
back = list(map(int, n[len(n)//2:]))
if sum(front) == sum(back):
    print("lUCKY")
else:
    print("READY")
```

`code`
```py
# 모범답안
n = input()
length = len(n)

for i in range(length//2):
  summary += int(n[i])

for i in range(length//2, length):
  summary -= int(n[i])

if summary == 0:
  print("LUCKY")
else:
  print("READY")
```
#### 문제 2
![2_문자열재정렬](https://user-images.githubusercontent.com/62474292/101722488-b13a9a00-3aed-11eb-9830-520ef92fc303.JPG)

#### 문제 2 풀이
- 문자열을 리스트에 저장후 sort()을 통해 정렬 (오름차순 정렬 시 숫자가 알파벳보다 앞에 정렬됨)
- 숫자이면 sum에 더해주면서 합을 저장, 알파벳이면 새로운 배열에 저장
- 숫자들의 합 sum을 마지막에 새로운 배열에 저장

`code`
```py
n = list(input())
n.sort()
sum = 0
arr=[]

for data in n:
    if data.isdigit():
        sum += int(data)
    else:
        arr.append(data)
arr.append(sum)

for data in arr:
    print(data, end="")
```

`code`
```py
# 모범답안
data = input()
result = []
value = 0

for x in data:
  if x.isalpha():
    result.append(x)
  else:
    value += int(x)

result.sort()

if value != 0:
  result.append(str(value))

print(''.join(result))
```
#### 문제 3 (프로그래머스 코드 참고)
![3_문자열압축](https://user-images.githubusercontent.com/62474292/101722474-ada71300-3aed-11eb-8a09-ee002c069440.JPG)
![3_2](https://user-images.githubusercontent.com/62474292/101722487-b0a20380-3aed-11eb-823a-db990eaad7a6.JPG)

`code`
```py
def solution(s):
    answer = 0
    return answer
```
#### 문제 4 (프로그래머스 코드 참고)
![4_자물쇠와열쇠](https://user-images.githubusercontent.com/62474292/101722498-b3045d80-3aed-11eb-896c-20d8bcb7f30c.JPG)
![4_2](https://user-images.githubusercontent.com/62474292/101722483-b0096d00-3aed-11eb-8b21-b0013f38806a.JPG)

`code`
```py

```
#### 문제 5
![5_뱀](https://user-images.githubusercontent.com/62474292/101722499-b39cf400-3aed-11eb-88e9-832ba9158d7d.JPG)

`code`
```py
n = int(input())                        # 보드의 크기
k = int(input())                        # 사과 개수

graph = [[0] * n for _ in range(n)]
head_x,head_y = 0,0
tail_x,tail_y = 0,0
graph[head_x][head_y] = 1
for _ in range(k):
    x,y = map(int, input().split())
    graph[x-1][y-1] = 10                # 사과 위치 표시
l = int(input())                        # 방향 변환 횟수

direction_change = []                   # 방향 변환 정보
for _ in range(l):
    direction_change.append(input().split())              # X 초 뒤에 'L'이면 왼쪽으로 90도회전, 'D'이면 오른쪽으로 90도 회전
change_time = [int(i[0]) for i in direction_change]      # 방향 바꾸는 시간 (오름차순)
change_direction = [i[1] for i in direction_change] # 방향 바꾸는 정보 (시계/반시계)

dx = [0,1,0,-1]         # 동, 남, 서, 북
dy = [1,0,-1,0]
direction = 0           # 처음 방향은 동쪽
time = 0                # 몇 초 뒤에 끝나는지
time_index = 0
snake = [(head_x,head_y)]

def turn_left():
    global direction
    direction -= 1
    if direction == -1:
        direction = 3

def turn_right():
    global direction
    direction += 1
    if direction == 4:
        direction = 0


while True:
    if time in change_time:     # 방향 바꿀 시간이면
        if change_direction[time_index] == 'L':         # 왼쪽 90도 회전
            turn_left()
        else:                                           # 오른쪽 90도 회전
            turn_right()
        time_index += 1
    nx = head_x + dx[direction]
    ny = head_y + dy[direction]
    if nx < 0 or nx >= n or ny < 0 or ny >= n or graph[nx][ny] == 1:
        time += 1
        break
    elif graph[nx][ny] != 10:         # 사과가 없으면
        graph[tail_x][tail_y] = 0
        del snake[0]


    head_x = nx
    head_y = ny
    snake.append((head_x,head_y))
    tail_x = snake[0][0]
    tail_y = snake[0][1]
    graph[nx][ny] = 1
    time += 1
    # print(head_x,head_y)

print(time)
```
#### 문제 6 (프로그래머스 코드 참고)
![6_기둥과보설치](https://user-images.githubusercontent.com/62474292/101722477-ae3fa980-3aed-11eb-8d58-d529cd640775.JPG)
![6_2](https://user-images.githubusercontent.com/62474292/101722490-b1d33080-3aed-11eb-9d69-ff25b88070b1.JPG)
![6_3](https://user-images.githubusercontent.com/62474292/101722480-af70d680-3aed-11eb-99b0-d025e2257241.JPG)
![6_4](https://user-images.githubusercontent.com/62474292/101722476-ae3fa980-3aed-11eb-9bdc-2dac70990e3e.JPG)
![6_5](https://user-images.githubusercontent.com/62474292/101722489-b1d33080-3aed-11eb-9475-0a16fd835f43.JPG)

`code`
```py

```
#### 문제 7
![7_치킨배달](https://user-images.githubusercontent.com/62474292/101722503-b4358a80-3aed-11eb-8dd7-d3db083dddb7.JPG)
![7_2](https://user-images.githubusercontent.com/62474292/101722482-af70d680-3aed-11eb-9b3a-d36eb3c03453.JPG)

`code`
```py

```
#### 문제 8 (프로그래머스 코드 참고)
![8_외벽점검](https://user-images.githubusercontent.com/62474292/101722470-abdd4f80-3aed-11eb-9d44-bc33326eee98.JPG)
![8_2](https://user-images.githubusercontent.com/62474292/101722494-b26bc700-3aed-11eb-8a49-26dda341ac61.JPG)
![8_3](https://user-images.githubusercontent.com/62474292/101722484-b0096d00-3aed-11eb-9293-beac5b51ca90.JPG)
![8_4](https://user-images.githubusercontent.com/62474292/101722492-b26bc700-3aed-11eb-96b9-5c1f972d1312.JPG)
![8_5](https://user-images.githubusercontent.com/62474292/101722485-b0a20380-3aed-11eb-970f-68f9826e01c3.JPG)
![8_6](https://user-images.githubusercontent.com/62474292/101722496-b3045d80-3aed-11eb-9f79-51de2809e8f6.JPG)

`code`
```py

```

<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
