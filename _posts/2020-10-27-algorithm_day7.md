---
title: "[ALGO] Search (BFS)"
categories: 
  - CS
last_modified_at: 2020-10-27 12:00:00
comments: true
use_math: true # MathJax On
---

#### BFS(Breadth-First Search)
- 그래프에서 가까운 노드부터 우선적으로 탐색하는 알고리즘 (너비 우선 탐색)
- 데이터의 개수가 N개인 경우 O(N)
- 큐 자료구조를 이용
  1. 탐색 시작 노드를 큐에 삽입하고 방문 처리를 한다.
  2. 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리를 한다.
  3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.  <br>
  tip. '방문 처리'는 큐에 한 번 삽입되어 처리된 노드가 다시 삽입되지 않게 체크하기 위함! <br>
  tip. BFS 알고리즘은 통상적으로 노드 번호가 낮은 순서부터 처리하도록 구현! <br><br>

EX. BFS 예시 (방문 처리된 노드는 회색으로, 큐에서 꺼내 현재 처리하는 노드는 노란색으로 표현)

`CODE`
```py
from collections import deque

def bfs(graph, start, visited):   # BFS 메서드 정의
  queue = deque([start])
  visited[start] = True   # 현재 노드를 방문 처리
  while queue:    # 큐가 empty일때까지 반복
    v = queue.popleft()
    print(v, end=' ')
    for i in graph[v]:    # 해당 원소와 연결된, 아직 방문되지 않은 원소들을 큐에 삽입
      if not visited[i]:
        queue.append(i)
        visited(i) = True
        
graph = [             # 각 노드가 연결된 정보를 리스트 자료형으로 표현
  [],
  [2,3,4],
  [1,5],
  [1,6,7],
  [1,8],
  [2,8,9],
  [3,7],
  [3,6],
  [4,5,9],
  [5,8]
]

visited = [False] * 9   # 각 노드가 방문된 정보를 리스트 자료형으로 표현

bfs(graph,1,visited)    # 정의된 BFS 함수 호출
```
```
1 2 3 4 5 6 7 8 9
```

#### 기본 예제 1
