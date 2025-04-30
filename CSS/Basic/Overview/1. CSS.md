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
### CSS 상속
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/6a9f5a63-5abc-4c46-9553-209688b59954">
</div>

1. 부모 요소의 속성값을 자식 요소에게도 상속
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/47a85031-3d8b-42a2-a021-512ce0378071">
</div> 

<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/48ba1ee2-fe9a-492d-9863-d5b99bad7f24">
</div> 

2. 부모 요소에 적용된 속성이 자식 요소는 물론, 그 자식 요소의 속성에게까지 상속

3. 하지만, 모든 요소가 상속되지는 않음
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/f3a8123d-117d-412b-ba4d-e3370e546768">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/ffd736d9-9efc-494e-b013-f29784e54613">
</div> 

  - 속성이 적용된 Container Box에만 적용되고, 그 자식 요소에는 적용되지 않음
  - 즉, 상속되는 속성이 있고, 아닌 속성이 있음

<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/82f0643d-6dcd-431d-ac86-c13b777c1470">
</div> 

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>04-01-inheritance</title>
    <link rel="stylesheet" href="./index.css">
</head>
<body>
    <div class="container">
        안녕하세요. 처음 뵙겠습니다.
        <div class="inner-box">
            <p>제 이름은 다람쥐입니다.</p>
        </div>
    </div>
</body>
</html>
```
```css
* {
    box-sizing:border-box;
}

.container {
    color:blue;
    font-size:38px;

    border:4px solid orange;
}

.inner-box {
    color:red;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/69f94c11-570f-4592-9047-202865ce0892">
</div>   

  - color와 font-size는 상속하는 요소이므로 자식 요소까지 영향
  - border의 경우 상속되지 않는 속성이므로 부모 요소에서만 적용
  - 상속받는 자식 요소의 경우에도 중첩되는 요소에 대해 다시 설정 가능

-----
### CSS 상속 우선 순위
-----
: Cacading이라는 룰에 의해 그 우선순위가 결정
