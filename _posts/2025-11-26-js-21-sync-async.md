---
# ====== 기본 Front Matter ======
title: "동기와 비동기"
description: "JavaScript 동기와 비동기 정리"
date: 2025-11-26 13:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, sync, async, 동기, 비동기]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## 동기
- 여러 작업을 순서대로, 하나씩 처리하는 방식
- 이전 작업이 끝나야 다음 작업이 실행됨
- 자바스크립트는 기본적으로 “단일 스레드”에서 동기적으로 실행됨
- 단점: 하나의 작업이 오래 걸리면 전체 흐름이 멈춤(블로킹)
- 이를 보완하기 위해 비동기 기술을 사용함

```js
// 동기 방식
console.log(1); // 1
console.log(2); // 2
console.log(3); // 3

// 출력
// 1
// 2
// 3
```

## 비동기
- 시간이 오래 걸리는 작업을 별도로 처리하고, 완료되면 나중에 다시 실행하는 방식
- 메인 스레드가 멈추지 않기 때문에 블로킹을 방지함
- setTimeout(), fetch(), 이벤트 리스너 등은 브라우저의 Web APIs 영역에서 실행됨
- Web APIs는 자바스크립트 엔진이 아닌 브라우저가 직접 관리하는 비동기 실행 공간

```js
console.log(1); // 1

setTimeout(()=>{
    console.log(2) // 3초 뒤 실행
}, 3000)

console.log(3); // 3

// 출력값 
// 1
// 3
// 2
```

### 비동기 동작 흐름
1.	콜스택(Call Stack) 에서 자바스크립트 코드 실행
2.	비동기 함수를 만나면 Web APIs 영역으로 보냄
3.	Web APIs에서 작업이 끝나면 Task Queue(대기열)에 콜백을 넣음
4.	이벤트 루프(Event Loop) 가 콜스택이 비었는지 계속 확인
5.	콜스택이 비면 Task Queue에서 콜백을 꺼내 실행

### 콜스택(Call Stack)
- 자바스크립트가 지금 당장 실행해야 하는 작업이 쌓이는 공간
- 한 번에 하나씩만 처리 가능

### Web APIs
- 브라우저가 제공하는 실행 영역(setTimeout, fetch, DOM 이벤트 등)
- 시간이 오래 걸리는 작업을 대신 수행

### Task Queue (Callback Queue)
- Web APIs에서 완료된 작업이 “실행 준비됨” 상태로 기다리는 큐(줄)

### 이벤트 루프(Event Loop)
- 콜스택이 비었는지 계속 감시하는 역할
- 비었으면 Task Queue에서 작업을 가져와 콜스택으로 올려 실행

### 단일 스레드(Single Thread)
- 자바스크립트 엔진은 하나의 실행 흐름만 가진다
- 동시에 여러 작업을 처리하는 구조가 아님