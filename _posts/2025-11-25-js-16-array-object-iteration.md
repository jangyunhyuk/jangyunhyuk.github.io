---
# ====== 기본 Front Matter ======
title: "반복문으로 배열과 객체 순회하기"
description: "JavaScript에서 배열과 객체를 순회하는 반복문 정리"
date: 2025-11-25 10:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, array, object, iteration]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## 순회(iteration)
- 배열, 객체에 저장된 여러개의 값에 순서대로 하나씩 접근하는 과정

### 배열 순회
#### 배열 인덱스
- 카운터 변수(i)에 인덱스가 들어가기 때문에 인덱스를 활용한 순회가 가능

```js
// 배열 순회
let arr = [1, 2, 3];

// 배열 인덱스
for(let i = 0; i < arr.length; i++){
    console.log(arr[i]); // 1
                         // 2
                         // 3
}
```

#### for of 반복문
- 인덱스를 사용하지 않고, 배열 요소만 순서대로 꺼내서 순회

```js
let arr = [1, 2, 3];

for(let item of arr){
    console.log(item); // 1
                       // 2
                       // 3
}
```

### 객체 순회
#### object.keys
- 객체에서 key 목록을 배열로 반환

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

let keys = Object.keys(person);
for(let key of keys){
    const value = person[key];
    console.log(key, value) // name 장윤혁
                            // age 28
                            // hobby 운동
}
```

#### object.values
- 객체에서 value 목록을 배열로 반환

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

let values = Object.values(person);
for (let value of values){
    console.log(value); // 장윤혁
                        // 28
                        // 운동
}
```

#### for in
- 객체의 key를 순회하는 반복문

```js
let person = {
    name: "장윤혁",
    age: 28,
    hobby: "운동"
};

for(let key in person){
    const value = person[key];
    console.log(key, value); // name 장윤혁
                             // age 28
                             // hobby 운동
}
```