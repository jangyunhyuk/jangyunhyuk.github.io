---
# ====== 기본 Front Matter ======
title: "구조 분해 할당(Destructuring)"
description: "JavaScript의 구조 분해 할당 개념"
date: 2025-11-24 15:30:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, destructuring]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 구조 분해 할당(Destructuring Assignment)
- 배열 또는 객체 내부의 값을 빠르게 꺼내 변수로 분리하는 문법
- 변수 선언과 동시에 값 추출이 가능하여 코드 가독성이 높아짐

### 배열의 구조 분해 할당
#### 기본 형태
- 순서(index)를 기준으로 변수에 값이 들어감

```js
let arr = [1, 2, 3];

let [one, two, three] = arr;
console.log(one, two, three); // 1 2 3
```
#### 필요한 값만 추출
- 배열 길이보다 적게 받아도 문제 없음

```js
let arr = [1, 2, 3];

let [one, two] = arr;
console.log(one, two); // 1 2
```

#### 없는 인덱스는 undefined
- 배열에 존재하지 않는 값은 자동으로 undefined 처리됨

```js
let arr = [1, 2, 3];

let [one, two, three, four] = arr;
console.log(one, two, three, four); // 1 2 3 undefined
```

#### 기본값(default value) 설정
- 값이 없을 때 기본값으로 대체됨

```js
let arr = [1, 2, 3];

let [one, two, three, four = 4] = arr;
console.log(one, two, three, four); // 1 2 3 4
```

### 객체의 구조 분해 할당
- 중괄호 {}를 사용
- key 이름을 기준으로 값을 가져오기 때문에 순서와는 무관함

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

let {name, age, hobby} = person;
console.log(name, age, hobby); // 장윤혁 28 운동
```

#### 없는 key는 undefined

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

let {name, age, hobby, extra} = person;
console.log(name, age, hobby, extra); // 장윤혁 28 운동 undefined
```

#### 기본값(default value) 설정

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

let {name, age, hobby, extra = "hello"} = person;
console.log(name, age, hobby, extra); // 장윤혁 28 운동 hello
```

#### 별칭(alias) 지정
- age 값을 받아서 myAge라는 이름으로 사용하고 싶을 때 사용

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

let {name, age: myAge, hobby, extra = "hello"} = person;
console.log(name, myAge, hobby, extra); // 장윤혁 28 운동 hello
```

### 객체 구조 분해 할당을 이용해서 함수의 매개변수를 받는 방법
- 매개변수에서 필요한 값만 꺼내서 바로 사용 가능

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

const func = ({name, age, hobby}) => {
    console.log(name, age, hobby); // 장윤혁 28 운동
}

func(person);
```