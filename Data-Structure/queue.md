## Queue (큐)
### 정의
<img width="400" alt="image" src="https://github.com/ghi512/ghi-log/assets/77954741/52c67361-5fc8-4f57-bd14-504190110b6f"><br>
큐는 선입선출(FIFO, First In First Out)로 먼저 삽입된 데이터가 먼저 삭제되는 자료 구조이다.
<br><br>

### Queue에서 지원하는 연산
1. **enqueue** <br>
큐의 끝부분에 자료를 추가한다.<br>

2. **dequeue** <br>
큐의 앞부분에서 항목을 제거하고 반환한다.<br>

3. **front** 또는 **peek** <br>
큐의 앞부분에 있는 자료를 반환한다. (제거X)

4. **isEmpty**<br>
큐가 비어 있는지 확인한다. <br><br>


### python에서의 Queue
파이썬에서는 큐를 여러 가지 방법으로 구현할 수 있다. 가장 간단한 방법 중 하나는 리스트(list)를 사용하는 것이지만, 리스트를 사용하면 성능 저하가 발생할 수 있다. 따라서 이를 대체하여 ```collections.deque``` 또는 ```queue.Queue```를 사용할 수 있다.<br>


### 1. 리스트(list)를 사용한 큐 구현
리스트를 사용하여 큐를 구현할 수 있지만, 리스트의 앞부분에서 요소를 제거하는 연산이 비효율적일 수 있다.

<details>
<summary>리스트 큐 구현 코드 & 예시</summary>

```python
class ListQueue:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return len(self.items) == 0

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        if not self.isEmpty():
            return self.items.pop(0)
        else:
            raise IndexError("dequeue from empty queue")

    def front(self):
        if not self.isEmpty():
            return self.items[0]
        else:
            raise IndexError("front from empty queue")

    def size(self):
        return len(self.items)
```
```python
q = ListQueue()
q.enqueue(1)
q.enqueue(2)
q.enqueue(3)
print(q.dequeue())  # 출력: 1
print(q.front())    # 출력: 2
print(q.size())     # 출력: 2
```
</details>
<br>

### 2. collections 모듈의 deque
deque는 double-ended queue의 약자로 양방향 큐이고, 데이터를 양방향에서 추가하고 제거할 수 있다.<br> 속도가 리스트에 비해 굉장히 빠르다. list = O(n), deque = O(1)<br>
<details>
<summary>사용할 수 있는 함수 목록</summary>

- append
- appendleft
- clear
- copy
- count
- extend
- extendleft
- index
- insert
- maxlen
- pop
- popleft
- remove
- reverse
- rotate
</details>

#### [1] 초기화
collections 모듈의 deque 클래스를 사용하여 deque(덱)를 표현한다.

```python
from collections import deque

dq1 = deque() # deque([])

data = [1,2,3]
dq2 = deque(data) # deque([1, 2, 3])

dq3 = deque([4,5,6]) # deque([4, 5, 6])
```

#### [2] append & appendleft
append 메서드를 이용해 deque의 오른쪽 끝에 원소를 추가한다. <br>
appendleft 메서드를 이용해 deque의 왼쪽 끝에 원소를 추가할 수 있다. <br>

```python
dq1.append(1)
dq1.append(2)
print(dq1) # deque([1, 2])

dq1.appendleft(0)
print(dq1) # deque([0, 1, 2])
```

#### [3] pop & popleft
pop 메서드를 이용해 deque의 오른쪽 끝에서 원소를 제거하고 리턴받는다.<br>
popleft 메서드를 이용해 deque의 왼쪽 끝에서 원소를 제거하고 리턴받는다.<br>

```python
dq = deque([0, 1, 2])
dq.pop() # 2
print(dp) # deque([0, 1])

dq.popleft() # 0
print(dp) # deque([1])
```

#### [4] peek 또는 top
덱의 가장 오른쪽 원소를 구할 때는 [-1], 가장 왼쪽 원소를 구할 때는 [0]을 이용한다. 이때는 덱에서 원소를 제거하지 않는다.

```python
dq = deque([1, 2, 3])
right = dq[-1] # 3
left = dq[0] # 1
```

#### [5] len
덱의 원소의 개수를 len 메서드를 이용해 구한다.

```python
dq = deque([1, 2, 3])
print(len(dq)) # 3
```

#### [6] extend & extendleft
extend 메서드를 이용해 deque의 오른쪽 끝에 iterable의 모든 원소를 추가한다.<br>
extendleft 메서드를 이용해 deque의 왼쪽 끝에 iterable의 모든 원소를 추가한다. 추가된 원소의 순서는 반대가 된다.

```python
dq = deque([1, 2])
dq.extend([3, 4])
print(dq) # deque([1, 2, 3, 4])

dq.extendleft([5, 6])
print(dq) # deque([6, 5, 1, 2, 3, 4])
```
✓ 이때 append는 단일 원소, extend는 여러 원소를 iterable 형태로 받아 추가한다는 차이점이 있다.<br>
✓ [공식문서 참고](https://docs.python.org/3/library/collections.html#collections.deque)
<br><br>


### 3. queue 모듈을 사용한 큐 구현
queue 모듈은 스레드 안전한 큐 구현을 제공한다.

#### [1] 초기화
```python
from queue import Queue
q = Queue()
```

#### [2] put
put 메서드를 이용해 큐의 끝에 원소를 추가한다.
```python
q.put(1)
q.put(2)
# 큐 상태: 1, 2
```

#### [3] get
get 메서드를 이용해 큐의 앞에서 원소를 제거하고 리턴받는다.
```python
# 큐 상태: 1, 2

q.get() # 1

# 큐 상태: 2
```

#### [4] peek 또는 top
Queue 클래스는 직접적으로 peek 메서드를 제공하지 않으므로, 큐의 가장 앞의 원소를 확인하려면 get 메서드로 원소를 제거한 후 다시 넣는 방법을 사용하거나, 큐를 복사해서 사용하는 등의 우회 방법을 사용해야 한다. <br>
기본적으로 큐는 이 작업을 위해 설계되지 않았으므로, 대안으로 deque를 사용하는 것이 좋다.
```python
q.put(1)
q.put(2)

front = q.get() # 1
q.put(front)    # 다시 큐에 넣기

# 큐 상태: 2, 1
```

#### [5] len
큐의 원소의 개수를 qsize 메서드를 이용해 구한다.
```python
q.put(1)
q.put(2)
print(q.qsize()) # 2
```

#### [6] isEmpty
큐가 비었는지 여부를 empty 메서드를 이용해 확인한다.

```python
q = Queue()

if q.empty():
    print(1)
else:
    print(0)

# 비어있으므로 1 출력
```

✓ [공식문서 참고](https://docs.python.org/3/library/queue.html)
<br>

### 요약
- 리스트(list): 간단하지만 큐의 앞부분에서 요소를 제거하는 데 비효율적이다.
- collections.deque: 효율적이고 간편하며, 큐의 앞부분에서 요소를 제거하는 연산이 빠르다.
- queue.Queue: 스레드 안전성을 제공하며, 멀티스레드 환경에서 유용합니다. 큐의 앞부분을 직접 접근하는 방법(front)은 제공하지 않는다.

#### Reference
- [파이썬에서 큐(queue) 자료구조 사용하기](https://www.daleseo.com/python-queue/)