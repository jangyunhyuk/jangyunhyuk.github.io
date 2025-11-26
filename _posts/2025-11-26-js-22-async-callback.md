---
# ====== 기본 Front Matter ======
title: "비동기 작업 처리(콜백 함수)"
description: "JavaScript 비동기 작업 처리(콜백 함수) 정리"
date: 2025-11-26 14:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, async, callback, 비동기, 콜백]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## 콜백 함수
- 콜백(callback)은 "나중에 실행될 함수" 를 의미
- 비동기 작업이 끝났을 때 그 결과를 전달받아 실행하는 방식  
- setTimeout, 이벤트 기반 함수 등에서 자주 사용

```js
function add(a, b, callback) {
  setTimeout(() => {
    const sum = a + b;
    callback(sum); // 계산이 끝난 뒤 결과를 전달
  }, 3000);
}

add(1, 2, (value) => {
  console.log(value); // 3초 뒤에 3 출력
});

```
## 콜백를 또 다른 비동기 작업의 인수로 활용 1

```js

function orderFood(callback) {
  setTimeout(() => {
    const food = "떡볶이";
    callback(food);
  }, 3000);
}

function cooldownFood(food, callback) {
  setTimeout(() => {
    const cooldownedfood = `식은 ${food}`;
    callback(cooldownedfood);
  }, 2000);
}

orderFood((food) => {
  console.log(food); // 3초 뒤 떡볶이 출력
  cooldownFood(food, (cooldownedFood) => {
    console.log(cooldownedFood); // 떡볶이 출력 후 2초 뒤 식은 떡볶이 출력
  });
});
```

## 콜백함수를 또 다른 비동기 작업의 인수로 활용 2

```js
function orderFood(callback) {
  setTimeout(() => {
    const food = "떡볶이";
    callback(food);
  }, 3000);
}

function cooldownFood(food, callback) {
  setTimeout(() => {
    const cooldownedfood = `식은 ${food}`;
    callback(cooldownedfood);
  }, 2000);
}

function freezeFood(food, callback) {
  setTimeout(() => {
    const freezedFood = `얼린 ${food}`;
    callback(freezedFood);
  }, 2000);
}

orderFood((food) => {
  console.log(food);
  cooldownFood(food, (cooldownedFood) => {
    console.log(cooldownedFood);
    freezeFood(cooldownedFood, (freezedFood) => {
      console.log(freezedFood);
    });
  });
});
```
## 콜백 지옥(Callback Hell)
- 비동기 작업을 순서대로 실행해야 할 때 콜백 안에서 또 콜백을 호출하고 그 안에서 또 콜백을 넣는 구조가 이어짐
- 이런 형태가 많아질수록 코드가 오른쪽으로 점점 깊게 파고들고, 가독성이 급격히 떨어짐
- 유지보수 어려움
- 에러 핸들링도 복잡해짐

이러한 콜백 지옥 문제를 해결하기 위해 다음 글에서는 비동기 처리를 더 깔끔하게 도와주는 Promise를 다룬다.