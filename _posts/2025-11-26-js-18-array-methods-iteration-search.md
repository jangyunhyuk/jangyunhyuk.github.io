---
# ====== 기본 Front Matter ======
title: "배열 메서드(순회와 탐색)"
description: "JavaScript 배열 메서드(순회와 탐색) 정리 - forEach, includes, indexOf, findIndex, find"
date: 2025-11-26 00:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, array, iteration, search]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## forEach
- 모든 요소를 순회하면서, 각각의 요소에 특정 동작을 수행시키는 메서드
- JavaScript 엔진이 순회하면서 자동으로 item, index, array를 콜백에 전달
- return 값을 무시하며, break/continue처럼 순회를 중단할 수 없음

```js
let arr1 = [1, 2, 3];

arr1.forEach(function(item, idx, arr){
    console.log(idx, item); // 0 1
                            // 1 2
                            // 2 3 
});
```

```js
let arr1 = [1, 2, 3];
let doubledArr = [];

arr1.forEach((item) => {
    doubledArr.push(item * 2);
})

console.log(doubledArr); // [2, 4, 6]
```

## includes
- 배열에 특정 요소가 있는지 확인하는 메서드
- 결과는 true/false
- === (엄격 비교) 기준으로 판단

```js
let arr2 = [1, 2, 3];
let isInclude = arr2.includes(3);

console.log(isInclude); // true

```

### indexOf
- 특정 요소가 배열의 몇 번째 인덱스에 있는지 확인
- 찾지 못하면 -1 반환

```js
let arr3 = [1, 2, 3];
let index = arr3.indexOf(2);

console.log(index); // 1
```

### findIndex
- 모든 요소를 순회하면서 콜백 조건을 만족하는 첫 번째 요소의 인덱스를 반환
- 찾지 못하면 -1 반환

```js
let arr4 = [1, 2, 3];
const findedIndex = arr4.findIndex((item) => {
    if (item % 2 !== 0) return true;
});

console.log(findedIndex); // 0
```

### find
- 콜백 조건을 만족하는 첫 번째 요소 자체를 반환
- 찾지 못하면 undefined 반환

```js
let arr5 =[
    { name: "장윤혁" },
    { name: "홍길동" }
];

const finded = arr5.find(
    (item) => item.name === "장윤혁"
);

console.log(finded); // {name: "장윤혁"}
```