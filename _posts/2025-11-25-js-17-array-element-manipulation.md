---
# ====== 기본 Front Matter ======
title: "배열 메서드(요소 조작)"
description: "JavaScript 배열 메서드(요소 조작) 정리 - push, pop, shift, unshift, slice, concat, splice"
date: 2025-11-25 14:00:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, array, element, manipulation]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## push
- 배열의 맨 뒤에 새로운 요소를 추가하는 메서드
- 요소를 추가한 후 변환된 배열의 길이를 반환

```js
let arr1 = [1, 2, 3];
const newLength = arr1.push(4, 5, 6);

console.log(arr1); // [1, 2, 3, 4, 5, 6]
console.log(newLength) // 6
```

## pop
- 배열의 맨 뒤에 있는 요소를 제거하고, 반환

```js
let arr2 = [1, 2, 3];

const poppedItem = arr2.pop();

console.log(poppedItem); // 3
console.log(arr2); // [1, 2]
```

## shift
- 배열의 맨 앞에 있는 요소를 제거하고, 반환

```js
let arr3 = [1, 2, 3];
const shiftedItem = arr3.shift();

console.log(shiftedItem); // 1
console.log(arr3); // [2, 3]
```

## unshift
- 배열의 맨 앞에 새로운 요소를 추가하는 메서드
- 요소를 추가한 후 변환된 배열의 길이를 반환(push와 동일)

```js
let arr4 = [1, 2, 3];
const newLength2 = arr4.unshift(0);

console.log(newLength2, arr4); // 4 [0, 1, 2, 3]
```

## slice
- 배열의 특정 범위를 잘라내서 새로운 배열로 반환

```js
let arr5 = [1, 2, 3, 4, 5];
let sliced = arr5.slice(2, 5); 
let sliced2 = arr5.slice(2); // 배열의 끝까지 자를거면 두번째 인수는 생략 가능
let sliced3 = arr5.slice(-1); // 배열의 뒤에서부터 자르기

console.log(sliced); // [3, 4, 5]
console.log(sliced2); // [3, 4, 5]
console.log(sliced3); // [5]
console.log(arr5); // [1, 2, 3, 4, 5]
```

## concat
- 두개의 서로 다른 배열을 이어 붙여서 새로운 배열을 반환

```js
let arr6 = [1, 2];
let arr7 = [3, 4];

let concatedArr = arr6.concat(arr7);
console.log(concatedArr); // [1, 2, 3, 4]
```

## splice
- 배열의 특정 위치에서 요소를 삭제, 추가, 교체하는 메서드
- 원본 배열을 직접 변경
- 반환값은 삭제된 요소들의 배열

### splice 인수
- splice(startIndex, deleteCount, ...itemsToInsert) 형태로 사용

#### startIndex
- 조작을 시작할 배열의 인덱스 위치
- 삭제/추가/교체 모두 이 위치를 기준으로 수행됨

#### deleteCount
- startIndex부터 몇 개의 요소를 삭제할지 지정
- 0이면 삭제 없이 삽입만 수행

#### itemsToInsert
- 삭제된 자리 혹은 startIndex 위치에 새로 추가할 값들
- 값이 없으면 단순히 삭제만 수행
- 값이 있으면 삭제된 자리에 새 요소가 들어가며 교체가 됨

```js
let arr8 = [1, 2, 3, 4, 5];

let deleted1 = arr8.splice(1, 2); 

console.log(deleted1); // [2, 3]
console.log(arr8);     // [1, 4, 5]

arr8.splice(1, 0, 10, 20);

console.log(arr8); // [1, 10, 20, 4, 5]

arr8.splice(2, 1, 99);

console.log(arr8); // [1, 10, 99, 4, 5]
```