-----
### 캐스케이딩 (Cascading)
-----
1. '폭포', '위에서 아래로 흐르는'
2. 수 많은 스타일 요소 중 어떤 스타일을 브라우저에 그릴지 결정해주는 CSS 우선순위 적용 원리
3. 기준 : 중요도, 구체성(명시도), 선언 순서

-----
### 중요도
-----
1. CSS가 선언된 위치에 따라 우선순위가 결정
2. 브라우저 스타일 시트 : 브라우저 프로그램의 개발자들의 기본값 스타일 시트
3. 사용자 스타일 시트 : 유저의 스타일 시트
4. 개발자 스타일 시트 : 웹 페이지를 만든 개발자의 스타일 시트
5. 우선순위 : 브라우저 스타일 시트 < 사용자 스타일 시트 < 개발자 스타일 시트

-----
### 브라우저 스타일 시트
-----
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/8345d4ce-86ba-4bbb-9f79-c5e4cf80fc35">
</div>

1. CSS가 적용되지 않은 스타일 시트
2. 브라우저에 내장된 스타일 시트

-----
### 사용자 스타일 시트
-----
1. 사용자 폰트 지정
2. 고대비 모드 사용 등

-----
### 개발자 스타일 시트
-----
1. 해당 웹 페이지의 개발자가 제작하여 만든 스타일 시트

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/fd16b86e-273d-4ebf-905c-a8f552cae008">
</div>

2. 개발자 스타일 시트 내 중요도 : < link >로 연결한 CSS 파일 < < style > 요소 안의 CSS < 인라인 스타일 CSS

-----
### 중요도 정리
-----
1. 인라인 스타일 CSS
2. < style > 요소 안에 있는 CSS
3. < link > 로 연결한 CSS 파일
4. 사용자 스타일 시트
5. 브라우저 스타일 시트

-----
### 구체성 (명시도)
-----
1. 선택할 대상을 구체적으로 특정할수록 명시도가 높아짐 (선택자 이용)
2. 명시도가 높아지면 우선순위도 함께 높아짐
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/4138b612-5439-4f44-8a63-adbe72c95078">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/88626a59-be58-439b-a2b1-d44261e823fb">
</div>

<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/cd2eba28-d2bb-41db-86a5-b75df68f166d">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/489efae2-9dcf-4aae-ad78-92fc48f70345">
</div>

3. 강제 명시도 끌어올리기 : !important (전체 우선순위를 망가뜨릴수 있으므로 사용하지 않는 것이 권장)
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/c964ce85-3429-4a76-a1f2-a5da4eaf5c51">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/e89734c0-8e82-4468-b8b9-a2c9e9709510">
</div>

-----
### 선언 순서
-----
: 나중에 선언한 스타일이 우선 적용
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/95dcc2f0-d68e-437a-912d-440f035a5cb6">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/d7cfb57b-fb65-4918-9ff3-62757754dd4c">
</div>

-----
### 예제
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>05-01-cascading</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="text-clas" id="text-id">
        Cascading 입니다.
    </div>
</body>
</html>
```
```css
* {
    background-color:yellow;
}

div {
    background-color:aqua;
}

.text-clas {
    background-color:blue;
}

#text-id {
    background-color:red;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/7d1a03c7-7503-4123-a9e7-8054a3423e62">
</div>
