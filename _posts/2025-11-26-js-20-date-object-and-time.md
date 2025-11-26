---
# ====== 기본 Front Matter ======
title: "Date 객체와 날짜"
description: "JavaScript Date 객체와 날짜 정리"
date: 2025-11-26 10:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, date, time]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## Date 객체 생성
- 생성자: new 키워드를 사용하여 Date 객체를 생성

```js
let date1 = new Date(); // 생성자
console.log(date1); // Wed Nov 26 2025 10:36:31 GMT+0900 (한국 표준시) 현재 시간
```

- 날짜 문자열을 넣어서 생성 가능
- 날짜 구분자는 “-” 또는 “/” 를 사용할 수 있지만 한 문장 내에서 섞으면 안됨

```js
let date2 = new Date("1998-03-18 10:10:10"); // 생성자
console.log(date2); // Wed Mar 18 1998 10:10:10 GMT+0900 (한국 표준시)
```

## 타임 스탬프
- "기준 시간(UTC)"으로부터 몇 ms가 지났는지를 나타내는 숫자값
- UTC(협정 세계시): 전 세계가 공통으로 사용하는 표준 시간 기준

```js
let date2 = new Date("1998-03-18 10:10:10");

let ts1 = date2.getTime();
console.log(ts1); // 890183410000
```

- 동일한 시간을 타임스탬프로 다시 Date 객체로 복구 가능

```js
let date2 = new Date("1998-03-18 10:10:10");
let ts1 = date2.getTime();
let date4 = new Date(ts1);

console.log(ts1); // 890183410000
console.log(date4); // Wed Mar 18 1998 10:10:10 GMT+0900 (한국 표준시)
```

## 시간 요소 추출
- 월(month)은 0부터 시작하므로 +1 필요

```js
let date2 = new Date("1998-03-18 10:10:10");

let year = date2.getFullYear();
let month = date2.getMonth() + 1;
let date = date2.getDate();
let hour = date2.getHours();
let minute = date2.getMinutes();
let seconds = date2.getSeconds();

console.log(year, month, date, hour, minute, seconds); // 1998 3 18 10 10 10
```

## 시간 수정
- set 메서드로 날짜 및 시간을 변경 가능

```js
let date2 = new Date("1998-03-18 10:10:10");

date2.setFullYear(2025);
date2.setMonth(10);
date2.setDate(26);
date2.setHours(10);
date2.setMinutes(30);
date2.setSeconds(30);

console.log(date2); // Wed Nov 26 2025 10:30:30 GMT+0900 (한국 표준시)
```

## 시간을 여러 포맷으로 출력

```js
let date2 = new Date("1998-03-18 10:10:10");

console.log(date2.toDateString()); // Wed Mar 18 1998
console.log(date2.toLocaleString()); // 1998. 3. 18. 오전 10:10:10
```