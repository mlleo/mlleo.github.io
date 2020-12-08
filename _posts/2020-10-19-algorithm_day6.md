---
title: "[ALGO] Search (DFS)"
categories: 
  - CS
last_modified_at: 2020-10-19 12:00:00
comments: true
use_math: true # MathJax On
---

#### DFS(Depth-First Search)
- 그래프에서 깊은 부분을 우선적으로 탐색하는 알고리즘
- 데이터의 개수가 N개인 경우 O(N)
- 스택 자료구조를 이용
  1. 탐색 시작 노드를 스택에 삽입하고 방문 처리를 한다.
  2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면 그 인접 노드를 스택에 넣고 방문 처리를 한다. 방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼낸다.
  3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.  <br>
  tip. '방문 처리'는 스택에 한 번 삽입되어 처리된 노드가 다시 삽입되지 않게 체크하기 위함! <br>
  tip. DFS 알고리즘은 통상적으로 노드 번호가 낮은 순서부터 처리하도록 구현! <br><br>
  
EX. DFS 예시 (방문 처리된 노드는 회색으로, 현재 처리하는 스택의 최상단 노드는 노란색으로 표현)

![1](https://user-images.githubusercontent.com/62474292/101473884-ba145a00-398d-11eb-8da2-90077d80fbbb.png)
![2](https://user-images.githubusercontent.com/62474292/101473893-bc76b400-398d-11eb-8784-b3bda7db8725.png)
![3](https://user-images.githubusercontent.com/62474292/101473840-b1238880-398d-11eb-8d5d-b1412f759f8b.png)
![4](https://user-images.githubusercontent.com/62474292/101473875-b680d300-398d-11eb-91e5-f065ec3a36b2.png)
![5](https://user-images.githubusercontent.com/62474292/101473835-b08af200-398d-11eb-8d97-d3b959a97984.png)
![6](https://user-images.githubusercontent.com/62474292/101473908-c00a3b00-398d-11eb-8586-6ad6e5d955db.png)
![7](https://user-images.githubusercontent.com/62474292/101473843-b1bc1f00-398d-11eb-9ff3-cd20a484a54f.png)
![8](https://user-images.githubusercontent.com/62474292/101473831-af59c500-398d-11eb-9d0e-7f8caa969fa5.png)
![9](https://user-images.githubusercontent.com/62474292/101473869-b5e83c80-398d-11eb-89c1-beacddc36ff1.png)
![10](https://user-images.githubusercontent.com/62474292/101473844-b254b580-398d-11eb-9b92-b48f76ad444d.png)
![11](https://user-images.githubusercontent.com/62474292/101473868-b54fa600-398d-11eb-9fdf-4e570592357a.png)
![12](https://user-images.githubusercontent.com/62474292/101473887-ba145a00-398d-11eb-8f37-00090728edd4.png)
![13](https://user-images.githubusercontent.com/62474292/101473858-b385e280-398d-11eb-9f25-f9faf6cac3be.png)
![14](https://user-images.githubusercontent.com/62474292/101473878-b7196980-398d-11eb-96de-29eefee033a0.png)
![15](https://user-images.githubusercontent.com/62474292/101473853-b2ed4c00-398d-11eb-878d-bf54729aa788.png)
![16](https://user-images.githubusercontent.com/62474292/101473862-b41e7900-398d-11eb-8f7c-ca99517d2e56.png)
![17](https://user-images.githubusercontent.com/62474292/101473865-b4b70f80-398d-11eb-9234-24475684d467.png)
![18](https://user-images.githubusercontent.com/62474292/101473902-be407780-398d-11eb-90b1-f1239bbf5fd5.png)
![19](https://user-images.githubusercontent.com/62474292/101473879-b7b20000-398d-11eb-84b3-c794e8876ae9.png)

Result : 1-> 2-> 5-> 8-> 4-> 9-> 3-> 7-> 6

`code`
```py
def dfs(graph,v,visited):
  visited[v] = True   # 현재 노드를 방문 처리
  print(v, end='')
  for i in graph[v]:  # 현재 노드와 연결된 다른 노드를 재귀적으로 방문
    if not visited[i]:
      dfs(graph,i,visited)

graph = [   # 각 노드가 연결된 정보를 리스트 자료형으로 표현
  [],
  [2,3,4],
  [1,5],
  [1,7],
  [1,8],
  [2,8,9],
  [7],
  [3,6],
  [4,5],
  [5]
]

visited = [False] * 9   # 각 노드가 방문된 정보를 리스트 자료형으로 표현

dfs(graph,1,visited)    # 정의된 DFS 함수 호출
```
```
1 2 5 8 4 9 3 7 6
```

#### 기본 예제 1





