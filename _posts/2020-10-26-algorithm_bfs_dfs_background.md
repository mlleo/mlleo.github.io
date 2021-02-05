---
title: "[ALGO] Search (DFS/BFS) Background"
categories: 
  - CS
last_modified_at: 2020-10-18 12:00:00
comments: true
use_math: true # MathJax On
---

Search Algorithm (BFS / DFS) Background

#### Background
- Stack (LIFO)
  - 별도로 재귀함수는 내부적으로 스택 자료구조와 동일 (나중에 호출된 함수가 먼저 수행을 끝내야 그 이전에 호출된 함수가 종료되므로)

`code`
```py
stack = []
stack.append(1)
stack.append(2)
stack.append(3)
stack.pop()
stack.append(4)
stack.pop()
print(stack)  # 가장 밑에 있는 원소부터 출력
print(stack[::-1])  # 가장 위에 있는 원소부터 출력
```
```
[1,2]
[2,1]
```
- Queue (FIFO)
  - deque 객체를 리스트 자료형으로 변경하고자 하면 list(queue)!
  
`code`
```py
from collections import deque

queue = deque() # queue구현을 위해 deque 라이브러리 사용

queue.append(1)
queue.append(2)
queue.append(3)
queue.append(4)
queue.popleft()
queue.append(5)
queue.append(6)
queue.popleft()

print(queue)  # 먼저 들어온 순서대로 출력
queue.reverse() # 역순으로 변경
print(queue)  # 나중에 들어온 순서대로 출력
```
```
deque([3,4,5,6])
deque([6,5,4,3])
```
  


- 그래프 표현 방식 2가지
  - 인접 행렬 (Adjacency Matrix) : 2차원 배열로 그래프의 연결관계를 표현
    - 모든 관계를 저장하므로 노드 개수가 많을수록 메모리를 불필요하게 낭비
  
`code`
```py
INF = 9999999 # 무한의 비용 선언
  graph = [
    [0,4,9]
    [4,0,INF]
    [9,INF,0]
  ]
print(graph)
```
```
[[0,4,9],[4,0,9999999],[9,9999999,0]]
```
  
  - 인접 리스트 (Adjacency List) : 리스트로 그래프의 연결관계를 표현
    - 연결된 정보만을 저장하기 때문에 메모리를 효율적으로 사용하지만 특정한 두 노드가 연결되어 있는지에 대한 정보를 얻는 속도는 인접 행렬에 비해 느림
  
`code`
```py
graph = [[] for _ in range(3)]  # 행(Row)이 3개인 2차원 리스트 생성
graph[0].append((1, 4))  # 노드 0에 연결된 노드 정보 저장(노드,거리)
graph[0].append((2, 9))

graph[1].append((0, 4))  # 노드 1에 연결된 노드 정보 저장(노드,거리)

graph[2].append((0, 9))  # 노드 2에 연결된 노드 정보 저장(노드,거리)

print(graph)
```
```
[[(1,4),(2,9)],[(0,4)],[(0,9)]]
```

<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)

