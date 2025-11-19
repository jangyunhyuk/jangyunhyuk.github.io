---
# ====== 기본 Front Matter ======
title: "형 변환"
description: "JavaScript의 형변환 개념"
date: 2025-11-19 09:00:00 +0900
categories: [JavaScript, basics]   # 최대 2개 권장
tags: [javascript, typecasting, 형변환]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 형 변환(Type Casting)
어떠한 값의 타입을 다른 타입으로 변경하는 것

### 묵시적 형 변환 (암묵적 형 변환)
- 개발자가 직접 설정하지 않아도 자바스크립트 엔진이 알아서 형 변환하는 것

```javascript
let num = 10;
let str = "20";

const result = num + str; // num에 저장된 숫자 10이 묵시적으로 string 타입으로 형 변환
console.log(result); // 1020
```

### 명시적 형 변환
- 개발자가 직접 함수 등을 이용해 형 변환하는 것

```js
// 문자열 -> 숫자
let str1 = "10";
let strToNum1 = Number(str1); // Number 함수 사용
console.log(10 + strToNum1); // 20

// 숫자 -> 문자열
let num1 = 20;
let numToStr1 = String(num1); // String 함수 사용
console.log(numToStr1 + "입니다."); // 20입니다.
```

- **parseInt**: 문자열에서 앞부분의 숫자만 읽어서 숫자로 변환할 때 사용하는 함수

```js
// 숫자가 문자보다 앞에 있어야 함
let str2 = "10개";
let strToNum2 = parseInt(str2); // 10
console.log(10 + strToNum2); // 20

let str3 = "asd10개";
let strToNum3 = parseInt(str3);
console.log(strToNum3); // NaN
```