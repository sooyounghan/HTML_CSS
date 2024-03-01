-----
### Link
-----
: 현재 문서에서 다른 문서로 이동할 수 있는 수단

-----
### 링크 태그 : a(anchor)
-----
1. a 태그 : href 속성을 통해 다른 페이지, 전화번호, 이메일 주소 등 그 외 다른 URL로 연결할 수 있는 링크(연결)
2. 인라인 요소이며, 콘텐츠는 주로 링크의 목적지
3. target / href 속성
   - target = "blank"(="_self") : 현재 탭에서 열기 (기본값)
   - target = "_blank" : 새로운 탭에서 열기
   - href : 웹문서 주소 뿐 아니라, 전화번호 / 메일 주소 등 지정 가능 
4. 콘텐츠로 이미지 등 사용 가능
   
```html
<html>
	<body>
	  <a href = "tel:000-000-0000" target = "_self"> 전화걸기 </a>
	  <a href = "mailto:aa@naver.com target = "_blank> 메일쓰기 </a>
	  <a href = "https://www.w3schools.com/html/html_forms.asp" target = "_blank"> 네이버로 이동 (새로운 창) </a>
	  <a href = "https://www.w3schools.com/html/html_forms.asp" target = "_self"> 네이버로 이동 (기존 창) </a>
	  <a href = "https://www.w3schools.com/html/html_forms.asp" target = "blank"> 네이버로 이동 (기존 창) </a>
	</body>
</html>
```

```html
<html>
	<body>
	  <a href = "www.naver.com" target = "_self"><img src = "./a.png" alt = "그림 설명" width = "300" height = "600"></a>
	</body>
</html>
```

5. 앵커 기능

        <태그 id = "앵커 이름"> 텍스트 또는 이미지 </태그>
        <a href = "#앵커 이름"> 텍스트 또는 이미지 </a>

```html
<html>
<body>
    <ul id = "menu">
    	<li><a href = "#content">메뉴1</a></li>
    </ul>

      <h2 id = "content">내용1</h2>
      <a href = "#menu">[메뉴로]</a>
</body>
</html>

```
