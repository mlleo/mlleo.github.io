---
title: "[ALGO] (DFS/BFS) BOJ PROBLEM"
categories: 
  - CS
last_modified_at: 2020-10-28 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 Baekjoon Online Judge (https://www.acmicpc.net/) 입니다

#### 1260번

`code`
```py
from collections import deque

n,m,v = map(int, input().split())   # n: vertex, m : edge, v: start vertex
graph = [[0] * (n+1) for _ in range(n+1)]

for _ in range(m):
    x,y = map(int, input().split())
    graph[x][y] = 1
    graph[y][x] = 1

visited = [0] * (n+1)

def dfs(v):
    visited[v] = 1
    print(v, end=' ')
    for i in range(1, n+1):
        if visited[i] == 0 and graph[v][i] == 1:
            dfs(i)

def bfs(v):
    queue = deque()
    queue.append(v)
    visited[v] = 0
    while queue:
        v = queue.popleft()
        print(v, end=' ')
        for i in range(1, n+1):
            if visited[i] == 1 and graph[v][i] == 1:
                queue.append(i)
                visited[i] = 0

dfs(v)
print()
bfs(v)
```

#### 2606번

`code`
```py
from collections import deque

n = int(input())        # 컴퓨터의 수
pair = int(input())     # 연결된 쌍의 수

graph = [[0] * (n+1) for _ in range(n+1)]
visited = [0] * (n+1)

for _ in range(pair):
    x,y = map(int, input().split())
    graph[x][y] = 1
    graph[y][x] = 1

def bfs(v):
    result = -1
    queue = deque()
    queue.append(v)
    visited[v] = 1
    while queue:
        v = queue.popleft()
        result += 1
        for i in range(1, n+1):
            if visited[i] == 0 and graph[v][i] == 1:
                queue.append(i)
                visited[i] = 1
    print(result)

bfs(1)
```

#### 2667번

`code`
```py

```

#### 1012번

`code`
```py

```

#### 2178번

`code`
```py
from collections import deque

n,m = map(int, input().split())

graph = []
for _ in range(n):
    graph.append(list(map(int, input())))

dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]

def bfs(x,y):
    queue = deque()
    queue.append((x,y))
    while queue:
        x,y = queue.popleft()
        for i in range(4):
            nx = x + dx[i]
            ny = y + dy[i]
            if nx < 0 or nx >= n or ny < 0 or ny >= m:
                continue
            if graph[nx][ny] == 0:
                continue
            if graph[nx][ny] == 1:
                queue.append((nx,ny))
                graph[nx][ny] = graph[x][y] + 1
    return graph[n-1][m-1]

print(bfs(0,0))
```

#### 1697번

`code`
```py

```
