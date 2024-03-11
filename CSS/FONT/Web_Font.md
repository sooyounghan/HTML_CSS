-----
### 웹 폰트 (Web Font)
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
  - arial은 영문 폰트로, 영문에 대한 폰트를 가지고 있지만, 한글 폰트는 없으므로 ABC에만 적용
  - 맑은 고딕은 영문 / 한글 폰트이므로, 한글 폰트에 대해 다음 우선순위인 맑은 고딕 폰트 적용
  - 
