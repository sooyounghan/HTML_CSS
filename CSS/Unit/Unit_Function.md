-----
### Unit 관련 함수
-----
1. calc() : 괄호 안의 사칙 연산을 수행한 결과를 속성값으로 사용

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/89a12c81-6e1a-4129-aded-eca4a07519b6">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c701592a-bf5a-4a55-916d-14e211728c7c">
</div>

  - 덧셈과 뺄셈의 경우에는 앞 뒤에 공백
  - 곱셈과 나눗셈은 문제 없음

-----
### 예제
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>06-01-calc</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="box">
        <span class="text">
            20px + 50%
        </span>
        <div class="item1"></div>
    </div>
    <div class="box">
        <span class="text">
            100% - 70px
        </span>
        <div class="item2"></div>
    </div>
    <div class="box">
        <span class="text">
            3 * 20px
        </span>
        <div class="item3"></div>
    </div>
    <div class="box">
        <span class="text">
            100% / 4
        </span>
        <div class="item4"></div>
    </div>
</body>
</html>
```

```css
* {
    box-sizing:border-box;
}

.box {
    border:1px solid red;
    margin-bottom:30px;
    padding:30px;
}

.text {
    font-weight:500;
    font-size:24px;
}

.item1 {
    background:red;
    width:calc(20px + 50%);
    height:50px;
}

.item2 {
    background:green;
    width:calc(100% - 70px);
    height:50px
}

.item3 {
    background:blue;
    width:calc(3*20px);
    height:50px;
}

.item4 {
    background:yellow;
    width:calc(100%/4);
    height:50px;
}
```

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3a581074-140e-4c3b-a3d7-50ff5fd77426">
</div>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>06-02-calc2</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        <div class="sidebar">
        <ul>
            <li>메뉴1</li>
            <li>메뉴2</li>
            <li>메뉴3</li>
            <li>메뉴4</li>
        </ul>
        </div>
        <div class="contents">
            <div class="item">상품</div>
            <div class="item">상품</div>
            <div class="item">상품</div>
            <div class="item">상품</div>
            <div class="item">상품</div>
            <div class="item">상품</div>
            <div class="item">상품</div>
            <div class="item">상품</div>
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
    display:flex;
    flex-direction:row;
    justify-content:space-between;
    align-items:flex-start;
}

.sidebar {
    background:orange;
    width:170px;
    padding:5px 15px;
}

.sidebar ul {
    width:100%;
    padding:0;
}

.sidebar ul li {
    list-style:none;
    padding:5px 0;
    color:#ffffff;
    border-bottom:1px dashed rgb(255, 255, 255, 0.3);
}

.contents {
    width:calc(100% - 170px);
    display:flex;
    flex-wrap:wrap;
    justify-content:space-between;
    align-content:flex-start;
    padding:0 10px;
}

.item {
    width:24%;
    height:140px;

    margin-bottom:10px;
    background-image:url("./img/dochi.png");
    background-size:cover;
}
```

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ab9f85fe-08c1-4d1f-acbd-9deae8a4cca6"
</div>
