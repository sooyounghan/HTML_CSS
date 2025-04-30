-----
### 폰트 패밀리 (Font Family)
-----
1. HTML 요소의 글씨체를 변경
2. font-family 속성 이용하며, 두 개 이상의 폰트를 적용하고자 할 때 사용
```css
font-family:"폰트 이름";
```

3. 예시
```css
body {
  font-family:"맑은 고딕", "돋움", sans-serif;
}
```

4. font-family는 앞에서부터 우선 순위를 가짐
```css
body {
  font-family:arial, "맑은 고딕", sans-serif;
}
```
  - 폰트 적용 순위 : 1순위(arial), 2순위(맑은 고딕), 3순위(sans-serif)
  - arial은 영문 폰트로, 영문에 대한 폰트를 가지고 있지만, 한글 폰트는 없으므로 ABC에만 적용
  - 맑은 고딕은 영문 / 한글 폰트이므로, 한글 폰트에 대해 다음 우선순위인 맑은 고딕 폰트 적용
  - sans-serif는 앞의 모든 폰트 파일을 찾지 못했을 때, 사용자의 컴퓨터에서 sans-serif 계열의 font를 찾아 적용 (Generic Family 설정)

        - sans-serif : 고딕체
        - serif : 바탕체
        - cursive : 필기체

5. 단, 유저 컴퓨터에도 폰트 파일이 설치되어있어야 글씨체가 제대로 보임

-----
### 웹 폰트 (Web Font)
-----
1. 웹 전용 폰트
2. 사용자가 로컬 (컴퓨터)에 폰트를 직접 설치하지 않아도, 특정 서버에 위치한 폰트를 다운받아 웹 페이지에 표시
3. 웹 폰트 적용 방법
   - 폰트 파일을 직접 다운 받아 적용 : @font-face 이용
   - 외부 서비스에서 제공하는 링크를 이용 : @import 혹은 < link > 이용
  
-----
### @font-face 이용
-----
1. 웹 폰트 파일 (확장자 : woff / woff2 / ttf / eot) 준비
2. CSS문서에서 @font-face를 이용해 폰트 파일을 불러옴
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/d064e4d4-d74a-4f84-a1c5-55020eee340d">
</div>

3. 불러온 폰트 파일을 이용해 새로운 font-family를 만듬
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/c2458449-b268-47f2-a3d0-c791d788774b">
</div>

4. 만든 font-family를 사용
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/6082300c-414d-46dc-a993-ca6dddbcc630">
</div>

-----
### @import 이용
-----
1. 구글 폰트에 접속해 원하는 폰트를 찾음
    - https://fonts.google.com/?subset=korean&noto.script=Kore
2. 폰트를 상세 페이지 접속 후 원하는 굵기의 폰트 옆에 있는 'Select this style'를 클릭
<div align = "center">
<img width="847" alt="20240311_111050" src="https://github.com/sooyounghan/Web/assets/34672301/bcbe1efa-3f6e-46bd-b73f-a1ff215efd67">
</div>


```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>04-02-web-font</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div>
        웹 폰트 연습입니다! 웹 폰트를 이용해보도록 하겠습니다.
    </div>
</body>
</html>
```

```css
@import url('https://fonts.googleapis.com/css2family=Black+Han+Sans&family=Jua&display=swap');

div {
    font-family: 'Jua', sans-serif;
    font-weight: 400;
    font-style: normal;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2ed0278a-b3a6-4ca6-a018-4b51bd4e7528">

</div>
