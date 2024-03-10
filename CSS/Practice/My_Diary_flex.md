-----
### HTML
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>나만의 일기장</title>
    <link rel="stylesheet" href="./index.css">
</head>
<body>
    <header class="header">
        <div class="header-inner">
            <div class="logo">
                <h1><a href="#none">HAGD</a></h1>
            </div>
            <div class="menu">
                <ul class="menu__ul">
                    <li>
                        <a href="#none">어제의 일기</a>
                    </li>
                    <li>
                        <a href="#none">오늘의 일기</a>
                    </li>
                    <li>
                        <a href="#none">내일의 일기</a>
                    </li>
                </ul>
            </div>
            <div class="user">
                <img src="./img/portrait.png" alt="유저 정보", width = "32", height = "32">
            </div>
        </div>
    </header>

    <div class="container">
        <div class="wrapper">
            <div class="wrapper__head">
                <div class="wrapper__head__title">
                    나만의 일기장
                </div>
                <p class="wrapper__head__sub-title">
                    나만의 일기장입니다!<br/>
                    원하는 색과 사이즈로 일기장을 커스텀해봅시다!<br/>
                    <span id="point">
                        Have a Good Day!!👀.
                    </span>
                </p>
            </div>
            <div class="wrapper__body">
                <div class="wrppper__body__content">
                    <p class="diary-title">
                        🎈 나의 일기
                    </p>
                    <p>
                        오늘은 <span class="kimchi">김치찜</span>을 먹었다. <span class="egg">계란말이</span>도 함께 있는 있는 세트이다.<br/>
                        맛있어서 정신없이 먹었다 먹다 보니 배가 너무 불러서 힘들었다.<br/>
                        내일은 <span class="highlight">과식하지 말아야겠다!!</span>
                    </p>
                    <p class="diary-date">
                        오늘은 2024년 3월 5일<br/>
                         
                        날씨 : 흐림 ✌
                    </p>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

-----
### CSS
-----
```css
* {
    box-sizing:border-box;
    margin:0;
    padding:0;
    
}

.container {
    background-color:#EEEEEE;
    padding:50px 0;

    display:flex;
    flex-direction:row;
    justify-content:center;
    align-items:center;
}

.wrapper {
    background-color:white;
    border:3px solid gray;

    width:620px;
    padding:40px 30px;

    border-radius:10px;
}

.wrapper__head {
    padding:20px;
    margin-bottom:20px;
    border-bottom:1px dashed gray;
}

.wrapper__head__title {
    background-color: orange;

    font-weight:600;
    font-size:35px;
    text-align:center;
    color:white;

    padding:5px;
    margin-bottom:10px;
}

.wrapper__head__sub-title {
    font-size:18px;
    font-weight:600;

    padding:10px 0;
}

.wrapper__head__sub-title #point {
    color:orange;
    text-decoration:underline;
    font-weight:bold;

    display:block;
    margin-top:15px;
}

.wrapper__body {
    border:1px solid #DDDDDD;

    padding:20px 30px;
}

.diary-title {
    background-color:#f4f4f4;

    font-size:18px;
    font-weight:700;

    margin-bottom:20px;
}

.kimchi {
    color:red;
    font-weight:600;
}

.egg {
    color:orange;
    font-weight:600;
}

.highlight {
    color:blue;
    font-size:18px;
    font-weight:700;
    font-style:italic;
}

.diary-date {
    color:#919191;
    font-size:14px;
    text-align:right;
}


.header{
    height:80px;
    display:flex;

    justify-content:center;
    align-items:center;

    border-bottom:1px solid grey;
}

.header-inner {
    width:900px;
    height:100%;

    display:flex;
    flex-direction:row;
    justify-content:space-between;
    align-items:center;
}

.logo {
    width:100px;
}

.logo h1 a {
    text-decoration:none;
    color:orange;
}

.menu__ul {
    display:flex;
    flex-direction:row;
}

.menu__ul li {
    list-style:none;
}

.menu__ul li a {
    display:block;
    padding:10px 20px;

    font-weight:600;
    text-decoration:none;
    color:black;
}

.user {
    width: 100px;
}
```

1. 항상 flex-item이 자식 요소, flex-container가 부모 요소이므로 이들의 관계를 생각하며, flex 지정

2. flex-direction : row가 기본값이지만, 추후 의사소통을 위해 기본값들이라도 명시하자
```css
.menu__ul {
    display:flex;
    flex-direction:row;
}
```

3. a 태그는 Inline 요소이기 때문에, Block 요소로 전환시켜야하며, 메뉴 구성에 관해서는 일정한 Padding이 존재해야 추후 Labeling 작업이 원활
```css
.menu__ul li a {
    display:block;
    padding:10px 20px;

    text-decoration:none;
    color:black;
}
```

<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/26499052-9d2e-4ca9-ab35-f0e7b38f43d9">
</div>
