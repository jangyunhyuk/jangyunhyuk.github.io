---
# ====== 기본 Front Matter ======
title: "콜백 함수"
description: "JavaScript의 콜백 함수 개념"
date: 2025-11-21 09:00:00 +0900
categories: [JavaScript, basics]   # 최대 2개 권장
tags: [javascript, callback, 콜백 함수]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 콜백 함수(Callback Function)
- 자신이 아닌 다른 함수에 인수로 전달되어 실행되는 함수
- 함수를 값처럼 전달하고, 전달받은 함수가 특정 시점에 실행되는 구조

```js
function main(value) {  // value는 함수
    value();            // 전달받은 함수를 실행
}

function sub() {
    console.log("sub");
}

main(sub); // sub 함수를 인수로 전달
```

## 함수 표현식
- 함수를 값처럼 직접 만들어 전달하는 방식

```js
function main(value) {
    value();
}

main(() => {
    console.log("sub");
});
```
## 콜백 함수의 활용
- 중복된 로직은 제거하고, 변경되는 부분만 함수로 전달

```js
function repeat(count) {
    for (let idx = 1; idx <= count; idx++){
        console.log(idx);
    }
}

function repeatDouble(count) {
    for (let idx = 1; idx <= count; idx++){
        console.log(idx * 2);
    }
}

function repeatTriple(count) {
    for (let idx = 1; idx <= count; idx++){
        console.log(idx * 3);
    }
}
repeat(5)
repeatDouble(5)
repeatTriple(5)
```
- 개선 코드

```js
function repeat(count, callback) {
    for (let idx = 1; idx <= count; idx++){
        callback(idx);
    }
}

repeat(5, (idx) => {
    console.log(idx)
}) 

repeat(5, (idx) => {
    console.log(idx * 2)
}) 

repeat(5, (idx) => {
    console.log(idx * 3)
}) 
```