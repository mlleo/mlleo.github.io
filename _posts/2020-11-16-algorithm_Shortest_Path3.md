---
title: "[ALGO] Shortest Path 3"
categories: 
  - CS
tags:
  - ALGORITHM
last_modified_at: 2020-11-16 12:00:00
comments: true
use_math: true # MathJax On
---

#### Shortest Path 3

#### 플로이드 워셜 알고리즘
- 다익스트라 알고리즘은 '한 지점에 다른 특정 지점까지의 최단 경로를 구해야 하는 경우'에 사용할 수 있는 최단 경로 알고리즘
- 플로이드 워셜 알고리즘은 '모든 지점에서 다른 모든 지점까지의 최단 경로를 모두 구해야 하는 경우'에 사용할 수 있는 알고리즘
- 다익스트라 알고리즘은 단계마다 최다 거리를 가지는 노드를 하나씩 반복적으로 선택한 후 해당 노드를 거쳐 가는 경로를 확인하며, 최단 거리 테이블을 갱신하는 방식으로 동작
- 플로이드 워셜 알고리즘 또한 단계맏 '거쳐 가는 노드'를 기준으로 알고리즘을 수행하지만 매번 방문하지 않은 노드 중에서 최단 거리를 갖는 노드를 찾을 필요가 없다
- 노드의 개수 N개일 때, 알고리즘상으로 N번의 단계를 수행하며, 각 단계마다 O(N^2)의 연산을 통해 '현재 노드를 거쳐 가는' 모든 경로를 고려
- 모든 노드에 대하여 모든 노드로 가는 최단 거리 정보를 담아야 하기 때문에 2차원 리스트에 '최단 거리' 정보를 담음
- 플로이드 워셜의 총 시간 복잡도는 O(N^3)

#### 원리
- 각 단계에서는 해당 노드를 거쳐 가는 경우를 고려
- 예를 들어 1번 노드 대해서 확인할 때는 1번 노드를 거쳐 지나가는 모든 경우를 고려
- A -> 1번 -> B로 가는 비용을 확인한 후에 A->B 최단 거리 테이블 값보다 작을 경우 업데이트
- 즉, 현재 확인하고 있는 노드를 제외하고, N-1개의 노드 중에서 서로 다른 노드 (A, B) 쌍을 선택 -> O(N^2)

STEP 1. 초기 테이블 설정 : 연결된 간선은 그 값을 채워 넣고, 연결되지 않은 간선은 무한(int(1e9))이라는 값을 채워넣음
![1](https://user-images.githubusercontent.com/62474292/128979467-e9ec95b8-b2c4-4d55-a560-7d606f01340d.png)
STEP 2. 1번 노드
![2](https://user-images.githubusercontent.com/62474292/128979471-b3cd9644-0ee9-4a76-841c-781dac5f02de.png)
STEP 3. 2번 노드
![3](https://user-images.githubusercontent.com/62474292/128979475-8e91d59c-17fc-4f15-a135-11b656dce39c.png)
STEP 4. 3번 노드
![4](https://user-images.githubusercontent.com/62474292/128979482-0e973317-609a-4be5-b069-a723724f825f.png)
STEP 5. 4번 노드
![5](https://user-images.githubusercontent.com/62474292/128979489-8935b546-d66f-4e9d-a2d5-b5bd20b58e5b.png)

```py
INF = int(1e9)    # 무한을 의미하는 값으로 10억을 설정

# 노드의 개수 및 간선의 개수 입력받기
n = int(input())
m = int(input())
# 2차원 리스트(그래프 표현)를 만들고, 모든 값을 무한으로 초기화
graph = [[INF] * (n+1) for _ in range(n+1)]

# 자기 자신에서 자기 자신으로 가는 비용은 0으로 초기화
for a in range(1, n+1):
  for b in range(1, n+1):
    if a == b:
        graph[a][b] = 0

# 각 간선에 대한 정보르 입력받아, 그 값으로 초기화
for _ in range(m):
  # A에서 B로 가는 비용을 C락 설정
  a, b, c = map(int, input().split())
  graph[a][b] = c

# 점화식에 따라 플로이드 워셜 알고리즘 수행
for k in range(1, n+1):
  for a in range(1, n+1):
    for b in range(1, n+1):
      graph[a][b] = min(graph[a][b], graph[a][k] + graph[k][b])

# 수행된 결과를 출력
for a in range(1, n+1):
  for b in range(1, n+1):
    # 도달할 수 없는 경우, 무한을 출력
    if graph[a][b] == INF:
      print("INFINITY")
    else:
      print(graph[a][b], end = " ")
  print()
```
