-----
### HTML 태그는 Inline 요소와 Block 요소로 나눠진다!
-----
-----
### Block 요소
-----
1. 블록 요소를 여러개 연속으로 쌓을 경우, 자동으로 다음 줄로 넘어감
2. 좌/우 양쪽으로 늘어나 부모 요소의 너비를 가득 채움
   - 너비와 높이를 조절하는 width, height 적용 가능
4. 예시 : div, p, ul, dl, p, h1~h6, session, article 등등

< div 태그의 예 >
<div align = "center">
<img src="https://github.com/sooyounghan/Data-Structure/assets/34672301/1526b171-ad4d-416f-adc3-96682ebad5d8">
</div>

-----
### Inline 요소
-----
1. 여러 개의 요소를 입력해도 자동으로 다음 줄로 넘어가지 않음
2. 태그에 할당된 공간 만큼 너비만 차지함
   - 따라서, Block 박스에 적용되는 속성(width, heigth)들이 미적용됨  -> display 속성 이용해 block 요소로 변환 가능
4. 예시 : a, span, img, strong, em, input, button, textarea, select 태그 등등

< span 태그의 예 >
<div align = "center">
<img src="https://github.com/sooyounghan/Data-Structure/assets/34672301/62b926ef-f256-4b7b-a9c7-597d393adf70">
</div>

-----
### display
-----
1. 강제적으로 Inline을 Block 요소로, Block 요소를 Inline으로 전환하기 위해 사용
2. display : inline | block
3. HTML5 이후 현대 웹에서는 구분하지 않음 (현재 : 시멘틱 웹)


```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./index.css">
</head>
<body>
    <div class="block-container">
        <div>div1</div>
        <div>div2</div>
        <div>div3</div>
        <div>div4</div>
    </div>
    <div class="inline-container">
        <span>span1</span>
        <span>span2</span>
        <span>span3</span>
        <span>span4</span>
    </div>
</body>
</html>
```

A. Inline / Block 요소의 차이점 : div(Block) 태그는 전체 영역 / span(Inline)은 지정된 영역
```css
.block-container {
    border:3px solid blue;
}

.inline-container {
    border:3px solid red;
}

.block-container div {
    border:3px solid green;
}

.inline-container span {
    background-color:red;
}
```
<div align = "center">
<img width="780" alt="1" src="https://github.com/sooyounghan/Data-Structure/assets/34672301/2b8d01b7-b66b-487c-ac88-314a8a0ca82e">
</div>

B. Inline / Block 요소 크기 지정 : Inline 요소는 적용 불가 / Block 요소는 적용 -> display로 강제 변환 필요
```css
.block-container {
    border:3px solid blue;
}

.inline-container {
    border:3px solid red;
}

.block-container div {
    border:3px solid green;
    width:400px;
}

.inline-container span {
    background-color:red;
    width:400px;
}
```

<div align = "center">
<img width="779" alt="2" src="https://github.com/sooyounghan/Data-Structure/assets/34672301/835fc604-1e0f-429f-bbc1-c306600f28d0">
</div>

C. display를 통한 강제 변환
```css
.block-container {
    border:3px solid blue;
}

.inline-container {
    border:3px solid red;
}

.block-container div {
    border:3px solid green;
    width:400px;
    display:inline;
}

.inline-container span {
    background-color:red;
    width:400px;
    display:block;
}
```
<div align = "center">
<img width="781" alt="3" src="https://github.com/sooyounghan/Data-Structure/assets/34672301/8c297aa9-a403-493e-a571-dae7c0f260dc">
<img width="779" alt="4" src="https://github.com/sooyounghan/Data-Structure/assets/34672301/2e761181-9a2f-4569-a4a2-093132d31ad6"></div>
