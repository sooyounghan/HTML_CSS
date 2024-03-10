-----
### CSS (Cascading Style Sheet)
-----
1. 웹 페이지의 스타일, 레이아웃을 담당하는 문서
2. 선택자(Selector) + 선언(Declaration)
3. 선언(Declaration) : 속성(Property) + 속성 값(Property Value)로 구성

-----
### CSS (Cascading Style Sheet) 적용 방식
-----
1. 인라인(In-Line) 방식 : 속성을 적용할 HTML 태그에 직접 CSS를 입력해주는 방식
2. <style> 태그 : < head > 내에 <style> 내 삽입이 가능 (한 파일 내에 넣어야하는 상황이면 사용)
3. 분리된 CSS 파일 연결
   
   : HTML 파일 & CSS 파일을 따로 만든 뒤, <link> 태그를 이용해 연결해주는 방식
   
   : 파일을 분리하여 보관하므로 유지보수가 편리하고 소스코드를 관리하기 좋음

             <link rel = "stylesheet" href = "./index.css">
             - rel : 해당 태그로 연결시켜줄 파일과 어떤 관계(relation)인지 지정
             - href : 연결할 파일의 경로 지정

-----
### 선택자 (Selector)
-----
1. 태그 선택자
```css
tag {
  property : value;
}
```

```html
<div>
  <h1> 제목입니다. </h1>
  <p> 내용입니다. </p>
</div>
```
```css
div {
  background-color : #f9f9f9;
}

h1 {
  font-size : 28px;
  color : red;
}

p {
  color : blue;
}
```

2. id 선택자
```css
#id {
    property : value;
}
```

```html
<body>
<div>
  <h1 id = "title"> 제목입니다. </h1>
  <p> 내용입니다. </p>
</div>
</body>
```

```css
#title {
  font-size : 28px;
  color : red;
}
```

3. class 선택자 : 여러 개의 요소에 중복 지정 가능
```css
.class {
    property : value;
}
```
```html
<body>
<div>
  <h1 id = "title"> 제목입니다. </h1>
  <p class = "contents"> 내용입니다. </p>
</div>
</body>
```

```css
.contents {
  font-size : 28px;
  color : red;
}
```

4. 자손 선택자
  - HTML 태그에는 부모-자식 관계 존재
```css
.parent .child {
    property : value;
}
```

```html
<body>
<h1 class ="title"> 전체 제목입니다. </h1>
<div class = "box1"> <!-- 부모 요소 -->
  <h1 class = "title"> 제목입니다. </h1> <!-- 자식 요소 1-->
  <p class = "contents"> 내용입니다. </p> <!-- 자식 요소 2-->
</div>
<div class = "box2">
  <p class = "text1">글 내용입니다 1.</p>
  <p class = "text2">글 내용입니다 2.</p>
</div>
</body>
```

```css
.box1 .title {
  color : yellow;
}

.box2 .text1 {
  color : green
}
```

5. 다중 선택자
```css
.class#id{ <!-- 혼용해서 사용 가능 -->
  property : value;
}
```

```html
<body>
<h1 class ="title"> 전체 제목입니다. </h1>
<div class = "box1"> <!-- 부모 요소 -->
  <h1 class = "title" id = "headline"> 제목입니다. </h1> <!-- 자식 요소 1-->
  <p class = "contents"> 내용입니다. </p> <!-- 자식 요소 2-->
</div>
<div class = "box2">
  <p class = "text1">글 내용입니다 1.</p>
  <p class = "text2">글 내용입니다 2.</p>
</div>
</body>
```

```css
.title#headline {
  color : violet;
}
```

6. 전체 선택자 : HTML 내 모든 요소를 선택하는 선택자
```css
* {
  property : value;
}
````

7. 그룹 선택자 : 원하는 선택자 여러 가지를 콤마를 통해 연결
```css
.class1, .class2 {
  proprty : value;
}
```

8. 가상 선택자 : 실제로 HTML 요소를 수정하지 않고, CSS만을 가상 요소로 추가해 선택
```css
선택자 : 가상 클래스 {
   property : value;
}
```
  - first-child : 해당 요소의 자식 중 첫 번째 자식 요소를 의미 (= 즉, 태그에 상관 없이 첫 번째 자식을 의미)
```css
.class:first-child {
  property : value;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/e94c4802-00f4-424d-ae57-d6f7d05bf5d2">
</div>

 - last-child : 해당 요소의 자식 중 마지막 자식 요소를 의미 (= 즉, 태그에 상관 없이 마지막 자식을 의미)
```css
.class:last-child {
  property : value;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/1496a142-9dae-41e8-bbae-b9b4277dceef">
</div>

 - n-th child (n) : 해당 요소의 자식 중 n번째 자식 요소 의미 (= 즉, 태그에 상관 없이 n번째 자식을 의미)
```css
.class:nth-child(n) {
  property : value;
}
```

<div align = "center">
<img  src="https://github.com/sooyounghan/DataBase/assets/34672301/7b9fecd8-362a-4b40-865a-0516c1b59678">
</div>

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/d27baad4-e1b4-41a8-80df-0af524f28edf">
</div>

  - hover : 요소 위에 마우스가 올라갔을 때 전환 효과, 이벤트가 되는 선택자
```css
.class:hover {
  property : value;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/076b59cd-68ab-49ef-9b5b-5264e8591a47">
</div>


    * 버튼 위에 마우스가 올라갔을 떄의 전환효과
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/7a48d18c-65a3-4d25-b2fc-1705834671b2">
</div>

-----
### 선택자 (Selector) : 가상 클래스 선택자
-----
< of-type 선택자 >
1. :first-of-type (of-type)
   - 형제 요소 중 첫번째 요소를 선택하는 가상 클래스
   - first-child와 다르게 가상 클래스가 적용된 선택자에 해당 되는 요소만 카운트
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3101f035-3f8d-425a-a40c-beeb96a2c7bc">
</div>

   - 즉, p태그 중에 첫 번째 p태그에 해당 요소를 적용

2. :last-of-type (of-type)
   - 형제 요소 중 마지막 요소를 선택하는 가상 클래스
   - last-child와 다르게 가상 클래스가 적용된 선택자에 해당 되는 요소만 카운트
  
3. :nth-of-type (of-type)
   - 형제 요소 중 n번째 요소를 선택하는 가상 클래스
   - nth-child와 다르게 가상 클래스가 적용된 선택자에 해당 되는 요소만 카운트
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/24bd7b53-ccd6-4caf-87e6-9193d8b9cd1b">
</div>

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>03-01-of-type-and-child</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        <h1>제목입니다.</h1>
        <p>첫 번째 p입니다.</p>
        <p>두 번째 p입니다.</p>
        <span>첫 번째 span입니다.</span>
        <p>세 번째 p입니다.</p>
    </div>
</body>
</html>
```

```css
* {
    box-sizing:border-box;
}

.container p:first-child {
    background-color:red;
}

.container p:first-of-type {
    background-color:blue;
}

.container p:last-of-type {
    background-color:yellow;
}

.container p:nth-of-type(2) {
    background-color:green;
}

.container span:first-of-type {
    font-weight:600;
    text-decoration:underline;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3dc3fa75-d769-44d9-8142-90b088dabab0">
</div>

4. :active
   - 활성화된 요소를 선택하는 가상 클래스 선택자

           활성화된 요소 : 버튼 등을 클릭해서 요소의 동작이 활성화되어 있는 상태

5. :focus
   - focus를 받고 있는 입력 창 등의 요소를 선택하는 가상 클래스 선택자
   - TAB 키 등을 이용해 입력창의 커서가 활성화되어 있는 상태
     
6. :visited
   - 사용자가 방문한 적 있는 링크를 선택하는 가상 클래스 선택자

           방문한적 있는 링크 : 링크를 눌러서 해당 경로를 방문한 기록이 브라우저상에 남아있는 링크(기본컬러 - 보라색)

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>03-02-active-focus-visited</title>
    <link rel="stylesheet" href="./index.css">
</head>
<body>
    <button class="button1">나는 버튼입니다!</button>
    <input type="text" class="input1">
    <a href="http://www.google.com" class = "link1">나는 링크입니다!</a>
</body>
</html>
```

```css
.button1:active {
    background-color:red;
}

.input1:focus {
    background-color:green;
}

.link1:visited {
    color:red;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/546ca71e-b8be-4537-8963-b5f59261aa11">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b922cd0f-cd93-4efd-b6d6-e3a7a265c60e">
<img  src="https://github.com/sooyounghan/Web/assets/34672301/635fbbf1-0479-4a04-ac34-ae9932ca5fa7">
</div>

-----
### 선택자 (Selector) : 가상 요소 선택자
-----
1. 실제로 HTML 요소를 수정하지 않고, CSS만으로 가상 요소를 추가해 선택할 수 있음
2. 가상 요소를 사용하지 않은 예시
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ee75754e-256b-4102-a25d-becd27d9d90f">
<img src="https://github.com/sooyounghan/Web/assets/34672301/83832d45-f6c1-49d2-a378-11f743e09b2c">
</div>

3. :before / :after
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6e989506-16f9-4c64-b84d-64dd214fb62a">
</div>
   - 가상의 div를 :after를 통해 생성 (본질적으로 HTML에 존재하지 않으므로, 채워줘야함)
   - content를 사용하지 않더라도, content:""를 명시해야 가상 요소가 화면에 보여짐

4. clearfix를 통한 예시
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/152e1a70-d9b6-4f77-801c-ca7bae2ebead">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0db4617a-2a29-4ec0-abcf-d208343f42c6">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0dab8867-8c37-4dda-b86a-2ccd5460002a">
<img src="https://github.com/sooyounghan/Web/assets/34672301/32e9365a-1345-4073-a1e7-3fdcb223c7b7">
</div>

   - 가상 요소 선택자를 이용해 더 깔끔한 clearfix를 적용하는 방법
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/fc8ee261-2881-4c27-b165-e96a7b699c59">
<img src="https://github.com/sooyounghan/Web/assets/34672301/043a46db-13b8-4cf7-948b-a2da7f3f0e36">
</div>

   - 그러나 이 때, 반드시 가상 선택자인 clearfix:after에 반드시 content:""라도 부여해야 화면에 출력됨을 주의

-----
### 선택자 (Selector) : 형제 요소 선택자
-----
```css
A ~ B {
   property : value;
}
```
: A와 같은 부모를 가지고 있는 형제 요소들 중 B를 선택
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/57f6f60e-bc17-438c-87dc-461b30a2cee2">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b7c2ea91-d8c9-45be-a644-740dbef4e741">
</div>

-----
### CSS Diner : CSS 선택자 연습 게임
-----
참조 : https://flukeout.github.io/
