-----
### 매개변수
-----
1. 함수의 매개변수 갯수를 넘어가는 인수 : 오류를 일으키지 않고 무시됨
```js
function add(a, b) {
  return a + b;
}

console.log(
  add(1, 3),
  add(1, 3, 5),
  add(1, 3, 5, 7)
);
```

2. 기본값 매개변수 (Default Parameter)
   - 값이 전달되지 않거나 Undefined인 경우 명명된 매개변수를 기본값으로 사용할 수 있음
   - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Default_parameters
```js
function add(a = 2, b = 4) {
  console.log(`${a} + ${b}`);
  return a + b;
}

console.log(
  add(),
  add(1),
  add(1, 3)
);
```

3. arguments
   - 함수 내에서 사용 가능한 지역 변수
   - 배열의 형태를 한 객체 (배열은 아니지만, 사실상 배열처럼 동작)
   - 함수 호출 시 전달된 모든 인수들을 배열 형태로 가짐
```js
function add(a, b){
  console.log('1. ', arguments);
  console.log('2. ', arguments[0]);
  console.log('3. ', typeof arguments);
  return a + b;
}

console.log(
  '4. ', add(1, 3, 5, 7)
);
```

```js
function add(a, b){
  for(const arg of arguments) {
    console.log(arg);
  }
}

console.log(
  add(1, 3, 5, 7);
);
```

  - for ... of가 가능한 이유 : Iterable이기 때문임
  - 화살표 함수에서는 arguments 사용 불가

```js
function getAverage() {
  let result = 0;
  for(const num of arguments) {
    result += num;
  }

  return result / arguments.length;
}

console.log(
  getAverage(1, 4, 7);
  getAverage(24, 31, 52, 80)
);
```

```js
function getAverage() {
  let result = 0, count = 0;
  for(const num of arguments) {
    if(typeof num !== 'number') continue;
    result += num;
    count++;
  }
  result result / count;
}

console.log(
  getAverage(2, '가', 8, true, 5);
}
```

```js
const add = (a, b) => a + b;
const sub = (a, b) => a - b;
const mul = (a, b) => a * b;
const div = (a, b) => a / b;

function combineArms() {
  return (x, y) => {
    let result = x;
    for(const arm of arguments){
      if(typeof arm !== 'function') continue;
      result = arm(result,y);
    }
    return result;
  }
}

const add_mul = combineArms(add, mul, 1, true);
const add_mul_sub = combineArms(add, mul, sub);
const add_mul_sub_div = combineArms(add, mul, sub, div);

const add_mul_sub_div_pow = combineArms(add, mul, sub, div, (x, y) => x ** y);
```

```js
console.log(
  add_mul(8, 3);
  add_mul_sub(8, 3);
  add_mul_sub_div(8, 3);
  add_mul_sub_div_pow(8, 3);
);
```

4. 나머지 변수 (Rest Parameters) : ... 변수그룹명
  - 특정 매개변수들 뒤에 정해지지 않은 수의 매개변수들을 받을 때
  - 마지막 인자로만 상요 가능
  - arguments와 달리 실제 배열

```js
console.log(
  '3. ',
  classInfo(3, '김민지', '영희', '철수', '보라')
); //Hoisting

function classInfo(classNo, teacher, ...children) {
  console.log('1. ', children);
  console.log('2. ', arguments);

  let childernStr = '';
  for(const child of children) {
    if(childrenStr) childrenStr += ', ';
    childrenStr += child;
  }

  return `${classNo}반의 선생님은 ${teacher}, `
    + `학생들은 $childrentStr}입니다.`
}

```js
const add = (a, b) => a + b;
const sub = (a, b) => a - b;
const mul = (a, b) => a * b;
const div = (a, b) => a / b;

function doMultiArms(x, y, ... arms) {
  let result = x;
  for(const arm of arms) {
    if(typeof arm !== 'function') continue;
    result = arm(result, y);
  }
  return result;
}

console.log(
  doMultiArms(8, 3, add, mul, 1, true);
  doMultiArms(8, 3, add, mul, sub);
  doMultiArms(8, 3, add, mul, sub, div);
  doMultiArms(8, 3, add, mul, sub, div, (x, y) => x ** y);
}
```
