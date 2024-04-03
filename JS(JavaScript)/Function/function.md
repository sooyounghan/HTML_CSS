-----
### Function
-----
```js
function 함수명 (입력값) {
  // 수행할 문장
  return 반환값;
}

함수명(입력값)
```

1. 함수를 사용한다는 것 : 반복될 수 있는 작업을 정의해두는 것
```js
// 함수 사용 전
let a = 3, b = 4;

console.log(`${a} + ${b} = ${a + b}`);
console.log(`${a} - ${b} = ${a - b}`);
console.log(`${a} * ${b} = ${a * b}`);
console.log(`${a} / ${b} = ${a / b}`);

let c = 10, d = 2;

console.log(`${c} + ${d} = ${c + d}`);
console.log(`${c} - ${d} = ${c - d}`);
console.log(`${c} * ${d} = ${c * d}`);
console.log(`${c} / ${d} = ${c / d}`);

let e = 7, f = 5;
console.log(`${e} + ${f} = ${e + f}`);
console.log(`${e} - ${f} = ${e - f}`);
console.log(`${e} * ${f} = ${e * f}`);
console.log(`${e} / ${f} = ${e / f}`);
```

```js
function allArithmeic (x, y) {
  console.log(`${x} + ${y} = ${x + y}`);
  console.log(`${x} - ${y} = ${x - y}`);
  console.log(`${x} * ${y} = ${x  y}`);
  console.log(`${x} / ${y} = ${x / y}`);
}

let a = 3, b = 4;
allArithmetics(a, b);

let c = 10, d = 2;
allArithemic(c, d);

let e = 7, f = 5;
allArithemic(e, f);
```

2. input를 받아 output을 반환(return) 하는 것
```js
function add(x, y) {
  return x + y; // 값을 반환
}

let z = add(2, 3);

console.log(z);

console.log(add(4, 5));

console.log(add(add(6, 7), add(8, 9)))
```

```js
function isOdd(x) {
  return !!(x % 2);
}






