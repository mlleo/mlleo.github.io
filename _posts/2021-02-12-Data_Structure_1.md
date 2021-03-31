---
title: "[Data Structure] ARRAY"
categories: 
  - CS
tags:
  - DATA STRUCTURE
last_modified_at: 2021-02-12 12:00:00
comments: true
use_math: true # MathJax On
---

#### ARRAY

- 여러 원소들이 순차적으로 메모리에 저장(contiguous memory locations)하는 구조
- 기본적으로 배열은 모든 원소가 같은 자료형이어야 하며, 배열의 크기를 변경할 수 없다.
- 배열의 주소값을 담은 변수에는 배열의 첫 원소의 메모리 주소가 저장되어 있으므로 배열의 index를 통해 다른 원소에 빠르게 접근할 수 있다. 
- 배열의 원소가 모두 같은 자료형으로 이루어져 있기 대문에, 다음 index의 원소가 위치한 물리적인 위치로 이동할 때 얼만큼 이동해야 하는지 알 수 있다.

#### ARRAY 장단점
- 구현이 쉽다
- index를 활용하여 원소에 쉽게 접근할 수 있어서 조회를 O(1)에 할 수 있다.
- 순차탐색에서도 배열은 연속된 메모리 공간에 할당됨에 따라 연결리스트보다 빠른 성능을 보인다.
- OS의 cache locality(운영체제는 물리적으로 근접한 위치의 데이터가 자주 활용됨에 따라 미리 cache에 넣어둠으로써 CPU 성능 향상)를 활용할 수 있다.

- 원소를 삽입, 삭제 시 기존 원소를 이동해야 하는 연산작업이 필요하므로 비효율적이다.
- 초기에 선언한 크기를 변경할 수 없다. (사용하지 않은 메모리가 낭비된다)
- 배열 요소를 삭제했더라도 변수의 선언이 해제되지 않는 이상 메모리를 점유하고 있어 재사용이 불가능하다.

#### PYTHON List
- 파이썬에서는 따로 정적 배열을 제공하지 않으며 동적 배열의 역할을 List가 수행한다. (Array와는 다르게 자유롭게 크기를 확장할 수 있다.)
- 동적 배열의 원리는 미리 초기값을 작게 잡아 배열을 생성하고, 데이터가 추가되면서 곽 채워지면, 늘려주고 모두 복사하는 방식으로 더블링(Doubling)이라고 일컫어진다.
- List 자료형도 Array처럼 index를 사용하여 원소에 접근할 수 있지만, 서로 다른 자료형을 원소로 가질 수 있다.
- 리스트 안의 원소들은 그 값들을 자유롭게 변경할 수 있다. (Mutable)

#### List 삽입
- 순차적으로 데이터를 삽입하고 조회할 필요가 있을 때 활용한다.
- index가 0인 곳에 삽입하는 작업이 많이 일어날 경우에는 collections.deque를 이용하여 appendleft() 메소드를 활용한다.

```py
arr = ['a','b','c']
arr.append('d')           # output : ['a','b','c','d']
arr.insert(0,'f')         # 지정된 index의 위치에 삽입(list 범위를 초과하는 index의 경우 맨 뒤에 삽입)  output : ['f','a','b','c','d']
```

#### List 삭제
- 원소를 삭제할 때는 순차적으로 저장되어 있는 데이터들의 위치를 이동해야 한다.

```py
arr = ['a','b','c']
del[0]                # output : ['b','c']
arr.remove('b')       # 원소를 찾아서 삭제   output : ['c']
```
#### List 조회(검색)
- 조회는 순차적으로 원소를 탐색해야 하며, 최악의 경우에는 모든 원소를 다 확인해야 하는 단점이 있다.

```py
arr = ['a','b','c']

arr.index('b')          # index()함수를 통해 탐색     output : 1
def find(arr, ch):
  i = -1
  for c in arr:
    i+= 1
    if ch == c:
      return i
  return -1

find(arr,'b')       # 1
find(arr,'d')       # -1
```

#### 별도 List 관련 함수
- 원소 추가 (append)
- 정렬 (sort)
- 리스트 뒤집기 (reverse)
- 원소 제거 (remove)
- 원소 꺼내기 (pop)
- 포함된 요소 x의 개수 세기 (count)
- 리스트 확장 (extend)
