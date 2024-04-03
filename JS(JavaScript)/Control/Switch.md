-----
### Switch문 (Switch ~ case)
-----
1. 주어진 평가에 일치하는 case로 실행 위치 이동
```js
const fingersOut = 2;

switch (fingersOut) {
  // 순서는 상관 없음
  case 2 :
    console.log('가위');
    break;
  case 0 :
    console.log('바위');
    break;
  case 5 :
    console.log('보');
    break;
  default :
    console.log('무효');
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/26f8bf5f-db94-4c2c-87e1-5008907d0925">
</div>

  - swtich(값) : case 값 (값에 매칭되는 case 진입)
  - break; 들을 제거하고 실행하면 ? break가 없으면 모든 문장 수행
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1c19d938-3197-47ba-a37a-26eeea2a4659">
</div>

2. default : 맨 아래 작성, break 되지 않는 이상 무조건 실행

```js
const direction = 'north'
let directionKor;

switch (direction) {
  case 'north':
    directionKor = '북';
    break;
  case 'south':
    directionKor = '남';
    break;
  case 'east':
    directionKor = '동';
    break;
  case 'west':
    directionKor = '서';
    break;
  default:
    directionKor = '무효';
}

console.log(directionKor);
```
  - break; 들을 제거하고 실행하면 ?

```js
// 참고 : 객체를 사용한 방법
const direction = 'north';

const directionKor = {
  north : '북',
  south : '남',
  east : '동',
  west : '서'
}[direction] ?? '무효' // 객체에 없는 키 값, 즉 direction이 없는 키 값이면, undefined이므로 '무효'

console.log(directionKor);
```

```js
const month = 1;
let season = '';

switch  (month) {
  case 1: case 2: case 3:
    season = '1분기'; break;

  case 4: case 5: case 6:
    season = '2분기'; break;

  case 7: case 8: case 9:
    season = '3분기'; break;

  case 10: case 11: case 12:
    season = '4분기'; break;

  default:
    season = '잘못된 월입니다.';
}

console.log(season);
```

```js
const startMonth = 1;
let holidays = '분기 내 휴일:';

switch (startMonth) {
  case 1:
    holidays += ' 설날';
  case 2:
  case 3:
    holidays += ' 3•1절';
    break;

  case 4:
  case 5:
    holidays += ' 어린이날';
  case 6:
    holidays += ' 현충일';
    break;

  case 7:
  case 8:
    holidays += ' 광복절';
  case 9:
    holidays += ' 추석';
    break;

  case 10:
    holidays += ' 한글날';
  case 11:
  case 12:
    holidays += ' 크리스마스';
    break;

  default: 
    holidays = '잘못된 월입니다.';
}

console.log(holidays);
```
