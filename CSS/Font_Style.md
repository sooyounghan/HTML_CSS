-----
### font-size : 글자 사이즈
-----

-----
### font-weight : 글자 두께
-----

-----
### font-style : 글자 기울임
-----

-----
### text-decoration : 글자 꾸밈 (밑줄, 취소선 등)
-----

-----
### color : 글자 색 (font, text 접두어가 붙지 않음)
-----

<예제>
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>01-01-css</title>
    <link rel="stylesheet" href="./index.css">
</head>
<body>
    <h1 class = "title">전체 제목</h1>
        <div class ="box1">
        <h1 class="title" id="headline">제목입니다.</h1>
        <p class="contents">내용입니다.</p>
    </div>
</body>
</html>
```

```css
.title {
    color : red
}

.box1 .title {
    color : yellow;
}

.contents {
    font-size : 28px;
    font-style : italic;
    text-decoration: underline;
    font-weight: 600;
}

.title#headline {
    color : violet;
}
```
