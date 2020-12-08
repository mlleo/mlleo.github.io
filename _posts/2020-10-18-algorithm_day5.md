---
title: "[ALGO] Search (DFS/BFS)"
categories: 
  - CS
last_modified_at: 2020-10-18 12:00:00
comments: true
use_math: true # MathJax On
---

Search Algorithm (BFS / DFS)

#### Background
- Stack (LIFO)
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
