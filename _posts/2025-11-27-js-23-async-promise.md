---
# ====== 기본 Front Matter ======
title: "비동기 작업 처리(Promise)"
description: "JavaScript 비동기 작업 처리(Promise) 정리"
date: 2025-11-27 00:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, async, promise, 비동기, 콜백지옥]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## Promise
- 비동기 작업을 보다 효율적으로 관리하기 위한 JavaScript 내장 객체
- 콜백 기반 비동기 처리의 단점(콜백 지옥)을 해결하기 위해 도입
- Promise 객체를 생성하면 executor 함수가 즉시 실행됨
- executor 함수는 두 개의 인자를 받음
  - resolve: 작업 성공
  - reject: 작업 실패

### Promise의 3가지 상태
1. 대기(Pending)상태: 작업이 아직 완료되지 않은 상태
2. 성공(Fulfilled)상태: 작업이 성공적으로 완료된 상태
3. 실패(Rejected)상태: 작업이 실패한 상태

### 대기(Pending)상태
executor 함수는 실행되지만 resolve/reject를 호출하지 않으면 Promise는 계속 Pending 상태로 유지됨

```js
const promise = new Promise(() => {
  setTimeout(() => {
    console.log("안녕!"); // 실행되지만 resolve/reject 없음 → Pending 유지
  }, 2000);
});

console.log(promise); // 2초후 안녕! 출력

// [[Prototype]] : Promise
// [[PromiseState]] : "pending"
// [[PromiseResult]] : undefined
```
### 성공(Fulfilled)상태
- resolve가 호출되면 Promise는 성공 상태로 변경됨
- resolve의 전달값은 then에서 받아 사용할 수 있음

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log("안녕!"); // 2초 뒤에 안녕! 출력
    resolve("안녕"); // Promise 상태 변경
  }, 2000);
});

setTimeout(() => {
  console.log(promise); // Fulfilled 상태 출력
}, 3000);

// [[Prototype]] : Promise
// [[PromiseState]] : "fulfilled"
// [[PromiseResult]] : "안녕"
```

### 실패(Rejected)상태
- reject가 호출되면 실패 상태가 됨
- reject의 인수는 catch에서 받아 처리함

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log("안녕!");
    reject("왜 실패했는지 이유...");
  }, 2000);
});

setTimeout(() => {
  console.log(promise); // Rejected 상태 출력
}, 3000);

// [[Prototype]] : Promise
// [[PromiseState]] : "rejected"
// [[PromiseResult]] : "왜 실패했는지 이유..."
```

### then 메서드
- resolve가 실행되면 then이 호출됨
- resolve의 반환값을 then의 매개변수로 전달함

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const num = 10;

    if (typeof num === "number") {
      resolve(num + 10);
    } else {
      reject("num이 숫자가 아닙니다.");
    }
  }, 2000);
});

// then 메서드
promise.then((value) => {
  console.log(value); // 20
});
```

### catch 메서드
- reject가 실행되면 catch가 호출됨
- then 내부에서 오류가 발생한 경우

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const num = null;

    if (typeof num === "number") {
      resolve(num + 10);
    } else {
      reject("num이 숫자가 아닙니다.");
    }
  }, 2000);
});

// then 메서드
promise.catch((error) => {
  console.log(error); // num이 숫자가 아닙니다.
});

```

### Promise Chaining
- then은 항상 Promise를 반환함
- 이를 활용해 여러 비동기 작업을 순차적으로 연결 가능

```js
const promise = Promise.resolve(10);

promise
  .then((value) => {
    console.log(value);
  })
  .catch((error) => {
    console.log(error);
  });
```

### 콜백지옥 탈출
- 전형적인 콜백 지옥 구조

```js
setTimeout(() => {
  console.log(10);
  setTimeout(() => {
    console.log(20);
    setTimeout(() => {
      console.log(30);
    }, 1000);
  }, 1000);
}, 1000);
```

- Promise로 개선

```js
function add10(num) {
  const promise = new Promise((resolve, reject) => {
    setTimeout(() => {
      if (typeof num === "number") {
        resolve(num + 10);
      } else {
        reject("num이 숫자가 아닙니다.");
      }
    }, 2000);
  });
  return promise;
}

add10(0)
  .then((result) => {
    console.log(result); // 10
    return add10(result);
  })
  .then((result) => {
    console.log(result); // 20
    return add10(result);
  })
  .then((result) => {
    console.log(result); // 30
  })
  .catch((error) => {
    console.log(error);
  });
```