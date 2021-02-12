---
title: "[Data Structure] ARRAY"
categories: 
  - CS
last_modified_at: 2021-02-12 12:00:00
comments: true
use_math: true # MathJax On
---

#### ARRAY

- 자료구조는 크게 메모리 공간 기반의 연속(Contiguous)방식과 포인터 기반의 연결(Link)방식으로 나뉜다.
- 배열은 이 중에서 연속방식의 가장 기본이 되는 자료형이다.
- 배열은 어느 위치에서나 O(1)에 조회가 가능하다는 장점이 있다.
- 배열이란 일반적으로 고정된 크기만큼의 연속된 메모리 할당을 의미하는데, 실제 데이터에서는 전체 크기를 가늠하기 힘든 경우가 많기 대문에 동적 배열이라는 개념이 등장했다.
- 동적 배열의 원리는 미리 초기값을 작게 잡아 배열을 생성하고, 데이터가 추가되면서 곽 채워지면, 늘려주고 모두 복사하는 방식으로 더블링(Doubling)이라고 일컫어진다.
- 파이썬에서는 따로 정적 배열을 제공하지 않으며 동적 배열의 역할을 리스트(list)가 수행한다.


#### Probelm 1
![1](https://user-images.githubusercontent.com/62474292/107736592-d47c0280-6d45-11eb-98b5-0cec32bee16c.JPG)

`code`
```py
# brute force : O(N^2)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i,j]
```

`code`
```py
# use 'in' function :  O(N^2)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i, n in enumerate(nums):
            diff = target-n
            if diff in nums[i+1:]:
                return nums.index(n), nums[i+1:].index(diff) + (i+1)
```

`code`
```py
# dictionary : O(N)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_map = {}
        # key와 value를 바꿔서 dictionary에 저장
        # target에서 첫 번재 수를 뺀 결과를 key로 조회
        for i, num in enumerate(nums):
            if target-num in nums_map:
                return [nums_map[target-num],i]
            nums_map[num] = i
```

`code`
```py
# Two pointer

```

`code`
```py
# brute force
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i,j]
```

#### Problem 2
![2](https://user-images.githubusercontent.com/62474292/107736596-d5149900-6d45-11eb-8593-c3100ad07b4d.JPG)

