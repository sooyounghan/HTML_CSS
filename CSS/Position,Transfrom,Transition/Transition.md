-----
### Transition
-----
1. '변환', '변화'라는 뜻

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f8b890d6-8e68-4ed6-b0ed-72adbceb4f9d">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a8362081-e5b0-4461-b925-cbf6116acb73">
</div>

2. transition이 적용되지 않으면, 버튼을 클릭할 때만 변경
3. transition이 적용되면, 자연스럽게 버튼을 클릭하면 색 전환 효과가 반영

4. 요소에 다양한 움직임 가능

5. 활용 예시
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6486170e-94eb-4c59-af7e-0ac863b0e37a">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7e8b3885-e3ff-4196-8ada-3a1f72e7be8d">
</div>

  - 새 글 쓰기 버튼에 마우스를 가져가면, 자연스럽게 아래 사진처럼 색이 바뀌며, 화살표도 이동

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6486170e-94eb-4c59-af7e-0ac863b0e37a">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7e8b3885-e3ff-4196-8ada-3a1f72e7be8d">
</div>

  - item에는 자연스럽게 그 item에 마우스가 이동하면, 다음과 같은 효과 부여 가능

-----
### Transition-Property
-----
1. transition에 어떠한 속성(property)을 적용할 것인지 지정
2. 형식
```css
transition-property:color, transform;
```

-----
### transition-duration
-----
1. transition에 걸리는 시간 지정 (초 : s / 밀리초 : ms 지정 가능)
2. 예시 (0.2초 동안 transition이 발생)
```css
transition-duration:0.2s;
```

-----
### transition-timing-fuction
-----
1. transition의 속도 패턴을 지정
2. 예시
```css
transition-duration:ease-in-out;
```
3. 형식
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/69b10034-cadd-4a6a-a761-a9d30b5e8a59">
</div>

4. transition 참조 : https://codepen.io/Joogumi/full/eYMgrKO
5. ease-in-out이 가장 많이 사용

-----
### transition-delay
-----
1. transition의 요청을 받은 후, 실제 실행되기까지 기다려야하는 시간의 양 지정
2. 예시
```css
transition-delay:2s;
```

3. 여러 개의 transition 요청에 대해 순서를 지정할 때 주로 사용

-----
### transition 단축 속성
-----
1. transition:propery duration timing-fuction delay
2. 예시 : transition:red 0.4s ease-in-out 1s
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/26ed45c3-f5c8-44c6-8bdc-58f5d5fc9667">
</div>

----
### transition 예제
----
1. https://codepen.io/joogumi/full/VwXpwwq
2. https://codepen.io/joogumi/full/NWYpWPx
   - 먼저 크기 전환 후, 배경색 전환
4. https://codepen.io/joogumi/full/JjLWjoZ
   - 둘이 동시에 전환
   
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>06-05-transition</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        <button class="button1">마우스를 올리면 길어져요</button><br>    
        <button class="button2">마우스를 올리면 길어져요</button><br>
        <button class="button3">마우스를 올리면 길어져요</button>
    </div>
</body>
</html>
```

```css
* {
    box-sizing:border-box;
}

.container {
    display:flex;
    flex-direction:column;
}

.button1 {
    width: 190px;
    display: inline-block;
    background-color: #123ecf;
    border-radius: 5px;
    text-decoration: none;
    padding: 10px;
    color: #ffffff;
    transition: width 0.3s ease-in-out
}

.button1:hover {
    width: 260px;
}

.button2 {
    width: 190px;
    display: inline-block;
    background-color: #123ecf;
    border-radius: 5px;
    text-decoration: none;
    padding: 10px;
    color: #ffffff;
    transition: width 0.5s ease-in-out 0.5s,
      background-color 0.5s ease-in-out;
}

.button2:hover {
    width: 320px;
    background-color: #002398;
}

.button3 {
    width: 190px;
    display: inline-block;
    background-color: #123ecf;
    border-radius: 5px;
    text-decoration: none;
    padding: 10px;
    color: #ffffff;
    transition: all 0.3s ease-in-out;
}

.button3:hover {
    width: 260px;
    background-color: #002398;
}
```

-----
### transform 중첩 적용
-----
1. transform은 변환 함수를 중첩 적용 시키는 것이 가능
2. 예제 : 요소를 75도 회전 시키고, y축 방향으로 120px 이동하려면?

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/3c4afb27-8db8-4c63-a5c4-938f68bfa836">
</div>

  - 첫 번째로 75도 회전
  - 두 번째로 y축 방향으로 120px 요소를 중첩 적용

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/5783ca60-0aaf-4e4e-a198-b7472dc9bac7">
</div>

3. 예제 : 요소를 x축 방향으로 30도, y축 방향으로 10도 기울이고, 45도 회전하려면?
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/e0c82d3a-4c74-469e-87e7-e06e9b0d25f5">
</div>

  - 첫 번째로 x축 방향으로 30도, y축 방향으로 10도 기울임
  - 두 번째로 45도 회전

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/4791e0ae-6f20-424a-80a4-be81d62b3433">
</div>


4. 예제 : 요소를 y축 방향으로 0.75 축소, x축 방향으로 20도 기울이려면?
```css
transform:scaleY(0.75) skewX(20deg)
```
