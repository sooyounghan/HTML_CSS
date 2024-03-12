-----
### html
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to My Shop - Card</title>
    <link rel="stylesheet" href="./card.css">
</head>

<body>
    <div class="wrap">
        <div class="item">
            <div class="imagebox">
                <img src="./img/item1.jpeg" alt="탁상용 조명">
            </div>
            <div class="textbox">
                <p class="textBox__name">탁상용 조명</p>
                <p class="textBox__price">260,000원</p>
            </div>
        </div>

        <div class="item">
            <div class="imagebox">
                <img src="./img/item2.png" alt="머그컵">
            </div>
            <div class="textbox">
                <p class="textBox__name">머그컵</p>
                <p class="textBox__price">32,000원</p>
            </div>
        </div>

        <div class="item">
            <div class="imagebox">
                <img src="./img/item3.jpeg" alt="거실용 슬리퍼">
            </div>
            <div class="textbox">
                <p class="textBox__name">거실용 슬리퍼</p>
                <p class="textBox__price">28,000원</p>
            </div>
        </div>

        <div class="item">
            <div class="imagebox">
                <img src="./img/item1.jpeg" alt="탁상용 조명">
            </div>
            <div class="textbox">
                <p class="textBox__name">탁상용 조명</p>
                <p class="textBox__price">260,000원</p>
            </div>
        </div>
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

.wrap {
    display:flex;
    flex-direction:row;
    justify-content:space-between;
    align-items:flex-start;
}

.item {
    width:calc(25% - 7px);
    aspect-ratio:6 / 5;

    position:relative;
    overflow:hidden;

    border-radius:10px;
}

.imagebox {
    width:100%;
    height:100%;

    z-index:1;
}

.imagebox img {
    width:100%;
    height:100%;

    object-fit:cover;
}

.textbox {
    width:100%;
    height:100%;

    position:absolute;
    top:0;
    left:0;
    
    display:flex;
    flex-direction:column;
    justify-content:flex-end;
    align-items:flex-start;

    padding:20px;

    z-index:3;
}

.textbox p {
    color:white;
    margin:5px 0 0;
}

.textBox__name {
    font-size:20px;
    font-weight:500;

    opacity:0;
}

.textBox__price {
    font-size:16px;
    font-weight:400;

    opacity:0;
}

.item:after {
    content:"";
    display:block;
    width:100%;
    height:100%;
    background:rgba(0, 0, 0, 0.2);

    position:absolute;
    top:0;
    left:0;

    z-index:2;
    opacity:0;
}

.item:hover:after {
    opacity:1;
}

.item:hover .imagebox img {
    transform:scale(1.1);
    filter:blur(3px);
}

.item:hover .textBox__name {
    opacity:1;
}

.item:hover .textBox__price {
    opacity:1;
}

.item:after,
.item .imagebox img,
.item .textBox__name,
.item .textBox__price {
    transition:all 0.4s ease-in-out;
}
```

1. blur() : 주어진 이미지에 가우시안 블러를 적용
   - 비율(숫자), 상대단위, 절대단위 모두 가능 / 0은 입력 결과 그대로 반환
2. aspect-ratio(width / height) : 요소를 비율대로 조정 [종횡비]
   - 요소의 너비가 100px이라면  
   - aspect-ratio:3 / 1 (100px, 33.33333px) [즉, 너비는 3, 높이는 1의 비율]
   - aspect-ratio:4; (너비는 4, 높이는 1의 비율을 가짐, 즉 하나의 값만 지정하면 높이는 1로 간주)
   - aspect-ratio:auto;
   - aspect-ratio:auto 1 / 1; (두 개의 값 지정, 고유한 종횡비를 가지면 해당 종횡비를 따르지만, 그렇지 않으면 지정한 종횡비)

             예를 들어, div에는 고유한 종횡비가 없으므로 1/1 종횡비를 따름
             하지만, img 요소의 경우 이미지 자체에 대한 종횡비가 있어 auto가 적용
             단, img 요소에서 auto를 제거하면 1/1의 종횡비를 따르게 됨
