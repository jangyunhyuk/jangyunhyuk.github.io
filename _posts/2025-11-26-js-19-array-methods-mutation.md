---
# ====== 기본 Front Matter ======
title: "배열 메서드(배열 변형)"
description: "JavaScript 배열 메서드(배열 변형) 정리 - filter, map, sort, toSorted, join"
date: 2025-11-26 08:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, array, mutation]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## filter
- 기존 배열에서 조건을 만족하는 요소들만 필터링하여 새로운 배열로 반환
- 원본 배열은 변경되지 않음(비변형 메서드)

```js
let arr1 = [
  { name: "장윤혁", hobby: "운동" },
  { name: "장길동", hobby: "운동" },
  { name: "홍길동", hobby: "독서" },
];

const sport = arr1.filter((item) => item.hobby === "운동");
console.log(sport);

```

## map
- 모든 요소를 순회하며 콜백 함수 결과값들로 새로운 배열을 생성
- 원본 배열은 변경되지 않음(비변형 메서드)

```js
let arr2 = [1, 2, 3];
const mapResult1 = arr2.map((item, idx, arr) => {
  return item * 2;
});
console.log(mapResult1); // [2, 4, 6]
```

## sort
- 원본 배열을 정렬하는 메서드(변형 메서드)
- 기본 정렬은 문자열 기준(유니코드 순)

```js
let arr3 = ["b", "c", "a"];
arr3.sort();

console.log(arr3); // ["a", "b", "c"]
```

- 숫자 정렬 시 compare 함수 필요
- return 값은 “비교 결과 신호”로 해석됨
    - 음수 → a가 앞
    - 0 → 그대로
    - 양수 → a가 뒤

```js
let arr3 = [10, 3, 5];
arr3.sort((a, b) => {
  if (a > b) {
    // a가 뒤로 가야 함 (b가 앞)
    return 1; // swap 발생
  } else if (a < b) {
    // a가 앞으로 가야 함
    return -1; // swap 없음
  } else {
    // 두 값의 순서를 그대로 유지
    return 0;
  }
});

console.log(arr3); // [3, 5, 10]
```

## toSorted
- 정렬된 새로운 배열을 반환하는 메서드(비변형 메서드)
- 원본 배열은 유지됨

```js
let arr5 = ["b", "c", "a"];
const sorted = arr5.toSorted();

console.log(arr5); // ["b", "c", "a"]
console.log(sorted); // ["a", "b", "c"]
```

## join
- 배열의 모든 요소를 하나의 문자열로 합쳐 반환하는 메서드
- 기본 구분자는 쉼표(",")

```js
let arr6 = ["hi", "im", "장윤혁"];
const joined = arr6.join();

console.log(joined); // hi,im,장윤혁
```

- 구분자 변경 가능("-", "\|", "", 등)

```js
let arr6 = ["hi", "im", "장윤혁"];
const joined = arr6.join("-");

console.log(joined); // hi-im-장윤혁
```