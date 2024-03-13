-----
### 반응형 웹
-----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cebfae5b-18a1-4cfd-a644-90f35771e6e0">
</div>

1. 모든 기기에서 동일한 레이아웃이 노출되면, 레이아웃이 맞지 않는 문제 충돌
2. PC/Mobile 웹 : 스마트폰과 데스크탑 PC 각각 URL를 구성, 즉 각각의 UI 구성 (옛날 방식)
3. 반응형 웹 : 어떤 기기로 접속하더라도 URL이 동일하며, 기기의 형태 및 사이즈에 따라 서로 다른 레이아웃 표시

-----
### 미디어 쿼리
-----
1. Viewport의 너비에 따라 웹 사이트의 스타일 시트를 수정할 수 있음
2. Viewport 너비 이외에도 단말기 종류, 해상도 등 기준으로 설정 가능

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ccc7b5dd-3095-476a-8f59-a7736c2fb99b">
</div>

  - @media : 미디어 쿼리
  - screen : 미디어 타입 (조건1)
  - max-width:500px : 조건2

        min-width와 max-width를 연결해 최소, 최대 크기로 설정 가능
        - max-width:값 (max-width가 지정한 값 이하면 적용)
        - min-wdith:값 (min-width가 지정한 값 이상이면 적용)

-----
### 예제
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>10-01-media-query</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="box">
        박스입니다.
    </div>

    <div class="container">
        <div class="box1">
            박스1
        </div>
        <div class="box2">
            박스2
        </div>
    </div>
</body>
</html>
```

```css
* {
    box-sizing:border-box;
}

.box {
    height:200px;
    background-color:blue;
    color:white;
    padding:30px;
}

@media screen and (max-width:600px) {
    .box {
        background-color:red;
    }
}

.container {
    display:flex;
    flex-direction:row;
}

.box1 {
    background-color:green;
    color:white;
    width:20%;
    padding:30px;
}

.box2 {
    background-color:orange;
    width:80%;
    padding:30px;
}

@media screen and (min-width:601px) {
    .container {
        flex-direction:column;
    }

    .box1 {
        width:100%;
    }

    .box2 {
        width:100%;
    }
}
```

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8a33e7a3-c64a-40d1-a741-29e43c81866d">
<img src="https://github.com/sooyounghan/Web/assets/34672301/67014efd-c8c2-47cb-b6ce-f183b73f58dc">
</div>

  - 화면이 600px이하이면, 위 같이 적용
  - 화면이 601px이상이면, 아래 같이 적용

