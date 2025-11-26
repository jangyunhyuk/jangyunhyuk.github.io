---
# ====== 기본 Front Matter ======
title: "비동기 작업 처리(async/await)"
description: "JavaScript 비동기 작업 처리(async/await) 정리"
date: 2025-11-27 00:50:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, async, await]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## async
- 함수를 비동기 함수로 만들어주는 키워드
- async 함수는 항상 Promise를 반환함
  - 일반 값 반환 → 자동으로 Promise로 감싸져 반환
  - Promise 반환 → 그대로 반환

```js
async function getData() {
  return {
    name: "장윤혁",
    hobby: "sport",
  };
}

console.log(getData());

// [[Prototype]]: Promise
// [[PromiseState]]: "fulfilled"
// [[PromiseResult]]: Object
```

### 이미 Promise를 반환하는 경우
- 이 경우 async는 별다른 일을 하지 않음
- 반환하는 Promise를 그대로 반환함

```js
async function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve({
        name: "장윤혁",
        hobby: "sport",
      });
    }, 1500);
  });
}

console.log(getData());

// [[Prototype]]: Promise
// [[PromiseState]]: "fulfilled"
// [[PromiseResult]]: Object
```

## await
- async 함수 내부에서만 사용 가능
- Promise가 처리될 때까지 기다렸다가, resolve의 반환값을 그대로 변수에 담아줌
- await은 함수 전체를 멈추는 것이 아니라, async 함수 내부 흐름만 일시 정지한다.
- 코드가 마치 동기 코드처럼 작성됨

```js
async function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve({
        name: "장윤혁",
        hobby: "sport",
      });
    }, 1500);
  });
}

async function printData() {
  const data = await getData(); // resolve 데이터가 data에 담김
  console.log(data);
}
printData();

// hobby: "sport"
// name: "장윤혁"
// [[Prototype]]: Object
```
