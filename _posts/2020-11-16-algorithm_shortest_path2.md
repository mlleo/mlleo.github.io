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
STEP 2.
![2](https://user-images.githubusercontent.com/62474292/128956432-dc7a6498-4d05-4404-b52c-c1149ca81c94.png)
![3](https://user-images.githubusercontent.com/62474292/128956436-fc7f970c-0faa-402d-8333-25c39f58bd84.png)
![4](https://user-images.githubusercontent.com/62474292/128956438-0684f043-f426-42cc-977d-103c3b22ea27.png)
![5](https://user-images.githubusercontent.com/62474292/128956441-95709b76-0a1c-4997-aa11-6506e6a8c6d1.png)
![6](https://user-images.githubusercontent.com/62474292/128956447-4d0b89b4-da7a-4efb-a953-6ed6c7274fa5.png)
![7](https://user-images.githubusercontent.com/62474292/128956450-2542be30-2dd5-4595-9e9a-5f10dcc4536e.png)
![8](https://user-images.githubusercontent.com/62474292/128956452-f1d717b5-d453-418d-a99e-7d003075c911.png)
![9](https://user-images.githubusercontent.com/62474292/128956455-871a9cc6-86d2-47eb-a632-9f72f5946993.png)
