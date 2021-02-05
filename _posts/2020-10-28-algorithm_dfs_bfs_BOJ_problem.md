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

```

#### 1697번

`code`
```py

```
