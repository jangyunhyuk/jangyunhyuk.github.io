---
# ====== 기본 Front Matter ======
title: "Spread 연산자와 Rest 매개변수"
description: "JavaScript의 Spread 연산자와 Rest 매개변수 개념"
date: 2025-11-24 17:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, spread, rest]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## Spread 연산자
- "흩뿌리다", "펼치다" 라는 의미
- 배열이나 객체에 저장된 여러 값을 개별 요소로 펼치는 역할
- 함수 호출, 배열/객체 복사, 결합 등에 자주 사용

### 배열에서 Spread 사용
#### Spread 사용 전
- 배열의 각 요소를 하나씩 꺼내 작성

```js
let arr1 = [1, 2, 3];
let arr2 = [4, arr1[0], arr1[1], arr1[2], 5, 6];
console.log(arr2) // [4, 1, 2, 3, 5, 6]
```

#### Spread 적용
- ...arr1로 배열 요소를 한 번에 펼칠 수 있음

```js
let arr1 = [1, 2, 3];
let arr2 = [4, ...arr1, 5, 6];
console.log(arr2) // [4, 1, 2, 3, 5, 6]
```

### 객체에서 Spread 사용
#### Spread 사용 전
- 객체의 속성을 하나씩 복사

```js

let obj1 = {
    a: 1,
    b: 2
};

let obj2 = {
    a: obj1.a,
    b: obj1.b,
    c: 3,
    d: 4
};

```
#### Spread 사용 후
- ...obj1로 객체 속성을 한 번에 펼쳐서 복사 가능

```js
let obj1 = {
    a: 1,
    b: 2
};

let obj2 = {
    ...obj1,
    c: 3,
    d: 4
};

console.log(obj2); // {a: 1, b: 2, c: 3, d: 4}
```

#### 함수 호출에서 Spread 사용
- 배열 요소를 각각의 매개변수로 전달할 때 유용

```js
let arr1 = [1, 2, 3];

function funcA(p1, p2, p3) {
    console.log(p1, p2, p3);
}
funcA(...arr1); // 1 2 3
```

## Rest 매개변수
- Rest는 "나머지"라는 뜻
- 함수의 매개변수에 ...를 사용하면, 넘어오는 값들을 배열로 묶어서 받는 역할
- Spread가 "펼치는 것"이라면 Rest는 묶는 것

### 기본 Rest 매개변수 예시
- 전달된 모든 인자를 배열로 수집

```js
function funcB(...rest){
    console.log(rest);
}

funcB(1, 2, 3); // [1, 2, 3]
```

### 일부는 개별 변수로 받고, 나머지는 rest로 묶기
- 앞쪽 매개변수는 일반 변수로 받고, 남은 나머지 값들은 rest 배열에 저장

```js
let arr1 = [1, 2, 3, 4];

function funcB(one, two, ...rest){
    console.log(one); // 1
    console.log(two); // 2
    console.log(rest); // [3, 4]
}

funcB(...arr1); 
```
