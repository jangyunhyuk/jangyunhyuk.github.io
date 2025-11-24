---
# ====== 기본 Front Matter ======
title: "Truthy와 Falsy"
description: "JavaScript의 Truthy·Falsy 개념"
date: 2025-11-24 09:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, truthy-falsy]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## Truthy와 Falsy
- JavaScript에서는 특정 값을 조건문에서 자동으로 true/false로 판별하는 특징이 있음
- 반복문, 조건문, 기본값 처리에서 자주 사용

### Falsy한 값
- undefined, null, 0, -0, NaN, 빈 문자열(""), 0n(BigInt)

```js
// 7가지의 Falsy 값
let f1 = undefined;
let f2 = null;
let f3 = 0;
let f4 = -0;
let f5 = NaN;
let f6 = "";
let f7 = 0n; // BigInt 타입의 0

if (!f1){
    console.log("falsy"); // falsy
}
```

### Truthy한 값
- Falsy 한 값들을 제외한 나머지 모든 값

```js
let t1 = "hello";
let t2 = 123;
let t3 = [];
let t4 = {};
let t5 = () => {};

if (t1){
    console.log("truthy"); // truthy
}
```

## 활용 사례
```js
function printName(person) {
    if (!person){
        console.log("person값이 없음");
        return;
    }
    console.log(person.name);
}

let person = {name: "장윤혁"};
printName(person);
```