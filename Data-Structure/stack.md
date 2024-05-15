## Stack (스택)
### 정의
<img width="689" alt="stack" src="https://github.com/ghi512/ghi-log/assets/77954741/dfd075ba-ca86-4dee-8966-3dad9828473b"><br>
스택은 후입선출(LIFO, Last In First Out)로 가장 마지막에 들어온 자료가 가장 먼저 처리되는 자료구조이다.<br>
스택은 재귀 함수 호출, 역추적(backtracking), 문법 검사, 메모리 관리 등에서 다양하게 사용된다.
<br><br>

### stack에서 지원하는 연산
1. **push** <br>
스택에 자료를 넣는다.<br>

2. **pop** <br>
스택의 가장 위에 있는 자료를 제거하고 출력한다.<br>

3. **peek** 또는 **top** <br>
스택의 가장 위에 있는 자료를 출력한다. (제거X) <br>

4. **isEmpty**<br>
스택이 비어 있는지 확인한다. <br><br>

### python에서의 stack
#### [1] 초기화
파이썬에서는 리스트로 스택을 표현한다.<br>
```python
stack = []
```
#### [2] push
append 메서드를 이용해 리스트(스택)의 마지막에 원소를 추가한다.
```python
stack.append(1)
stack.append(2)

stack
# [1, 2]
```

#### [3] pop
pop 메서드를 이용해 리스트(스택)의 가장 마지막 원소를 제거하고 리턴받는다.
```python
stack = [1, 2, 3]
stack.pop() # 3

stack
# [1, 2]
```

#### [4] peek 또는 top
리스트의 마지막 인덱스를 의미하는 [-1]을 이용해서 스택의 가장 위의 원소를 구한다. 이때는 스택에서 원소를 제거하지 않는다.

```python
stack = [1, 2, 3]
top = stack[-1] # 3
```

#### [5] len
스택의 원소의 개수를 len 메서드를 이용해 구한다.
```python
stack = [1, 2, 3]
print(len(stack)) # 3
```

#### [6] isEmpty
스택이 비었는지 len을 이용해 확인한다.
```python
stack = []

if len(stack) == 0:
    print(1)
else:
    print(0)

# 비어있으므로 1 출력
```
