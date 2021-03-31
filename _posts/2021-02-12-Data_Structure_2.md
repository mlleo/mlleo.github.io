---
title: "[Data Structure] STACK"
categories: 
  - CS
tags:
  - DATA STRUCTURE
last_modified_at: 2021-02-13 12:00:00
comments: true
use_math: true # MathJax On
---

#### STACK

- LIFO(Last In First Out) 구조로서 데이터의 삽입, 삭제가 stack의 최상단에서부터 일어나는 자료구조
- 연속으로 저장된 데이터 구조를 가지고 있으며, 맨 위 요소에 대한 포인터(주소값)을 가지고 있는 Array나 Linked_List로 구현할 수 있다.

#### STACK 구현 - List
- Python의 List는 동적 배열이므로 배열에 새로운 원소를 삽입, 삭제할 수 있다.
- List 변수에는 첫번째 원소(맨 아래)의 주소값이 저장되기 때문에 맨 마지막으로 삽입한 원소(맨 위)의 주소값도 구할 수 있다.
- List를 사용하여 원소를 삽입(push), 삭제(pop) 할 때의 시간복잡도는 O(1)이다.

```py
Class Stack(list):
  def __init__(self):
    self.stack = []
  
  def push(self,data):
    self.stack.append(data)
  
  def pop(self):
    if self.is_empty():
      return -1
    return self.stack.pop()
    
  def peek(self):
    return self.stack[-1]
  
  def is_empty(self):
    if len(self.stack) == 0:
      return True
    return False
    
if __name__ == "__main__":
  s = Stack()
  s.push(1)
  s.push(2)
  s.push(3)
  print(s.peek())       # 3
  print(s.pop())        # 3
  print(s.pop())        # 2
  print(s.pop())        # 1
  print(s.pop())        # -1
```

#### Stack 구현 - Linked List
- Linked list의 head는 Stack의 가장 윗 부분을 가리킨다.
- 즉, 새로운 데이터가 들어오면 head는 새로운 데이터를 가리키게 된다.

```py
Class Node:
  def __init__(self,data):
    self.data = data
    self.next = None

Class Stack:
  def __init__(self):
    self.head = None
  
  def push(self, data):
    new_node = Node(data)
    new_node.next = self.head
    self.head = new_node
    
  def pop(self):
    if self.is_empty():
      return -1
    data = self.head.data
    self.head = self.head.next
    return data
  
  def is_empty(self):
    if self.head:
      return False
    return True
    
  def peek(self):
    if self.is_empty():
      return -1
    return self.head.data
```
