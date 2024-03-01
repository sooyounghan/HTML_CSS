-----
### form 태그
-----
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/94e10da8-3428-4978-a70f-a6bec097e9cf">
</div>   

1. 사용자가 웹 브라우저를 통해 입력된 모든 데이터를 한 번에 웹 서버로 전송하는 양식
2. 전송한 데이터는 웹 서버가 처리, 처리 결과에 따라 다른 웹 페이지를 보여줌
3. 웹에서의 폼은 크게 사용자가 입력하는 부분과 입력한 내용을 서버로 전송하는 버튼 부분으로 나눠짐
4. 단독으로 쓰이지 않고, 사용자가 다양한 정보를 입력하는 양식을 포함하는 최상위 태그
   
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/25c9a004-9e7a-44af-86ac-c9f31ac5569c">
</div>   

4. action 속성 : 입력값을 전송할 서버의 URL 
5. method 속성 : 클라이언트가 입력한 데이터를 어떠한 방식으로 전송할지 결정 [GET 방식, POST 방식 (기본값 : GET 방식)]

       - form 태그의 모든 속성은 필수가 아니라 선택적 사용
       - 속성을 이용해 데이터를 전송할 때 어디로, 어떻게 보낼지 설정

       - form의 내용(입력값) 제출을 위해 input 태그의 submiot 타입 사용 가능
       - name은 중복이 가능, id를 사용
      
7. autocomplete 속성 : 자동 완성 기능 (기본값 : on)

```html
<form action = "/login.jsp" method = "post" autocomplete = "off">
    아이디 : <input type = "text" name = "user_id" id = "id" placeholder = "아이디" value = "ID"><br>
    비밀번호 : <input type = "password" name = "user_pw" id = "pwd" placeholder = "비밀번호" value = "password"><br>
    <input type="submit" value = "로그인">
</form>
```

-----
### GET, POST 방식
-----
1. GET 방식 (기본값)
   - 서버에 요청을 보내어 응답을 받아냄 (서버로부터 정보를 가져오겠다는 성격의 요청)
   - Request의 body부분에 담겨서 전송
   - URL에 정보가 담겨서 전송
     
2. POST 방식
   - 서버에 요청을 보내어 작업을 수행 (서버에 있는 데이터를 추가/수정/삭제한 후 응답을 받아내는 성격의 요청)
   - Request의 Header부분의 Body에 담겨서 전송
   - URL 상에 전송한 정보가 표시되지 않음

<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/68352951-fe25-471e-8dab-f1f0325bbe8b">
</div>

-----
### label
-----   
1. 폼 요소에 이름표를 붙이기 위한 것

       - label : 입력 창 옆의 붙여 놓은 텍스트를 의미
    	 - 폼 요소와 레이블 텍스트가 서로 연결되어 있다는 것을 브라우저가 알 수 있음
   	  
2. for 속성
   - 다른 요소와 결합
   - 사용자가 마우스로 해당 텍스트를 클릭할 경우 <label> 요소와 연결된 요소를 곧바로 선택 가능
   - 사용자의 편의성을 높이기 가능


   	    	 + id 속성을 이용해 서로 연결, id 속성 값을 <label> 태그의 for 속성에게 알려주는 방법
           + <label> 태그와 <input> 소스가 떨어져 있더라도 둘 사이를 쉽게 연결할 수 있음
   	
3. <label> 요소의 for 속성값은 결합하고자 하는 요소의 id 속성값과 같아야 함

        <label [속성 = "값" ]>레이블<input .. ></label>
   
   		  <label for = "id이름" >레이블</label>
   		  <input id = "id이름" [ 속성 = "속성 값" ]>

```html
<li> 성별 : 
	<input type = "radio" name = "male" id = "user_sex_male" checked = "checked" value = "남"><label for = "male"> 남 </label>
	<input type = "radio" name = "female" id = "user_sex_female" value = "여"><label for = "female"> 여 </label>
</li>

<li> 좋아하는 동물 :
	<input type = "checkbox" name = "animal_cat" id = "cat" value = "cat" checked = "checked"><label for = "cat"> 고양이 </label>
	<input type = "checkbox" name = "animal_dog" id = "dog" value = "dog"><label for = "dog"> 강아지 </label>
	<input type = "checkbox" name = "animal_fish" id = "fish" value = "fish"><label for = "fish"> 물고기 </label>
</li>
```

-----
### fieldset
-----   
1. 하나의 폼 안에서 폼 요소를 그룹으로 묶는 태그 
2. <fieldset> </fieldset> : 태그 사이의 폼들을 하나의 영역으로 묶어 외곽선 표시
3. <legend> : <fieldset> 태그로 묶은 그룹에 제목을 붙여줌 

```html
<form>
  <fieldset>
    <legend>좋아하는 몬스터</legend>

    <input type = "radio" id = "kraken" name = "monster" value = "kraken" />
    <label for = "kraken">크라켄</label><br/>

    <input type = "radio" id = "sasquatch" name = "monster" value = "sasquatch" />
    <label for = "sasquatch">사스콰치</label><br/>

    <input type = "radio" id = "mothman" name = "monster" value = "mothman" />
    <label for = "mothman">모스맨</label>
  </fieldset>
</form>
```
<div align = "center">
<img width="170" alt="20240226_121009" src="https://github.com/sooyounghan/Web/assets/34672301/de7eccb3-97e4-4af2-a9c5-81229fb9202e">
</div>   

-----
### iframe (Inline Frame)
-----    
1. 웹 페이지 안에 다른 html 파일을 불러와서 삽입해주는 태그
2. src 속성 : 삽입할 웹 문서의 경로를 작성
3. width, height 속성 : frame의 크기를 조절 가능

```html
<iframe name = "inner" src = "http://www.daum.com" width = "300" height = "400">다음</iframe>
```

-----
### button
-----    
 1. type : button
    : input type = "button"과 동일 (주로 javaScript와 연동하여 사용)

     		javaScript와 연동해 처리할 수 있는 기능으로 많이 사용

 2. type : reset
    - 입력한 값을 초기화
    - input type = "reset"과 동일
 
3. type : submit (기본값)
    - 입력한 값을 웹 서버에 전송
    - input type = "submit"과 동일 
   
```html
<button type = "button">button (type = "button") 역할</button>
<button type = "reset">reset (type = "reset") 역할</button>
<button type = "submit">submit (type = "submit") 역할</button>
```   

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ca26a7f8-b180-4eec-967d-6991d840e9eb">
</div>   


-----
### output
-----    
1. 입력하는 값이 계산 결과라는 것을 브라우저에게 알려주는 태그
2. <output> 태그로 묶인 부분이 일반 텍스트가 아닌 계산의 결과값
3. 스크립트 등에 의해 수행된 계산의 결과나 사용자의 액션에 의한 결과를 나타낼 때 사용

```html
<form oninput = "result.value=parseInt(a.value)+parseInt(b.value)">
  <input type = "number" id = "a" name = "a" value= " 10"/> +
  <input type = "range" id = "b" name = "b" value = "50"/> =
  <output name = "result" for = "a b"></output>
</form>
```

     - a.value : name 속성이 a인 요소의 값(value)을 정수화
     - b.value : name 속성이 b인 요소의 값(value)을 정수화
     - oninput = "result.value = parseInt(a.value) + parseInt(b.value)" : a의 값과 b의 값을 더해서 output name 속성이 result인 속성에 저장
     - out name = "이름" for = "output에서 사용할 변수들을 선언"
   
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/aa3491ba-8883-4649-99d3-b89864c0c398">
</div>   
