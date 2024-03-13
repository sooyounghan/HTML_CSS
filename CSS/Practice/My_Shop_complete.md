-----
### HTML
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to My Shop - Card</title>
    <link rel="stylesheet" href="./my-shop.css">
</head>

<body>
    <header class="menu">
        <div class="mainBanner">
            <h1 class="text">
                Welcome to My Shop
            </h1>
        </div>
    </header>

    <div class="page">
        <div class="menu">
            <div class="container">
                <div class="sidebar">
                <ul>
                    <li class="menu1"><a href="./my-shop.html" class = "new">New Items</a></li>
                    <li class="menu2"><a href="./my-shop.html" class = "best">Best Items</a></li>
                    <li class="menu3"><a href="./my-shop.html" class = "list">상품 목록</a></li>
                    <li class="menu4"><a href="./my-shop.html" class = "usage">중고 마켓</a></li>
                </ul>
                </div>
            </div>

            <div class="sidebar_item">
                <button class="item_submit">상품 등록</button>
                <span>></span>
            </div>
        </div>
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
}

html, body {
    margin:0;
    padding:0;
}

.menu {
    width:100%;
    height:280px;
}

.menu .mainBanner {
    width:100%;
    height:100%;
    background-image:url("./img/banner.jpg");
    background-size:cover;

    display:flex;
    flex-direction:row;
    justify-content:center;
    align-items:center;
}

.menu .text {
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

.page {
    display:flex;
    flex-direction:row;
    justify-content:space-between;
    align-items:flex-start;
}

.menu {
    display:flex;
    flex-direction:column;
    justify-content:flex-start;
    align-items:flex-start
}

.container {
    margin:10px;
    display:flex;
    flex-direction:row;
    justify-content:space-between;
    align-items:flex-start;
}

.sidebar {
    background:orange;
    width:170px;
    padding:5px 15px;
    border-radius:10px;

}

.sidebar ul {
    width:100%;
    padding:5px;

}

.sidebar ul li {
    list-style:none;
    padding:10px;
}

.sidebar ul li a {
    display:inline-block;

    text-decoration:none;
    color:#ffffff;

    transition:transform 0.3s ease-in-out;
}

.sidebar ul .menu1:hover,
.sidebar ul .menu2:hover,
.sidebar ul .menu3:hover,
.sidebar ul .menu4:hover {
    background-color:rgb(252, 178, 40);
    border-radius:10px;
}

.sidebar ul .menu1:hover .new,
.sidebar ul .menu2:hover .best,
.sidebar ul .menu3:hover .list,
.sidebar ul .menu4:hover .usage {
    transform:translateX(20px);
}

.sidebar_item {
    background-color:black;
    width:170px;
    height:40px;

    display:flex;
    flex-direction:row;
    justify-content:flex-start;
    align-items:center;

    margin:0 10px;
}

.sidebar_item .item_submit {
    padding-left:20px;
    border:none;
    background-color:black;
    color:#ffffff;
}

.sidebar_item span {
    color:white;
    width:calc(100% - 90px);
}

.sidebar_item:hover {
    background-color:white;
    border:1px solid black; 
}

.sidebar_item:hover button {
    background-color:white;
    color:black;
}

.sidebar_item:hover span {
    transition:transform 1s ease-in-out;
}

.sidebar_item:hover span {
    color:black;
    transform:translateX(calc(100% - 5px)); 
}

.wrap {
    display:flex;
    flex-wrap:wrap;
    flex-direction:row;
    justify-content:space-between;
    align-items:flex-start;
    margin:5px;
}

.item {
    width:calc(25% - 7px);
    aspect-ratio:6 / 5;

    position:relative;
    overflow:hidden;
    
    border-radius:10px;
    margin-bottom:10px;
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

    transform:translateY(50px);
    opacity:0;
}

.textBox__price {
    font-size:16px;
    font-weight:400;

    transform:translateY(50px);
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
    
    transform:translateY(0px);
}

.item:hover .textBox__price {
    opacity:1;

    transform:translateY(0px);
}

.item:after,
.item .imagebox img, 
.item .textBox__name {
    transition:all 0.4s ease-in-out;
}

.item .textBox__price {
    transition:all 0.4s ease-in-out 0.15s;
}
```
