-----
### 컨테이너 태그 (Container Tag)
-----
1. 컨테이너 태그   
   : 콘텐츠나 레이아웃에 아무런 영향을 주지 않고, 단지 다른 요소 여럿을 묶어 관리하기 편하게 만든 역할을 하는 태그
2. 콘텐츠 내용을 구분하거나, 공통적인 스타일을 적용하고자 할 때 사용 [CSS나 JS와 연동하여 사용하기 편리]
3. 종류
   - < div > < /div > : 블록 레벨 컨테이너
   - < span > < /span > : 인라인 컨테이너

   
-----
### 컨테이너 태그 (span, div)
-----
1. span : 단순 텍스트나 텍스트에 관련된 마크업 등 구문 콘텐츠 스타일이나 속성의 범위를 적용하기 위해 감싸주는 태그   
   (인라인 레벨 컨테이너)

```html
<!DOCTYPE html>
	<html>
	<body>
		<span style = "color:blue;">이 부분</span>은 파란색으로 표시합니다.
	</body>
	</html>
```

2. div : 레이아웃을 만들거나 콘텐츠를 나누는(Division) 컨테이너로 사용 (블록 레벨 컨테이너)
   
```html
<!DOCTYPE html>
<html>
  <body>
    <div>
      <img src = "/pic.jpg" alt = "사진" width = "700" height = "600><
    </div>
    <div>
      <p> div로 나눈 영역 </p>
    </div>
  </body>
</html>
```

-----
### 전역 속성 (Global Attribute)
-----
1. 모든 HTML에 공통으로 사용할 수 있는 속성
2. 대표적인 전역 속성
   - id : 요소에 고유한 이름을 부여하는 식별자 역할 속성 [모든 id는 서로 다른 값을 가져야함] (사용자 정의 값)
   - class : 요소를 그룹 별로 묶을 수 있는 식별자 속성 [다중 지정 및 중복 가능] (사용자 정의 값)
   - style : 요소에 적용할 CSS 스타일을 선언하는 속성
   - title : 요소의 추가 정보를 제공하는 텍스트 속성 (사용자에게 툴팁 제공)

            특정 태그에만 지정 가능한 속성도 존재
```html
<!DOCTYPE html>
<html>
  <body>
    <div id = "pictrue">
      <p class = "title"> div로 나눈 영역 </p>
      <img src = "/pic.jpg" alt = "사진" width = "700" height = "600 title = "사진 설명">
    </div>
    <div id = "text">
      <p class = "title" > div로 나눈 영역 </p>
    </div>
  </body>
</html>
```
