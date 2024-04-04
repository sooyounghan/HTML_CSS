-----
### 일급 객체 (First Class Object)
-----
1. https://developer.mozilla.org/ko/docs/Glossary/First-class_Function
2. 함수를 변수와 같이다루는 언어에 있는 개념
3. 자바스크립트의 함수도 일급 객체 (함수는 기본적으로 객체)
```js
function addNumbers(a, b) { return a + b; }

console.log(typeof addNumbers)
```

-----
### 일급 객체 (First Class Object) 특성
-----
1. 상수 또는 변수에 할당 가능
2. 다른 함수에 인자로 전달될 수 있음
3. 다른 함수의 결과값으로 반환될 수 있음

-----
### 할당
-----
```js
function isOddNum(number){
  console.log(
    (number % 2 ? '홀' : '짝')
    + '수입니다.'
  );

  return number % 2 ? true : false;
};

const checkIfOdd = isOddNum; // 뒤에 괄호 없음 주의

console.log(checkIfOdd(23));
```

```js
let x = 7, y = 3;

let func1 = (a, b) => a + b;
let func2 = (a, b) => a - b;

console.log(func(x, y), func(x, y));
```
```js
func1 = func2;

console.log(func(x, y), func(x, y));
```
1. 함수도 객체와 배열처럼 참조타입
2. 객체와 배열의 값으로도 할당 가능
```js
let person = {
  name : '홍길동',
  age : 30,
  married : true,
  introduce : function (formal) {
    return formal
    ? '안녕하십니까. 홍길동 대리라고 합니다.'
    : '안녕하세요, 홍길동이라고 해요.';
  }
};

console.log(person.introduce(true));
console.log(person.introduce(false));
```

```js
let arithmetics = [
  (a, b) => a + b,
  (a, b) => a - b,
  (a, b) => a * b,
  (a, b) => a / b
];

for(arm of arithmetics) {
  console.log(arm(5, 3));
}
```

3. 객체의 함수 프로퍼티 : 메서드(Method)
4. ES6부터는 메서드의 정의가 달라짐 (단축 표현 메서드만 가리킴)
5. 객체에 함수 프로퍼티를 포함할 때 기억할 것
```js
let person = {
  name : '홍길동',
  age : 30,
  married : true,
  introduce : function () {
    return `저는 ${this.name}, ${this.age} 살이고 `
    + `${this.married ? '기혼' : '미혼'}입니다.`;
  }
};

console.log(person.introduce());
```
  - 객체의 다른 프로퍼티에 접근 : this 사용
  - 객체 리터럴의 프로퍼티로는 this를 사용 : 화살표 함수에서는 권장하지 않음

-----
### 인자로 전달
-----   
1. 함수가 다른 함수를 인자로 전달받음
2. 전달받는 함수 : 고차 함수(Highter-order Function)
3. 전달되는 함수 : 콜백 함수(Callback Function)
```js
let list = [1, 2, 3, 4, 5];

function doInArray(array, func) {
  for(item of array) {
    func(item);
  }
}

doInArray(list, console.log);
```
  - console.log : console이란 객체에서 log란 키에 할당된 함수
  - doInArray : 고차 함수
  - console.log : 콜백 함수

```js
function doNTimes (func, repeat, x, y) {
  let result = x;
  for(let i = 0; i < repeat; i++) {
    result = func(result, y)
  }
  return result;
}

console.log(
  doNTimes((x, y) => x * y, 3, 5, 2),
  doNTimes((x, y) => x / y, 3, 5, 2)
);
```
  - 익명 함수(Anonymous Function) : 인자로 전달된 함수들은 변수나 상수에 할당되지 않아 이름이 없음

```js
// Calculate
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
const multiply = (a, b) => a * b;

// Evaluate
const isOdd = (number) => !!(number % 2);
const isPositive = (number) => number > 0;

function calcAndEval (calc, eval, x, y) {
  return eval(calc(x, y));
}

console.log(
  calcAndEval(add, isOdd, 5, 7);
  calcAndEval(subtract, isPostivie, 5, 7);
  calcAndEval(multiply, isOdd, 5, 7);
);
```

-----
### 결과값으로 반환
-----   
```js
function getIntroFunc(name, formal) {
  reutrn formal
  ? function() {
    console.log(`안녕하십니까, ${name}입니다.`);
  : function() {
    console.log(`안녕하세요~ ${name}이라고 해요.`);
  }
}

const hongIntro = getIntroFunc('홍길동', true);
const jeonIntro = getIntroFunc('전우차', false);

hongIntro();
jeonIntro();
```

```js
const add = (a, b) => a + b;
const sub = (a, b) => a - b;
const mul = (a, b) => a * b;
const div = (a, b) => a / b;

function comb3ArmFuncs(armFunc1, armFunc2, armFunc3) {
  return(x, y) => armFun3(armFunc2(armFunc1(x, y), y), y);
}

const add_mul_sub = comb3ArmFuncs(add, mul, sub);
const mul_add_div = comb3ArmFuncs(mul, add, div);
const div_add_mul = comb3ArmFuncs(div, add, mul);

console.log(
  add_mul_sub(10, 4),
  mul_add_div(10, 4),
  div_add_mul(10, 4)
);
```

-----
### 커링 (Currying)
-----  
1. 필요한 인자보다 적은 수의 인자를 받으면, 나머지 인자를 인자로 받는 다른 함수를 반환
```js
// 기존 코드
function addMultSub(a, b, c, d){
  return (a + b) * c - d;
}

const addMultSubt2 = (a, b, c, d) => (a + b) * c - d;

console.log(
  addMultSubt(2, 3, 4, 5),
  addMultSubt(2, 3, 4, 5)
);
```

2. 커링으로 작성된 함수
```js
function curryAddMultSubt(a) {
  return function(b) {
    return function(c) {
      return function(d) {
        return (a + b) * c - d;
      }
    }
  }
}

const curryAddMultSubt2 = a => b => c => d => (a + b) * c - d;

console.log(
  curryAddMultSubt(2)(3)(4)(5),
  curryAddMultSubt2(2)(3)(4)(5)
);

const curryAddMultSubtFrom2 = curryAddMultSub2(2);
const curryMultSubFrom5 = curryAddMultSubt(2)(3);
const currySubFrom20 = curryAddMultSubt(2)(3)(4);

console.log(curryAddMultSubtFrom2);
console.log(curryMultSubtFrom5);
console.log(currySubtFrom20);

console.log(
  curryAddMultSubtFrom2(3)(4)(5),
  curryMultSubtFrom5(4)(5),
  currySubtFrom20(5)
);
```

-----
### 참고사항
-----  
1. 하나의 함수는 한 가지 일만 하도록 설정
2. 하나의 함수가 여러 일을 수행하면, 이후 코드 수정하기 복잡해짐
3. 각자 하나의 일을 하는 여러 함수들의 조합을 사용할 것
