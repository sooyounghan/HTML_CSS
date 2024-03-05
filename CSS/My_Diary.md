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
```

<div>
<img width="443" alt="20240305_165334" src="https://github.com/sooyounghan/Data-Structure/assets/34672301/c01ce1b3-6dd1-454f-b941-a286a168496b">
</div>

-----
### 발견사항 및 놓치고 있던 사항
-----
1. 일반적으로 웹 상에서 font-size는 16~18를 주로 사용 / 굳이 가장 큰 div에 너비/높이를 지정할 필요 없음

2. 텍스트 가운데 정렬 (text-align:center)

3. 🎈🎈🎈 주로 CSS 작업 시, 다음과 같은 작업을 먼저 초기화
```css
* {
    box-sizing:border-box;
    margin:0;
    padding:0;
}
```

  - 위 코드는 모든 CSS영역에 적용하는 사항!
  - Box-sizing의 경우, 우리가 작업하기 쉽게 border-box 기준으로 초기화
  - 웹 페이지의 기본 margin과 padding 값이 적용되어있으므로 0으로 초기화

4. 🎈🎈🎈 Padding과 Margin Box에 대해서 잘 생각할 것
  - Box-sizing의 개념과 더불어 Padding과 Margin 적용 시, 명확하게 어떻게 다를지 생각하며, 적용해야함
  - Padding/Border/Margin의 경우 다음과 같이 설정할 수 있음

        * padding을 예시로 들면
          A. padding:10px 10px (위/아래에 대해 10px의 Padding, 왼/오른쪽에 대해 10px의 Padding) 가능
          B. Padding/Border/Margin-top/bottom/left/right에 대해 네 방향에 대해 각각 적용할 수 있음

5. Border의 속성
   : Border-top/bottom/left/right에 따라, 각각 그 방향에 맞는 선을 설정할 수 있음(굵기 속성 색상)
  
