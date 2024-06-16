## Python 기본
<details>
<summary>목차</summary>

  * [출력](#--)
  * [변수와 자료형](#-------)
  * [출력 형식](#-----)
</details>

### 출력
- ```print()``` 사용
- ```"""출력할 문자"""``` 또는 ```'''출력할 문자'''```를 이용하면 따옴표 안에 넣은 그대로 출력할 수 있다.

---

### 변수와 자료형
- 자료형을 확인할 때는 ```type()```를 사용한다.
```python
a = "toy"
b = 3.5346
print(type(a)) # <class 'str'>
print(type(b)) # <class 'float'>
```
<br>

- 코딩 컨벤션(Coding Convention)
    - 일반적으로 변수나 함수명은 소문자로 쓰는 것이 원칙
    - 여러 단어를 사용하는 경우 언더바(Underscore) 사용
```python
# 권장
hello sam chavo will make_prime get_numbers
# 권장하지 않음
Hello sAm ChaVo WILL MAKE_____Prime GetNumbers
```

---

### 출력 형식
**[1] 변수 포맷과 % 사용**
```python
a = 5
print("A is %d" % a) # A is 5
b = "apple"
print("A is %d and B is %s" % (a, b)) # A is 5 and B is apple
```
- 변수 포맷
    - 문자열 %s
    - 문자 %c
    - 정수 %d
    - 실수 %f

<br>

**[2] format 함수 사용**
- 순서 혹은 이름을 명시하여 원하는 변수를 포맷에 맞춰 넣어줄 수 있다.
- 숫자를 적게되는 경우에는 format 함수에 적게되는 변수에 번호를 0번부터 붙였을 때 몇 번째 값인지를 명시한다.
- 숫자 대신 새로운 이름을 붙여 적는 것도 가능하다.
- 꼭 문자열 내 변수를 사용할 위치에 {}로 감싸줘야 한다.
```python
a, b = 5, "apple"

print("A is {0}".format(a)) # A is 5
print("A is {new_a}".format(new_a=a)) # A is 5

print("B is {0}".format(b)) # B is apple
print("B is {new_b}".format(new_b=b)) # B is apple

print("A is {0} and B is {1}".format(a, b)) 
# A is 5 and B is apple
print("A is {new_a} and B is {new_b}".format(new_a=a, new_b=b))
# A is 5 and B is apple
print("B is {1} and A is {0}".format(a, b))
# B is apple and A is 5
print("B is {new_b} and A is {new_a}".format(new_a=a, new_b=b))
# B is apple and A is 5
```

<br>

**[3] f 문자열 포맷 사용**
- python 3.6부터 이용 가능
- 문자열 앞에 f를 붙이고 변수 이름을 중괄호{}로 감싸면 원하는 변수를 해당 위치에 넣어줄 수 있다.

```python
a, b = 5, "apple"

print(f"A is {a}") # A is 5
print(f"B is {b}") # B is apple 
print(f"A is {a} and B is {b}") # A is 5 and B is apple
```
---
### 소수점 맞춰 출력하기
소수점 n번째 자리까지 출력하기

```python
a = 33.567268
print("%.4f" % a) # % 이용
print("{0:.4f}".format(a)) # format 함수 이용
print(f"{a:.4f}") # f 포맷 이용

# 출력 결과 -> 33.5673
```
---
### 문자열 type 바꾸기
```python
a = input()
a = int(a) # 정수형
a = float(a) # 실수형
```
---
### 공백으로 나눠 입력받기
python에서 입력은 한 줄 단위로만 받는다.<br>
공백으로 나눠 입력받고 싶다면 ```split()``` 함수를 이용한다.
```python
a = input()
print(a.split())
```
```python
# 출력 결과
>> 13 17
['13', '17']
```
---
### 삼항 연산자
```python
a = v1 if 조건 else v2
```
변수 a는 조건이 참인 경우 v1값을, 조건이 거짓인 경우에는 v2 값을 갖는다.