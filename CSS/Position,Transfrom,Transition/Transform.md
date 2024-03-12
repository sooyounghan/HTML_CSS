-----
### Transform
-----
1. '변형시킨다'는 의미
2. 요소에 이동, 회전, 확대 및 축소, 비틀기 등의 변형 효과를 줄 수 있음
3. transform의 속성값

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/00ab1b22-b0da-43a1-a926-3f1c9b9cfa24">
</div>

-----
### translate(x, y)
-----
1. 요소의 좌표를 움직일 수 있음
2. X축으로 x만큼, Y축으로 y만큼 이동
3. 예시 (X축으로 20px 이동, Y축으로 설정된 부모 요소 비율에 25% 이동)
```css
translate:translate(20px, 25%);
```

4. 양수, 음수 값 모두 가능
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/d325f365-fa74-4d79-a377-baa9ad9726ca">
</div>

5. 하나의 값만 입력하면, X축/Y축 모두 같이 이동

-----
### translateX(n) / translateY(n)
-----
1. translateX(n) : 요소의 X축 좌표를 n만큼 이동
2. 예시 (X축으로 20px으로 이동)
```css
translate:translateX(20px)
```

3. translateY(n) : 요소의 Y축 좌표를 n만큼 이동
4. 예시 (Y축으로 20px으로 이동)
```css
transform:translateY(20px)
```

-----
### scale(x, y)
-----
1. X축으로 x만큼, Y축으로 y만큼 요소를 축소 혹은 확대
2. 예시 (x축 방향으로 0.75배만큼 축소, y축 방향으로 1.1배만큼 확대)
```css
transform:scale(0.75, 1.1);
```

3. 배수로 측정되어, 1을 기준으로 기준 요소의 몇 배 축소/확대를 의미
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/06eb35a3-48b6-4363-ba84-e556ec51b598">
</div>

4. 하나의 값만 입력하면, X축/Y축 모두 같이 이동

-----
### scaleX(n), scaleY(n)
-----
1. scaleX(n) : 요소를 X축 방향으로 n만큼 축소 혹은 확대
2. 예시 (X축 방향으로 1.1배만큼 확대)
```css
transform:scaleX(1.1);
```

1. scaleY(n) : 요소를 Y축 방향으로 n만큼 축소 혹은 확대
2. 예시 (Y축 방향으로 0.75배만큼 축소)
```css
transform:scaleY(0.75);
```

-----
### skew(x, y)
-----
1. X축으로 x도 만큼, Y축으로 y도 만큼 요소를 기울임 (단위 : degree)
2. 예시 (x축으로 15도 만큼, y축으로 10도 만큼 기울임)
```css
transform:skew(15deg, 10deg);
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/2aff2fe0-b2ce-4057-9c3b-f1b7537959ad">
</div>

-----
### skewX(x), skewY(y)
-----
1. 요소를 X축으로 x도 만큼 기울임
2. 예시 (X축으로 15도 만큼 기울임)
```css
transform:skewX(15deg);
```

3. 요소를 Y축으로 y도 만큼 기울임
4. 예시 (Y축으로 10도 만큼 기울임)
```css
transform:skewY(10deg);
```

-----
### rotate(n)
-----
1. 요소를 n만큼 시계방향으로 회전시킴
2. 예시 (45도 만큼 시계방향으로 회전)
```css
transform:rotate(45deg);
```

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/3a5f4e62-cf57-432d-884a-be4fc0663a89">
</div>

3. 음수 값을 주면, 시계 반대방향으로 회전

-----
### transform 예제
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>07-01-transform</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        <div class="base"></div>
        <div class="target target1">
            <span>translate</span>
        </div>
    </div>

    <div class="container">
        <div class="base"></div>
        <div class="target target2">
            <span>scale</span>
        </div>
    </div>

    <div class="container">
        <div class="base"></div>
        <div class="target target3">
            <span>skew</span>
        </div>
    </div>

    <div class="container">
        <div class="base"></div>
        <div class="target target4">
            <span>rotate</span>
        </div>
    </div>
</body>
</html>
```
```css
* {
    box-sizing:border-box;
}

.container {
    width:500px;
    height:320px;
    position:relative;
}

.base {
    width:200px;
    height:200px;
    border:2px dashed #aaaaaa;
    border-radius:10px;
    background-color:#dddddd;
}

.target {
    width:200px;
    height:200px;
    background-color:rgba(0, 0, 255, 0.8);
    position:absolute;
    top:0;
    left:0;
    border:2px solid blue;
    border-radius:10px;

    display:flex;
    flex-direction:row;
    justify-content:center;
    align-items:center;
}

span {
    color:#ffffff;
}

.target1 {
    transform:translate(50%, 20px);
}

.target2 {
    transform:scale(0.8, 1.2);
}

.target3 {
    transform:skew(30deg, 20deg);
}

.target4 {
    transform:rotate(45deg);
}
```
<div align = "center">
<img width="234" alt="20240312_162414" src="https://github.com/sooyounghan/DataBase/assets/34672301/b13639bd-42a6-4bca-89b7-c4b0968a93a7">
<img width="222" alt="20240312_162422" src="https://github.com/sooyounghan/DataBase/assets/34672301/1ccaa5c1-bd12-47b8-9980-2163206a9c78">
</div>
