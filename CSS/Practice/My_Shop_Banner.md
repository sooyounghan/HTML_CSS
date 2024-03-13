-----
### 배너 생성
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to My shop - Banner</title>
    <link rel="stylesheet" href="./banner.css">
</head>

<body>
    <div class="mainBanner">
        <h1 class="text">
            Welcome to My Shop
        </h1>
    </div>
</body>
</html>
```

```css
* {
    box-sizing:border-box;
}

html, body {
    margin:0;
    padding:0;
}

.mainBanner {
    width:100%;
    height:280px;
    background-image:url("./img/banner.jpg");
    background-size:cover;

    display:flex;
    flex-direction:row;
    justify-content:center;
    align-items:center;
}

.text {
    color:white;
    font-size:42px;
    font-weight:700;

    text-shadow:2px 2px 5px rgba(0, 0, 0, 0.3);

    animation:title_text 3s ease-in-out;
}

@keyframes title_text {
    0% {
        transform:translateY(70px);
        opacity:0;
    }

    92% {
        transform:translateY(-10px);
    }

    100% {
        transform:translateY(0);
        opacity:1;
    }
}
```

1. text-shadow(offset-x, offset-y, blur-radius, color) : 텍스트에 그림자 지정
    - offset-x, offset-y : 그림자의 위치를 지정 / 양수면 글자 오른쪽, 음수면 글자 왼쪽
    - blur-radius : 숫자가 커질 수록, 그림자가 흐릿해짐 (px 단위)
    - color : 그림자의 색 지정

2. 예시
```css
text-shadow:10px 10px 10px rgba(0, 0, 0, 0.2);
```
