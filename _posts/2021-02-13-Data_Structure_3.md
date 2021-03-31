---
title: "[Data Structure] Linked_List"
categories: 
  - CS
tags:
  - DATA STRUCTURE
last_modified_at: 2021-02-13 12:00:00
comments: true
use_math: true # MathJax On
---

#### Linked List

- Linked_list는 데이터와 다음 노드의 주소를 담고 있는 노드들이 한 줄로 연결되어 있는 방식의 자료 구조이다.
- 연결되는 방향에 따라 Singly_Linked_List, Doubly_Linked_List, Circular_Linked_List가 있다.
- Linked_List는 데이터를 노드의 형태로 저장한다. 노드에는 데이터와 다음 노드를 가리키는 포인터를 담은 구조로 이루어져 있다.
- Linked_List는 Array처럼 선형 데이터 자료구조이지만, Array는 물리적인 배치 구조 자체가 연속적으로 저장되어 있는 반면 Linked_List는 노드의 next부분에 다음 노드의 위치를 저장함으로써 선형적인 데이터 자료구조를 가진다.
- Python에서 List의 삽입과 삭제의 시간복잡도가 O(N)인 이유가 Array에서는 물리적인 데이터의 저장 위치가 연속적이어야 하므로 데이터를 옮기는 연산작업이 필요하기 때문이었는데 Linked_List는 데이터를 삽입, 삭제하는 경우, 노드의 next부분에 저장한 다음 노드의 포인터만 변경해주면 되므로 조금 더 효율적으로 데이터를 삽입, 삭제할 수 있다. 
- Linked List에서 탐색의 경우 첫 노드부터 시작하여야 하기 때문에 O(N)만큼의 시간이 필요해서 상대적으로 비효율적이다.

#### Linked List의 장단점
- 길이를 동적으로 조절할 수 있다.
- 데이터의 삽입과 삭제가 쉽다

- 임의의 노드에 바로 접근하기 어렵다
- 다음 노드의 위치를 저장하기 위한 추가 공간이 필요하다.
- Cache locality를 활용해 근접 데이터를 사전에 캐시에 저장하기 어렵다
- 거꾸로 탐색하기가 어렵다 (양방향 연결리스트로 해결 가능)

#### Singly_Linked_List 구현

```py
class Node(object):
    def __init__(self, data):
        self.data = data
        self.next = None


class SinglyLinkedList(object):
    def __init__(self):
        self.head = None
        self.count = 0

    def append(self, node):
        if self.head == None:
            self.head = node
        else:
            cur = self.head
            while cur.next != None:
                cur = cur.next
            cur.next = node

    def getdataIndex(self, data):
        cur = self.head
        idx = 0
        while cur:
            if cur.data == data:
                return idx
            cur = cur.next
            idx += 1
        return -1

    def insertNodeAtIndex(self, idx, node):
        cur = self.head
        prev = None
        cur_index = 0

        # Add node at the front of the linked list
        if idx == 0:
            if self.head:
                node.next = self.head
                self.head = node
            else:
                self.head = node
        else:
            # Add at given index or at the end of the linked list
            while cur_index < idx:
                if cur:
                    prev = cur
                    cur = cur.next
                else:
                    break
                cur_index += 1
            if cur_index == idx:
                node.next = cur
                prev.next = node
            else:
                return -1


    def insertNodeAtData(self, data, node):
        # Add new node before the given data
        index = self.getdataIndex(data)
        if 0 <= index:
            self.insertNodeAtIndex(index, node)
        else:
            return -1

    def deleteAtIndex(self, idx):
        cur_index = 0
        cur = self.head
        prev = None
        nextn = self.head.next
        if idx == 0:
            self.head = nextn
        else:
            while cur_index < idx:
                if cur.next:
                    prev = cur
                    cur = nextn
                    nextn= nextn.next
                else:
                    break
                cur_index += 1
            if cur_index == idx:
                prev.next = nextn
            else:
                return -1
        pass

    def clear(self):
        self.head = None

    def print(self):
        cur = self.head
        string = ""
        while cur:
            string +=str(cur.data)
            if cur.next:
                string += "->"
            cur = cur.next
        print(string)


if __name__ == "__main__":
    s = SinglyLinkedList()
    s.append(Node(1))
    s.append(Node(2))
    s.append(Node(3))
    s.append(Node(5))
    s.insertNodeAtIndex(3, Node(4))
    s.print()
    print(s.getdataIndex(1))
    print(s.getdataIndex(2))
    print(s.getdataIndex(3))
    print(s.getdataIndex(4))
    print(s.getdataIndex(5))
    s.insertNodeAtData(1,Node(0))
    s.print()
```
