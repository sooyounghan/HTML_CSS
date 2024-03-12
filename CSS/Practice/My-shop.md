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
