---
title: "[ALGO] Shortest Path"
categories: 
  - CS
tags:
  - ALGORITHM
last_modified_at: 2020-11-16 12:00:00
comments: true
use_math: true # MathJax On
---

#### Shortest Path 2

#### 힙 자료구조
- 우선순위 큐를 구현하기 위하여 사용하는 자료구조 중 하나
- 우선순위 큐는 우선순위가 가장 높은 데이터를 가장 먼저 삭제
- 파이썬에서는 일반적으로 heapq 라이브러리를 통해 우선순위 큐를 사용 (기본적으로 최소 힙 구조)
- 대부분의 프로그래밍 언어에서는 우선순위 큐 라이브러리에 데이터의 묶음을 넣으면, 첫 번째 원소를 기준으로 우선순위를 설정
- 최소 힙을 최대 힙처럼 사용하기 위해서 일부로 우선순위에 해당하는 값에 음수 부호(-)를 붙엿 넣었다가 나중에 우선순위 큐에서 꺼내 다음에 다시 음수 부호(-)를 붙여 원래의 값으로 되돌리는 방식도 사용
- 힙 -> 삽입 : O(logN), 삭제 : O(logN)
- 데이터의 개수가 N개일 때 힙 자료구조에 데이터를 모두 넣은 뒤에 모두 꺼내는 경우 : O(NlogN) + O(NlogN) = O(NlogN) -> 힙 정렬

#### 다익스트라 알고리즘
- 시간 복잡도 : O(ElogV), E : 간선의 개수, V : 노드의 개수
- 힙 자료구조 사용 (현재 가장 가까운 노드를 저장하기 위한 목적으로 우선순위 큐 사용)

STEP 1. 출발 노드를 제외한 모든 노드의 최단 거리를 무한으로 설정 한 후, 우선순위 큐에 1번 노드(출발노드)르 넣는다. 이 때 1번 노드로 가느 거리는 자기 자신까지 도달하는 거리이기 때문에 0
![KakaoTalk_Photo_2021-08-11-10-33-51](https://user-images.githubusercontent.com/62474292/128956426-f406284c-9587-4a34-82f5-a6916b4cc4b7.png)
STEP 2. 거리가 가장 짧은 노드를 선택학 위해서는 우선순위큐에서 그냥 노드를 꺼내면 된다. 따라서 우선순위 큐에서 노드르 꺼낸 뒤에 해당 노드를 이미 처리한 적이 있다면 무시하며 되고, 아직 처리하지 않은 노드에 대해서만 처리하면 된다. 우선순위 큐에서 노드를 꺼내면 (0,1)이 나오는데 이는 1번 노드까지 가느 최단 거리가 0이라는 의미이므로, 1번 노드르 거쳐서 2,3,4번 노드로 가는 최소 비용을 업데이트한다. 이렇게 더 짧은 경로를 찾은 노드 정보들은 다시 우선순위 큐에 넣는다.
![2](https://user-images.githubusercontent.com/62474292/128956432-dc7a6498-4d05-4404-b52c-c1149ca81c94.png)
STEP 3. 동일한 과정을 반복하면 이번에느 (1,4)가 나온다. 아직 노드 4를 방문하지 않았으므로 같은 원리로 노드 4와 연결된 간선들을 업데이트 해준다.
![3](https://user-images.githubusercontent.com/62474292/128956436-fc7f970c-0faa-402d-8333-25c39f58bd84.png)
STEP 4. 동일한 과정이지만 이번에는 2번 노드를 거쳐 현재 최단 거리가 더 짧게 갱신되는 경우가 없으므로 우선순위 큐에 추가로 들어가느 원소는 없다.
![4](https://user-images.githubusercontent.com/62474292/128956438-0684f043-f426-42cc-977d-103c3b22ea27.png)
STEP 5. 노드 5에 대해 동일한 과정을 진행한다.
![5](https://user-images.githubusercontent.com/62474292/128956441-95709b76-0a1c-4997-aa11-6506e6a8c6d1.png)
STEP 6. 노드 3에 대해 동일한 과정을 진행한다.
![6](https://user-images.githubusercontent.com/62474292/128956447-4d0b89b4-da7a-4efb-a953-6ed6c7274fa5.png)
STEP 7. (4,3)를 꺼내는데 3번 노드는 앞서 처리된 적이 있으므로 무시한다. (3번 노드의 최단 거리 테이블이 4보다 작음을 통해 알 수 있음)
![7](https://user-images.githubusercontent.com/62474292/128956450-2542be30-2dd5-4595-9e9a-5f10dcc4536e.png)
STEP 8. 번 노드에 대해 처리한다.
![8](https://user-images.githubusercontent.com/62474292/128956452-f1d717b5-d453-418d-a99e-7d003075c911.png)
STEP 9. (5,3)을 꺼내는데 3번 노드는 앞서 처리되었으므로 무시한다.
![9](https://user-images.githubusercontent.com/62474292/128956455-871a9cc6-86d2-47eb-a632-9f72f5946993.png)

```py
import heapq
import sys
input = sys.stdin.readline
INF = int(1e9)  # 무한을 의미하는 값으로 10억을 설정

# 노드의 개수, 간선의 개수 입력받기
n, m = map(int, input().split())
# 시작 노드 번호를 입력받기
start = int(input())
# 각 노드에 연결되어 있는 노드에 대하 정보를 담는 리스트를 만들기
graph = [[] for i in range(n+1)]
# 최단 거리 테이블을 모두 무한으로 초기화
distance = [INF] * (n+1)

# 모든 간선 정보를 입력받기
for _ in range(m):
  a, b, c = map(int, input().split())
  # a번 노드에서 b번 노드로 가는 비용이 c라느 의미
  graph[a].append((b,c))

def dijkstra(start):
  q = []
  # 시작 노드로 가기 위한 최단 경로는 0으로 설정하여, 큐에 삽입
  heapq.heappush(q, (0,start))
  distance[start] = 0
  while q:  # 큐가 비어있지 않다면
    # 가장 최단 거리가 짧은 노드에 대한 정보 꺼내기
      dist, now = heapq.heappop(q)
      # 현재 노드 이미 처리된 적이 있다면 무시
      if distance[now] < dist:
        continue
      # 현재 노드와 연결된 다른 인접한 노드들을 확인
      for i in graph[now]:
        cost = dist + i[1]
        # 현재 노드를 거쳐서, 다른 노드로 이동하는 거리가 더 짧은 경우
        if cost < distance[i[0]]:
          distance[i[0]] = cost
          heapq.heappush(q, (cost, i[0]))

# 다익스트라 알고리즘 수행
dijkstrat(start)

# 모든 노드로 가 위한 최단 거리를 출력
for i in range(1, n+1):
  # 도달할 수 없는 경우, 무한으로 출력
  if distance[i] == INF:
    print("INFINITY")
  else:
    print(distance[i]) 
```

#### 시간 복잡도 분석
- 노드를 하나씩 꺼내 검사하는 반복문(while문)은 노드의 개수 V이상의 횟수로느 반복되지 않음
- 또한 V번 반복될 때마다 각각 자신과 연결된 간선들을 모두 확인 (즉, 최대 E회만큼)
- 즉, 전체 다익스트라 최단 경로 알고리즘은 E개의 원소를 우선순위 큐에 넣었다가 모두 빼내는 연산과 매우 유사
- 즉 최대 E개의 간선 데이터르 힙에 넣었다가 다시 빼는 연산이므로 O(ElogE)
- 이 때, 중복 간선을 포함하지 않는 경우, E는 항상 V^2보다 작다
- 따라서 일반적으로 다익스트라 알고리즘의 시간 복잡도는 O(ElogE) -> O(ElogV^2) = O(2ElogV) -> O(ElogV)이다.
