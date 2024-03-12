-----
### 예제
-----
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>07-03-transition-transform</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="box">
        <span id="text1">T</span>
        <span id="text2">R</span>
        <span id="text3">A</span>
        <span id="text4">N</span>
        <span id="text5">S</span>
        <span id="text6">F</span>
        <span id="text7">O</span>
        <span id="text8">R</span>
        <span id="text9">M</span>
    </div>
</body>
</html>
```
```css
* {
    box-sizing:border-box;
}

.box {
    width:600px;
    height:120px;
    background-image:linear-gradient(to top, orange, red);

    display:flex;
    flex-direction:row;
    justify-content:center;
    align-items:center;
}

.box span {
    font-size:36px;
    color:white;
    font-weight:600;
}

.box:hover span{
    transform:translateY(-20px);
}

.box #text1 {
    transition:transform 0.4s ease-in-out 0.1s;
}

.box #text2 {
    transition:transform 0.4s ease-in-out 0.2s;
}

.box #text3 {
    transition:transform 0.4s ease-in-out 0.3s;
}

.box #text4 {
    transition:transform 0.4s ease-in-out 0.4s;
}

.box #text5 {
    transition:transform 0.4s ease-in-out 0.5s;
}

.box #text6 {
    transition:transform 0.4s ease-in-out 0.6s;
}

.box #text7 {
    transition:transform 0.4s ease-in-out 0.7s;
}

.box #text8 {
    transition:transform 0.4s ease-in-out 0.8s;
}

.box #text9 {
    transition:transform 0.4s ease-in-out 0.9s;
}
```
