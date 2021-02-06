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
from collections import deque
n= int(input())
graph = []
for _ in range(n):
    graph.append(list(map(int, input())))
dx = [-1,1,0,0]     # 상,하,좌,우
dy = [0,0,-1,1]
cnt = []
visited = [[0] * (n) for _ in range(n)]
def bfs(x,y):
    result = 0
    if graph[x][y] == 0 or visited[x][y] == 1:                  # 집이 없는 곳 or 이미 방문한 곳
        return 0
    queue = deque()
    queue.append((x,y))
    visited[x][y] = 1
    while queue:
        x,y = queue.popleft()
        result += 1
        for i in range(4):
            nx = x +dx[i]
            ny = y +dy[i]
            if nx < 0 or nx >= n or ny < 0 or ny >= n:
                continue
            if graph[nx][ny] == 0:
                continue
            if graph[nx][ny] == 1 and visited[nx][ny] == 0:
                queue.append((nx,ny))
                visited[nx][ny] = 1
    return result
for i in range(n):
    for j in range(n):
        target = bfs(i,j)
        if target > 0:
            cnt.append(target)
print(len(cnt))
cnt.sort()
for data in cnt:
    print(data)
```

#### 1012번

`code`
```py
from collections import deque

t = int(input())    # 테스트 케이스 개수
for _ in range(t):
    m,n,k = map(int, input().split())

    graph = [[0] * (m) for _ in range(n)]
    for _ in range(k):
        x,y = map(int, input().split())
        graph[y][x] = 1
    visited = [[0] * (m) for _ in range(n)]

    dy = [-1,1,0,0]
    dx = [0,0,-1,1]

    def bfs(y,x):
        if graph[y][x] == 0 or visited[y][x] == 1:                  # 배추가 없거나 이미 방문한 배추인 경우
            return False
        queue = deque()
        queue.append((y,x))
        while queue:
            y,x = queue.popleft()
            for i in range(4):
                nx = x + dx[i]
                ny = y + dy[i]
                if nx < 0 or nx >= m or ny < 0 or ny >= n:
                    continue
                if graph[ny][nx] == 0:
                    continue
                if graph[ny][nx] == 1 and visited[ny][nx] == 0:
                    queue.append((ny,nx))
                    visited[ny][nx] = 1
        return True


    count = 0
    for i in range(n):
        for j in range(m):
            if bfs(i,j) == True:
                count += 1
    print(count)
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
from collections import deque

def bfs(v):
    count = 0
    queue = deque()
    queue.append((v,count))
    while queue:
        data = queue.popleft()
        v = data[0]
        count = data[1]
        if not visited[v]:
            visited[v] = 1
            if v == k:
                return count
            count += 1
            if (v * 2) <= 100000:
                queue.append((v * 2, count))
            if (v + 1) <= 100000:
                queue.append((v + 1, count))
            if (v - 1) >= 0:
                queue.append((v - 1, count))
    return count


n, k = map(int, input().split())
visited = [0] * 100001
print(bfs(n))
```
