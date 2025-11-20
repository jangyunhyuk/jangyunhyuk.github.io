---
# ====== 기본 Front Matter ======
title: "연산자"
description: "JavaScript의 연산자 개념"
date: 2025-11-20 09:00:00 +0900
categories: [JavaScript, basics]   # 최대 2개 권장
tags: [javascript, operator, 연산자]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 연산자(operator)
- 프로그래밍에서의 다양한 연산을 위한 기호 또는 키워드

### 대입 연산자
- 변수의 값을 저장할 때 사용

```js
let var1 = 1;
```

### 산술 연산자

```js
let num1 = 3 + 2; // 더하기
let num2 = 3 - 2; // 빼기
let num3 = 3 * 2; // 곱하기
let num4 = 3 / 2; // 나누기
let num5 = 3 % 2; // 나머지
```
- 곱하기(*), 나누기(/), 모듈러(%) 연산자가 더하기(+), 빼기(-) 연산자보다 우선순위가 높다.

```js
let num6 = 1 + 2 * 10;
console.log(num6) // 21

// 우선순위가 낮은 연산을 먼저 수행시키려면 소괄호 () 사용
let num7 = (1 + 2) * 10;
console.log(num7) // 30
```

### 복합 대입 연산자
- 산술 연산자와 대입 연산자가 복합되어 있다.

```js
num8 += 20; // num8 = num8 + 20
num8 -= 20;
num8 *= 20;
num8 /= 20;
num8 %= 20;
```

### 증감 연산자
- 값을 1씩 늘리거나 1씩 줄일 때 사용

```js
let num9 = 10;
console.log(++num9); // 11 전위 연산
console.log(num9++); // 11 후위 연산

console.log(--num9); // 11 전위 연산
console.log(num9--); // 11 후위 연산
console.log(num9--); // 10 (출력 후 9가 됨)
```

### 논리 연산자

```js
let or = true || false; // 둘 중 하나라도 참이면 참
let and = true && false; // 둘 다 참이어야 참
let not = !true; // true라면 false로, false라면 true로 반전
console.log(or, and, not) // true false false
```

### 비교 연산자
- 두 개의 값을 서로 비교하는 연산자

```js
let comp1 = 1 === 2; // 일치 비교 연산자
let comp2 = 1 !== 2; // 불일치 비교 연산자
console.log(comp1, comp2) // false true
```
- ==, === 차이 (동등 비교, 일치 비교)

```js
// ==로 비교하면 값의 자료형까지 같은지는 비교가 안된다.
let comp1 = 1 == '1'; // true (동등 비교)
let comp2 = 1 === '1'; // false (일치 비교)
```

- 두 값의 대소 비교

```js
let comp1 = 1 > 2; 
let comp2 = 1 < 2; 
console.log(comp1, comp2) // false true

let comp3 = 2 >= 2;
let comp4 = 2 <= 2; 
console.log(comp3, comp4) // true true
```

## 특수한 연산자

### null 병합 연산자
- null 또는 undefined가 아닐 때의 값을 반환한다.

```js
let var1;
let var2 = 10;
let var3 = 20;

let var4 = var1 ?? var2; // var1이 undefined이므로 var2의 값(10)이 반환된다.
console.log(var4) // 10

let var5 = var2 ?? var3; // 두 값이 모두 null/undefined가 아니라면 앞의 값이 반환된다.
console.log(var5) // 10
```

### typeof 연산자
- 값의 타입을 문자열로 반환하는 기능을 하는 연산자

```js
let var7 = 1;
var7 = "hello";

let t1 = typeof var7;
console.log(t1); // string
```

### 삼항 연산자
- 항 3개를 사용하는 연산자
- 조건식을 이용해서 참, 거짓일 때 값을 다르게 반환

```js
let var8 = 10;

let res = var8 % 2 === 0 ? "짝수" : "홀수"; // var8이 2로 나눴을 때 나머지가 없으면 짝수가 반환되고, 나머지가 있으면 홀수가 반환된다.
console.log(res) // 짝수
```