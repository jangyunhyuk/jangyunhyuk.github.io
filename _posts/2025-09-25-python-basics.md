---
# ====== Front Matter ======
title: "파이썬 기초 (Python Basics)"
description: "파이썬 기초 문법 요약 — 변수, 연산자, 문자열, 리스트, 제어문, 함수 등 개념 정리"  
date: 2025-09-25 21:00:00 +0900
categories: [Language, Python]
tags: [python, Python-Basics]
pin: false
toc: true
comments: false
render_with_liquid: false
math: false
mermaid: false
lang: "ko"
---

## 기본 연산자

### 1. 변수
- 변수는 값을 담아두는 공간이라고 할 수 있다.
> 나중에 재사용하기 위해 변수를 선언한다.

### 2. 산술 연산자
- 값을 더하거나 빼는 등의 계산을 처리를 하는 연산자

| 연산 | 의미  |
|:-: |-|
| a + b | 더하기 |
| a - b | 빼기 |
| a * b | 곱하기 |
| a / b | 나누기 |
| a // b | 나눈 몫 |
| a % b | 나머지 |
| a ** b | 거듭제곱 |

### 3. 비교 연산자
- 두 값을 비교하고, 결과로 True 또는 False를 반환한다.

| 연산 | 의미  |
|:-: |-|
| > | 크다 |
| < | 작다 |
| >= | 크거나 같다 |
| <= | 작거나 같다 |
| != | 같지 않다 |
| == | 같다 |

### 4. 복합 대입 연산자
- 연산 결과를 다시 변수에 바로 저장할 때 사용한다.

| 연산 | 의미  |
|:-: |-|
| a += b | a = a + b |
| a -= b | a = a - b |
| a *= b | a = a * b |
| a /= b | a = a / b |
| a //= b | a = a // b |
| a %= b | a = a % b |
| a **= b | a = a ** b |

### 5. 자료형 변환
- 데이터의 자료형을 바꾸는 함수들이다.
- 관련 함수
  - int(): 정수로 변환
  - float(): 실수로 변환
  - bool(): True / False 형태로 변환
  - str(): 문자열로 변환
- type() 함수로 자료형 확인 가능

---

## 문자열 자료형

### 1. 문자열 표현
- 문자열 표현 방법
  - 문자열은 작은따옴표(’) 또는 큰따옴표(”)로 감싸서 만든다.

```python
# 문자열 출력 예시
print('Hello World')
print("Hello World")
```
- 변수에 문자열을 저장할 수도 있다.

```python
# 문자열 변수 선언
a = 'Hello'
b = "World"

# 출력 확인
print(a, b) # Hello World
```

### 2. 문자열 연산
- \+ : 문자열을 이어 붙인다.
- \* : 지정한 횟수만큼 반복한다.

```python
# 문자열 더하기
s1 = 'Hello'
s2 = 'World'
hw = s1 + ' ' + s2

# 결과 확인
print(hw) # Hello World
```

- 문자열에 숫자를 곱하면 지정한 숫자만큼 문자열이 반복

```python
# 문자열 반복 출력
print('*' * 17)                      # *****************
print('** ' + s1 + ' ' + s2 + ' **') # ** Hello World **
print('*' * 17)                      # *****************
```

### 3. 문자열 내에 값 추가 (f-String)
- 문자열 내에 다른 값을 추가하고 싶을 때 f-String을 사용한다.
- 문자열 앞에 소문자 f를 붙이고, 문자열 안 중괄호 {} 안에 변수 이름을 대입

```python
# 변수 선언
name = '홍길동'
age = 25
score = 2345.6789

# 문자열 포매팅
print(f'이름: {name}')
print(f'나이: {age}')
print(f'점수: {score}')
print(f'{age}살의 {name}의 점수는 {score}입니다.')

# 이름: 홍길동
# 나이: 25
# 점수: 2345.6789
# 25살의 홍길동의 점수는 2345.6789입니다.
```

---

## 리스트 자료형


### 1. 리스트(List) 자료형
- 대괄호 [] 안에 여러 값을 쉼표로 구분하여 작성한다.

```python
# 리스트 생성
score = [85, 95, 90, 75]

# 출력 확인
print(score) # [85, 95, 90, 75]
print(len(score)) # 4
```

### 2. range() 함수
- 연속된 숫자 범위를 생성할 때 사용한다.
- range(n): 0 부터 n-1 까지 1 씩 증가하는 정수 범위가 됨
- range(m, n): m 부터 n-1 까지 1 씩 증가하는 정수 범위가 됨
- range(m, n, x): m 부터 n-1 까지 x 만큼씩 증가하는 정수 범위가 됨

```python
# 숫자 리스트 생성
nums1 = list(range(10))        # [0,1,2,3,4,5,6,7,8,9]
nums2 = list(range(0,10,2))    # [0,2,4,6,8]
nums3 = list(range(1,10,3))    # [1,4,7]
```

### 3. 리스트 인덱싱
- 리스트 안에서 특정 값을 찾을 때 사용하는 데이터를 인덱스(Index)라고 함
- 인덱스로 특정 요소를 찾는 과정을 인덱싱(Indexing)이라고 함
- 대괄호 [ ] 안에 0부터 시작하는 정수형 위치 인덱스를 지정해 원하는 위치의 요소를 확인
- 순방향 인덱스는 0부터 시작, 역방향 인덱스는 -1부터 시작

```python
# 인덱스 접근 예시
member = ['홍길동', 85, '한사랑', 95, '일지매', 90, '박여인', 75]

print(member[0]) # 홍길동
print(member[3]) # 95
print(member[-1]) # 75
print(member[-7]) # 85
```

### 4. 리스트 슬라이싱
- 인덱스를 사용해 특정 범위의 요소를 찾는 과정을 슬라이싱(Slicing)이라 함
- 대괄호안에 [m:n] 형태로 범위를 지정하여 요소를 확인함
- m 부터 n-1 까지, 즉 n 번째 요소는 결과에 포함되지 않음(주의)

```python
member = ['홍길동', 85, '한사랑', 95, '일지매', 90, '박여인', 75]

print(member[2:6]) # ['한사랑', 95, '일지매', 90]
print(member[6:]) # ['박여인', 75]
print(member[:4]) # ['홍길동', 85, '한사랑', 95]
print(member[:]) # ['홍길동', 85, '한사랑', 95, '일지매', 90, '박여인', 75]
print(member[0:-2]) # ['홍길동', 85, '한사랑', 95, '일지매', 90]
```

### 5. 리스트 요소 추가
- append() 메서드 뒤에 요소 하나 추가

```python
# 리스트 확장 예시
nums = list(range(5))
print(nums) # [0, 1, 2, 3, 4]

# 요소 추가
nums.append(5)
nums.append(6)
print(nums) # [0, 1, 2, 3, 4, 5, 6]
```

- insert() 메서드로 중간에 요소 하나 추가

```python
# 리스트 만들기
nums = [10, 20, 40, 50]
print(nums) # [10, 20, 40, 50]

# 요소 추가
nums.insert(2, 30)
print(nums) # [10, 20, 30, 40, 50]
```

- 리스트 더하기 연산을 사용해 뒤에 요소 추가

```python
# 리스트 만들기
nums = list(range(5))
print(nums) # [0, 1, 2, 3, 4]

# 리스트 더하기
nums = nums + [5, 6, 7, 8, 9]
print(nums) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

- extend() 메서드 뒤에 요소 추가

```python
# 리스트 만들기
nums = list(range(5))
print(nums) # [0, 1, 2, 3, 4]

# 여러 요소 추가
nums.extend([5, 6, 7, 8, 9])
print(nums) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 6. 리스트 요소 삭제
- del 문으로 요소 하나 지우기

```python
# 리스트 만들기
nums = list(range(10, 100, 10))
print(nums) # [10, 20, 30, 40, 50, 60, 70, 80, 90]

# 요소 삭제
del nums[7]
print(nums) # [10, 20, 30, 40, 50, 60, 70, 90]
```

- 범위로 여러 요소 지우기, 모두 지우기

```python
# 요소 범위 지우기
nums[4:] = []
print(nums) # [10, 20, 30, 40]

# 리스트 초기화
nums = []
print(nums) # []
```

---

## 튜플, 집합, 딕셔너리 자료형

### 1. 튜플(Tuple) 자료형
- 소괄호 ()로 만든다.
- 한 번 생성하면 값 변경이 불가능하다(immutable).

```python
# 여러 형태의 튜플 만들기
score1 = (90, 85, 70)
score2 = 90, 85, 70
score3 = (90, 85, 70, ('A', 'B', 'D', 'F'))
```

### 2. 집합(Set) 자료형
- 중괄호 {}를 사용한다.
- 중복이 없고, 순서가 중요하지 않다.
- 합집합(\|), 교집합(&), 차집합(-) 연산이 가능하다.

```python
# 정수를 갖는 집합
nums = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
```
```python
# 문자열을 갖는 집합
members = {'홍길동', '한사랑', '일지매', '박여인'}
```
```python
# 여러 자료형을 갖는 집합
etc = {'홍길동', 100, (1, 2, 3), '박여인'}
```

### 3. 합집합, 교집합, 차집합
- 합집합: \| 또는 union() 메서드 사용
- 교집합: & 또는 intersection() 메서드 사용
- 차집합: - 또는 difference() 메서드 사용
- 대칭 차집합: ^ 또는 symmetric_difference() 메서드 사용

```python
# 교집합 구하기
member_set1 = set(['홍길동', '한사랑', '일지매', '박여인'])
member_set2 = set(['한사랑', '홍길민', '강우동'])
member_set3 = member_set1.intersection(member_set2)
print(member_set3) # {'한사랑'}

# 차집합 구하기
member_set4 = member_set1 - member_set2
print(member_set4) # {'박여인', '홍길동', '일지매'}
```

### 4. 딕셔너리(Dictionary) 자료형
- {key1: value1, key2: value2, key3: value3}의 형태로 키:값 쌍으로 데이터를 저장한다.
- 딕셔너리는 요소의 순서가 의미가 없으며, key를 사용해 value를 확인

```python
# 일정한 정보를 갖는 딕셔너리
word = {'love': '사랑', 'happy': '행복', 'dream': '꿈'}

# 다양한 정보를 갖는 딕셔너리
member = {'이름': '홍길동', '나이': 20, '지역': '서울'}

# 리스트 안의 리스트나 튜플, 튜플 안의 리스트나 튜플 값을 딕셔너리로 변환
members = (('홍길동', 100), ('일지매', 90), ('한여인', 90), ('강우동', 95))
member_dic = dict(members)
```

### 5. 딕셔너리 조회
- 딕셔너리는 요소 순서가 없으므로 인덱싱과 슬라이싱을 할 수 없음
  - 참고: 3.7 버전 부터는 입력된 요소 순서대로 정렬되어 유지됨
- Key를 사용해 Value를 조회
- in 연산자를 사용해 해당 Key가 있는지 확인 가능

```python
# 이름 확인
member = {'이름': '홍길동', '취미': ['독서', '여행', '걷기']}
print(member['이름']) # 홍길동

# 데이터 존재 여부 확인
print('이름' in member) # True
print('홍길동' in member) # False
print('여행' in member['취미']) # True
```

### 6. 딕셔너리 변경, 추가, 삭제
- 있는 key를 수정하면 변경, 없는 Key를 수정하면 Key:Value 형태로 추가됨

```python
# 딕셔너리 만들기
member = {'이름': '홍길동', '나이': 20}

# 변경
member['나이'] = 30
print(member) # {'이름': '홍길동', '나이': 30}
member['취미'] = ['독서', '여행']
print(member) # {'이름': '홍길동', '나이': 30, '취미': ['독서', '여행']}
```

- Key를 지정해 del 문으로 삭제 가능(조회 → 삭제 순서로 진행 권고)

```python
# 딕셔너리 만들기
member = {'이름': '홍길동', '나이': 20, '지역':'서울'}

# 삭제
del member['나이']
print(member) # {'이름': '홍길동', '지역': '서울'}
```

---

## 제어문

### 1. if문
- if문

```python
my_score = 73

if my_score >= 80:
  my_score += 10
```


- if...else 문

```python
my_score = 73

if my_score >= 80:
  my_result = 'Pass'
else:
  my_result = 'Fail'
```

- if...elif...else문

```python
my_score = 73

if my_score >= 90:
  my_grade = 'A'
elif my_score >= 80:
  my_grade = 'B'
elif my_score >= 70:
  my_grade = 'C'
elif my_score >= 60:
  my_grade = 'D'
else:
  my_grade = 'F'
```

### 2. for문
- 첫 번째 값부터 마지막 값까지 하나씩 가져가서 처리
- 구문

```python
# 범위 값 출력
for i in range(5):
  print(i)

# 리스트 요소 출력
fruits = ['apple', 'banana', 'cherry']
for i in fruits:
  print(i)
```

### 3. 리스트와 for문
- enumerate() 함수
  - 문자열 또는 컨테이너형 자료를 입력 받아, 순번(=인덱스)과 값을 포함하는 오브젝트를 반환
  - 반복문이 몇 번째 요소를 처리 중인지 확인이 필요할 때 사용
  - for 문에서 리스트 자료형에 대해 사용하는 경우가 많음

```python
fruits = ['apple', 'banana', 'cherry']

# 인덱스와 값 출력
for index, value in enumerate(fruits):
  print(index, value)

# 0 apple
# 1 banana
# 2 cherry
```


- 반복문 확장

```python
nums = [0, 1, 2, 3, 4]

# 요소 제곱
squares = [x ** 2 for x in nums]
```

- 조건에 맞는 데이터만 가져오기

```python
# 짝수만 추출해 제곱
even_squares = [x ** 2 for x in nums if x % 2 == 0]
```

### 4. 딕셔너리와 for 문
- 리스트와 비슷하나, 키(Key)와 값(Value)으로 제어

```python
score = {'홍길동': 85, '한사랑': 95, '일지매': 90}

# 이름과 점수 출력
for key in score:
  value = score[key]
  print(f'{key}: {value}')
```

- Items() 메서드를 사용해 키와 값을 쌍으로 확인할 수 있음

```python
# 이름과 점수 출력
for key, value in score.items():
  print(f'{key}: {value}')
```

- 확장 문법

```python
# 점수가 90보다 큰 이름과 점수 출력
score_over_90 = {k: v for k, v in score.items() if v > 90}
print(score_over_90) # {'한사랑': 95}
```

#### 5. while 문
- 조건문이 True인 동안 while문 안의 문장이 반복해서 실행됨
- 특정 상황에서 반복을 중지하도록 while 문 안에서 조건을 제어해야 함

```python
# 리스트 만들기
fruits = ['apple', 'banana', 'cherry']

# 요소 출력
i = 0
while i < len(fruits):
  print(fruits[i])
  i += 1
```

- break 문
  - 반복문 안에서 특정 조건이 되어 반복문을 빠져 나올 때 사용
- continue 문
  - 반복문을 중단시키지 않고 다음 반복으로 넘어갈 때 사용

```python
# 문자 입력하면 continue, 0 입력하면 break, 아니면 10으로 나눈 나머지 표시
while True:
  response = input('숫자를 입력하세요(0 = 종료):')
  if not response.isnumeric():
    continue
  if int(response) == 0:
    break
  result = int(response) % 10
  print(f'{response} 나누기 10의 나머지는 {result}입니다.')
```

---

## 함수

### 1. 함수 개념 및 선언
- 프로그래밍에서 함수란?
  - 반복해 사용할 코드를 미리 정의해 두는 모듈
- def 문으로 함수를 만든다.

```python
# 간단한 덧셈 함수
def add(a, b):
  return a + b

# 함수 사용
a = 10
b = 20
c = add(a, b)
print(f'{a}, {b}의 합은 {c}') # 10, 20의 합은 30
```

### 2. 매개변수
- 매개변수는 필수적인 것은 아님
- 매개변수 없이 처리만 하는 함수도 충분히 만들어 활용 가능함

- 매개변수가 없는 함수

```python
# 인사 함수
def hello():
  print('안녕하세요? 반갑습니다!')

# 함수 사용
hello() # 안녕하세요? 반갑습니다!
```

- 매개변수가 있는 함수

```python
# 인사 함수
def hello(name):
  print(f'{name}님 안녕하세요? 반갑습니다!')

# 함수 사용
hello('홍길동') # 홍길동님 안녕하세요? 반갑습니다!
```

### 3. 매개변수 기본값
- 기본값이 없는 함수는 매개변수가 없으면 오류가 발생
- '매개변수 = 값' 형태로 기본값을 지정할 수 있음
- 이름을 전달하지 않으면 '여러분'이 기본값으로 사용되게 수정한 예

```python
# 인사 함수
def hello(name='여러분'):
  if name == '여러분':
    print(f'{name} 안녕하세요? 반갑습니다!')
  else:
    print(f'{name}님 안녕하세요? 반갑습니다!')

# 함수 사용
hello('홍길동') # 홍길동님 안녕하세요? 반갑습니다!
hello() # 여러분 안녕하세요? 반갑습니다!
```

### 4. 결괏값 반환
- 함수 안에서 결괏값을 반환할 때는 return 문을 사용

```python
# 합계 반환 함수
def calculate1(a, b):
  summ = a + b
  return summ

# 함수 사용
r1 = calculate1(10, 5)
print(r1) # 15
```

- 반환되는 값이 없는 함수의 결괏값을 받아 출력하면 None이 출력

```python
# 함수 만들기
def calculate1(a, b):
  summ = a + b
  print(summ)

# 함수 사용
r1 = calculate1(10, 5) # 15
print(r1) # None
```

### 5. 여러 개의 결괏값
- 함수가 여러 개의 결괏값을 반환할 수도 있음

```python
# 두 가지 결과 반환
def calculate2(a, b):
  summ = a + b
  mult = a * b
  return summ, mult

# 함수 사용
r1, r2 = calculate2(10, 5)
print(r1) # 15
print(r2) # 50
```