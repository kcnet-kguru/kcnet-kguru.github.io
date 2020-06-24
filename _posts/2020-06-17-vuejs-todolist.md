---
layout: post
title:  "[K-GURU] 나만의 TODO App 만들기 - Javascript"
author: "장상익"
comments: true
---
### K-GURU 나만의 TODO App 만들기 - Javascrtipt

안녕하세요. KGuru 첫번째 강의를 담당했던 장상익 입니다.<br/>
K-Guru 첫 강의형 스터디를 진행하면서 느꼈던 점과 스터디 내용에 대해 공유하려고 합니다.

### K-Guru 란?

지식 공유를 지향하는 스터디 그룹입니다. 첫 시작을 강의형 스터디로 하였지만, 그룹스터디, 멘토링, 세미나 등등 기술이나 업무에 관련된 지식과 경험을 공유하고, 사내에 선한 영향력을 전파하려는 그룹입니다.

저는 **항상 진화하는 개발자**를 모토로 삼고 있습니다. 항상 좋은 코드를 작성하려고 노력하고, 진화하는 어플리케이션을 설계하고, 구현하는 것에 관심이 많습니다. 제가 입사한지 얼마 되지 않아 많은 분들과 친하지는 않지만, 사내에도 저와 같은 사상을 가지셨거나 관심사가 비슷한 개발자 분들이 분명히 존재 할 거라고 생각했습니다. KGuru의 시작점은 그 개발자 분들과의 소통을 위해서 기획되고, 만들어졌습니다.

그리고 관심사에 대한 수요를 조사하여 그 기준에 맞추기 보다, 그룹이 공유할 수 있는 기술 지식에 대해 공지하고, 그 기술에 관심있는 개발자 분들을 모집하는 것으로 초점을 맞추어 강의형으로 스터디를 기획하였습니다.

회사에서는 주로 웹개발을 java로 하고 관공서 프로젝트를 많이 하기 때문에 Spring Framework과 JavaScript에 대해서는 낯설지 않을 거라 생각했고 그 첫 시작을 'Vuejs'와 'Spring Boot'로 선정하셨습니다.


### Ecmascript 6

javascript 언어는 계속해서 진화와 변화를 꾸준히 진행하고 있습니다. 브라우저에서만 작동했던 javascript 가 그 한계를 넘어서 Stand Alone Runtime 을 가질 수 있었던 Nodejs 의 릴리즈 때문입니다.

Nodejs 의 출현이후 javascript 가 급속도록 발전할 수 있는 계기가 되었고, 그 발전에 따라 타 프로그래밍언어에 비해 부족하거나 버그를 유발했던 기본 코딩스타일들에 변화를 하기 시작했습니다.

고전적인 웹 어플리케이션에서 사용하던 Ecmascript6 이전에 비해 많은것이 추가되고 바뀌기 시작했습니다.

이번 교육에서 공유한 내용은
 
 - Const, let
 - Arrow Function
 - 전개 연산자
 - Promise
 
 에 대해 스터디를 진행하였습니다. 그 외에도 많은 내용들이 존재하지만, 이번 어플리케이션 구현에 필요한 부분만 하게 되었습니다.

#### const, let
```javascript
// javascript 는 변수에 대한 정의를 var 키워드로 선언해서 사용합니다.
var val1 = 1;

//하지만 var 키워드를 사용하지 않아도 호이스팅 때문에 에러가 나지 않습니다.
val2 = 3
var val2;

//ECMAScript 6에서는 호이스팅에 대한 버그를 최소화하기 위해 const 와 let 을 사용합니다.
// 이전 버전에는 호이스팅 등의 버그를 피하기 위해 'use strict' 를 명시하여 사용하기도 했습니다.
const val3 = 3
let val4 = 4

// const 는 변하지 않는 상수를 정의할 때, let 은 const 를 사용할 때를 제외하고 사용합니다.

const val5 = 5
val5 = 6 // 에러

```

#### 화살표 함수 (arrow function)
화살표 함수는 function 표현에 비해 구문이 짧고 자신의 this, arguments, super 또는 new.target 을 바인딩 하지 않습니다. 화살표 함수는 항상 익명 입니다. 이 함수 표현은 메소드 함수가 아닌 곳에 가장 적합합니다. (출처 - https://developer.mozilla.org/  화살표 함수)

화살표 함수는 다음과 같이 표현하여 사용할 수 있습니다.

```javascript
    
(param) => { code }
param => { code }
() => { code }
(param1, param2,,,,,,,paramN) => { code }
param => ( { key: value })
(param1, param2, ...rest) => { code }
(param1, param2 = 123,,,,paramN) => { code }
([one, two] = [1,2] => one + two

```

#### spread operator (전개 구문)

```javascript

function myFunction(x, y, z) {}
var args = [0, 1, 2]
myFunction(...args)

// 배열 리터럴에서의 전개
var parts = ['shoulders', 'knees']; 
var lyrics = ['head', ...parts, 'and', 'toes']; 
// ["head", "shoulders", "knees", "and", "toes"]

```

#### Promise

Promise 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값을 나타냅니다.
javascript 는 비동기로 동작하기 때문때 동기적으로 제어 하기 위해서 Promise 객체를 사용합니다.

```javascript
function first() {
    console.log("do first function");
}

function second() {
    setTimeout(() => {
        console.log("do second function");
    }, 3000);
}

function third() {
    console.log("do third function");
}

first();
second();
third();
// 결과 do first function -> do third function -> do second function 순으로 console 에 print 됩니다.

function promiseFirst() {
    return new Promise((resolve, reject) => {
        console.log("do promiseFirst function");
        resolve();
    } )
}

function promiseSecond() {
    return new Promise(((resolve, reject) => {
        setTimeout(() => {
            console.log("do promiseSecond function");
            resolve();
        }, 3000);
    }))
}

function promiseThird() {
    return new Promise((resolve, reject) => {
        console.log("do promiseThird function");
        resolve();
    } );
}

promiseFirst()
    .then(promiseSecond)
    .then(promiseThird);

// 결과 do promiseFirst function -> 3초 후 do promiseSecond function -> do promiseThird function 순으로 console 에 print 됩니다.

```