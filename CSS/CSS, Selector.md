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
3. 분리된 CSS 파일 연결 : HTML 파일 & CSS 파일을 따로 만든 뒤, <link> 태그를 이용해 연결해주는 방식
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
  property : value
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
  background-color : #f9f9f9
}

h1 {
  font-size : 28px
  color : red
}

p {
  color : blue
}
```

2. id 선택자
```css
#id {
    property : value
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
  color = red;
}
```

3. class 선택자 : 여러 개의 요소에 중복 지정 가능
```css
.class {
    property : value
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
  color = red;
}
```

4. 자손 선택자
  - HTML 태그에는 부모-자식 관계 존재
```css
.parent .child {
    property : value
}
```

```html
<body>
<h1 class ="title"> 전체 제목입니다. </h1>
<div class = "box1"> <!-- 부모 요소 -->
  <h1 id = "title"> 제목입니다. </h1> <!-- 자식 요소 1-->
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
  color = yellow;
}

.box2 .text1 {
  color = green
}
```

5. 다중 선택자
```css
.class#id{ <!-- 혼용해서 사용 가능 -->
  property : value
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
  color : violet
}
```
