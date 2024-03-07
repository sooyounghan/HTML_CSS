-----
### Layout
-----
1. CSS를 이용해 단순한 문서의 형태인 HTML을 보기 좋게 배치하고 재배열 하는 것
2. 관련 기능, 완성된 배열 등 포괄적 지칭

-----
### Selector
-----
1. 전체 선택자 : HTML 내 모든 요소를 선택하는 선택자
```css
* {
  property : value;
}
````

2. 그룹 선택자 : 원하는 선택자 여러 가지를 콤마를 통해 연결
```css
.class1, .class2 {
  proprty : value;
}
```

3. 가상 선택자 : 실제로 HTML 요소를 수정하지 않고, CSS만을 가상 요소로 추가해 선택
```css
선택자 : 가상 클래스 {
   property : value;
}
```
  - first-child : 해당 요소의 자식 중 첫 번쨰 자식 요소를 의미
```css
.class:first-child {
  property : value;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/e94c4802-00f4-424d-ae57-d6f7d05bf5d2">
</div>

 - last-child : 해당 요소의 자식 중 마지막 자식 요소를 의미
```css
.class:last-child {
  property : value;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/DataBase/assets/34672301/1496a142-9dae-41e8-bbae-b9b4277dceef">
</div>

 - n-th child (n) : 해당 요소의 자식 중 n번째 자식 요소 의미
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
### CSS Layout
-----
1. Float : 모바일 웹 개념 전, PC로만 사용했던 웹 페이지 구성
2. Flex : FLEX 속성을 이용해 레이아웃을 구성, 오직 레이아웃 구현을 위해 제작된 속성 (Float보다 편리)
3. Grid : 레이아웃 구현을 목적으로 FLEX와 목적이 비슷
4. flex와 grid는 상황에 따라 혼용

-----
### Float가 사용되지 않는 이유
-----
1. 반응형 웹에 적합하지 않음
2. 반응형 웹 : 모바일, 태블릿, PC 등 접속하는 기기의 너비에 맞춰 레이아웃이 변하는 웹 페이지
