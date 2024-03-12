-----
### Box Model
-----
1. 웹 브라우저에서 HTML Element를 구성할 때 각 요소가 차지하는 박스 공간을 정의한 모델
2. 모든 HTML 요소는 박스 형태로 되어있음

<div align = "center">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/8c9dbb90-b437-47bb-bbf7-51e271440c64">
</div>

  - 가장 먼저 내용(Content Box) 존재
  - 내용을 감싸는 여백(Padding Box) 존재
  - Padding Box를 감싸는 상자의 외곽선(Border Box) 존재
  - 외부 여백에 해당(Margin Box)

3. 예제
```html
<link rel="stylesheet" href="./index.css">
<div class="box1">
    DIV입니다.        
</div>
```

```css
.box1 {
    background-color:gray;
    width:400px;
    height:300px;
    
    border:2px solid red;
    padding:50px;
    margin:50px;
}
```

  - Padding Box 과 Margin Box의 기본값은 투명 (단,Padding Box는 Content Box를 감싸고 있으므로 Background-color의 영향을 받음)
  - Margin Box는 외부 여백 영역이므로 Background-color의 영향을 받지 않음
  - Border 속성 순서 : 굵기 선종류 색

4. 예제
```html
<div class="box1">
    box1입니다.
</div>

<div class="box2">
    box2 입니다.
</div>
```

```css
div {
    width:200px;
    height:200px;
    background-color:lightgray;
}

.box1 {
    padding:50px;
    border:1px solid blue;
}
```
<div align = "center">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/5deda50f-f7a5-498c-aaf0-54956998ed66">
</div>

-----
### Box-Sizing 속성
----
1. content-box : Content 영역을 기준으로 box의 size를 적용 (기본값)
2. border-box : Border 영역을 기준으로 box의 size를 적용

<div align = "center">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/fcc53be9-b76f-47c8-b001-67676cfb9e91">
</div>

3. box-sizing의 값이 content-box로 설정 : content-box를 기준으로 적용하게 됨 (따라서, content box는 400px, padding box을 포함한 border box는 500px) [중요!]

<div align = "center">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/26e1c12f-3e8e-472c-bdba-c53f4a5cfef8">
</div>

4. box-sizing 값이 border-box로 설정 : border-box를 기준으로 적용하게 됨(border box는 500px, content box는 400px) [중요!]
     - 따라서, 일반적으로 모든 box-sizing을 border-box 기준으로 설정하고 시작
```html
<div class="container">
    <div class="box1">
        box1
    </div>
    <div class="box2">
        box2
    </div>
    <div class="box3">
        box3
    </div>
</div>
```
```css
.container {
    background-color:gray;
}

.box1 {
    width:200px;
    height:200px;
    background-color:white;
    border:3px solid blue;
    box-sizing:content-box;
    padding: 50px;
}

.box2 {
    width:200px;
    height:200px;
    background-color:white;
    border:3px solid red;
    box-sizing:border-box;
    padding:50px;
}

.box3 {
    width:200px;
    height:200px;
    background-color:white;
    border:3px solid green;
    /* padding:50px */
}
```
<div align = "center">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/4a9915c6-46ba-4207-a851-19dc0ec32948">
</div>

5. box1의 경우 content-box 속성이므로 padding 적용시 50px씩 더 증가하게 됨
6. box2의 경우 border-box 속성이므로 padding 적용시 그 크기 내에서 50px의 padding 생성
