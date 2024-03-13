-----
### 예제
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>08-01-animation</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        <div class="item">
            <span>Item</span>
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
    width:100%;
    height:103px;
    border:2px solid red;

    position:relative;
}

.item {
    width:100px;
    height:100px;
    background-color:blue;

    display:flex;
    flex-direction:row;
    justify-content:center;
    align-items:center;

    animation:moveBox 2s ease-in-out infinite alternate;
    
    /* animation-name:moveBox;
    animation-duration:2s;
    animation-timing-function:ease-in-out;
    animation-iteration-count:infinite;
    animation-direction:alternate; */

    position:absolute;
}

.item span {
    color:white;
}

@keyframes moveBox {
    from {
        border-radius:0;
        left:0;
        background-color:blue;
        transform:scale(1);
    }

    to {
        border-radius:50%;
        left:calc(100% - 100px);
        background-color:green;
        transform:scale(0.75);
    }
}
```

