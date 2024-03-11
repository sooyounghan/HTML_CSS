-----
### background-color
-----
1. 요소의 배경에 색상을 지정
2. 형식
```css
background-color:#f12ab0;
```

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/2e3cabec-aac7-40ce-8eff-d0c978753439">
</div>

-----
### background-image
-----
1. 요소의 배경 이미지에 한 개, 혹은 여러 개 지정
2. 형식
```css
background-image:url("이미지경로");
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/b1fd7cf1-5af3-4487-8194-87eeb41904ac">
</div>

3. 그라데이션 지정 가능
```css
background-image:linear-gradient(to top, red, blue);
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/96c5a415-79ca-4fee-8ebc-26dfbf9ef959">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/93a1843f-bdf4-4bff-a685-bfdecef1089d">
</div>

  - 방향을 생략하면, 아래에서 위 방향으로 그라데이션 생성
  - 그라데이션 종류

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/fc282adf-eb12-491b-99b3-dc47b7109650">
</div>

  - linear-gradient : 선형 그라데이션
  - radical-gradient : 원형 그라데이션
  - conic-gradient : 콘형 그라데이션

4. 다중 이미지 삽입 및 이미지-그라데이션 삽입
   - 먼저 선언한 것이 가장 위에 표시
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/f9c9f062-8d1f-4dec-97c3-c4e86a6141cd">
</div>

-----
### background-position
-----
1. 요소의 배경 이미지의 위치를 지정
```css
background-position:center;
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/10d8a2cc-9ba0-431a-a968-5562cb8f29c9">
</div>

2. 속성 : top / bottom / left / right / center
3. 두 속성을 동시에 적으면, 두 속성 적용 (예) top right : 좌측 상단)
4. 직접적인 수치 지정도 가능
 
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/c35c7fc1-1cf9-44dd-9011-0806ef436b39">
</div>

  - 첫 번째 속성 : x축
  - 두 번째 속성 : y축

-----
### background-repeat
-----
1. 요소의 배경 이미지의 반복 여부, 반복 방향을 지정
2. 형식
```css
background-repear:no-repeat;
```
3. 기본값 : background-repeat:repeat

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/aa675dd3-7c77-43fd-a0f0-e8916a4177c4">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/0604eee2-4a69-4680-8637-3e6e5f63da35">
</div>

4. background-repeat:repeat-x / repeat-y
   - x, y축으로 반복
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/aacac26c-f22e-4a80-945a-2b8cd4767115">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/cbcf3e7f-e2ec-411c-837a-be6eb6045daf">
</div>
