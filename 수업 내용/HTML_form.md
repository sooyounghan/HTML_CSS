-----
### form
-----

1. 사용자가 웹 브라우저를 통해 입력된 모든 데이터를 한 번에 웹 서버로 전송하는 양식
2. 전송한 데이터는 웹 서버가 처리, 처리 결과에 따라 다른 웹 페이지를 보여줌

<div align = "center">
<img width="308" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/94e10da8-3428-4978-a70f-a6bec097e9cf">
</div>

3. 사용자가 다양한 정보를 입력하고 서로 전달할 때 사용하는 태그
4. 단독으로 쓰이지 않고, 사용자가 다양한 정보를 입력하는 양식을 포함하는 최상위 태그

<div align = "center">
<img width="306" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/25c9a004-9e7a-44af-86ac-c9f31ac5569c">
</div>

5. form 태그의 모든 속성은 필수가 아니라 선택적 사용, 속성을 이용해 데이터를 전송할 때 어디로, 어떻게 보낼지 설정
6. name은 중복이 가능하므로, 주로 id를 사용
7. action : 서버 측의 페이지로 전송 
8. method 방식 : get 방식, post 방식 (기본값 : get 방식)

-----
### get, post 방식
-----
1. get 방식 : request의 body부분에 담겨서 전송되며, URL에 정보가 담겨서 전송
2. post 방식 : request의 header부분의 body에 담겨서 전송되며, URL 상에 전달한 정보가 표시되지 않음

<div align = "center">
<img width="306" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/68352951-fe25-471e-8dab-f1f0325bbe8b">
</div>

-----
### input
-----
1. 사용자로부터 입력을 받을 수 있는 입력 필드(input filed)를 정의할 때 사용
2. 사용자가 데이터를 입력할 수 있는 입력 필드를 선언하기 위해 <form> 요소 내부에서 사용

<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/850696b9-f7b5-431e-85cc-8b507e9137dd">
</div>

         * radio는 단 하나 선택, checkbox는 다중 선택이 가능함

3. checked 속성 : 페이지가 로드될 때 미리 선택될 <input> 요소를 명시 (하나를 선택해야 하는 경우에는 default 값에만 지정)
4. radio나 checkbox는 <> 설정 후 뒤에 그 항목을 표시할 수 있는 이름 표기
   
```html
   <!-- name에 snsYN을 중복 적용을 통해 수신 허용, 불허했는지에 대한 파라미터 값을 얻기 가능 // name은 중복 가능하지만. id는 중복 불가 -->
		<input type = "radio" name = "snsYN" id = "snsY" value = "Y" checked = "checked"> 수신허용
		<input type = "radio" name = "snsYN" id = "snsN" value = "N"> 수신불허
   ```

5. id 속성
    - id 속성은 고유해야하므로 중복 불가하지만, name은 중복이 가능
    - id 속성은 page 안에서 중복으로 사용할 수 없으며, 주로 JavaScript에서 다루기 위해 지정

6. name 속성
    - 입력 양식을 식별하는 이름 (요소를 구별하기 위한 이름)
    - 변수에 대한 이름
  
7. required 속성
<div align = "center">
<img width="306" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/5bdca2a4-4a3f-49ee-aefd-9c77c7265b82">
</div>

8. input type 종류 참조 : https://www.w3schools.com/html/html_form_input_types.asp
```html
<li> color : <input type = "color" name = "color" id = "color"></li>
```
```html
http://localhost:8081/webPro/html/ok.jsp?...&color=%23000000
```

	 %23 : #
  	 00 / 00 / 00 : RGB 값 의미

   - 시간 관련 속성 예시
```html
<fieldset>
	<legend> FieldSet </legend>
	<ul>
		<li> color : <input type = "color" name = "color" id = "color"></li>
		<li> date : <input type = "date" name = "date1" id = "date1"></li>
		<li> datetime-local : <input type = "datetime-local" name = "date2" id = "date2"></li>
		<li> month : <input type = "month" name = "month" id = "month"></li>
		<li> time : <input type = "time" name = "time" id = "time"></li>
		<li> week : <input type = "week" name = "week" id = "week"></li>
	</ul>
</fieldset>
```
<div align = "center">
<img width="758" alt="20240226_122058" src="https://github.com/sooyounghan/Web/assets/34672301/dcb94480-9744-4dd1-be1b-2aebd9ba31b6">
</div>

```html
<!-- %3A는 : 를 의미 -->
http://localhost:8081/webPro/html/ok.jsp?...date1=2024-02-26&date2=2024-02-27T12%3A18&month=2024-07&time=12%3A22&week=2024-W10
```

9. email, tel, url 속성은 DB와 연동하여 유효성 검사 필요
```html
<fieldset> <!-- 유효성 검사 필요 -->
	<legend> FieldSet </legend>
		<ul>
			<li> E-mail : <input type = "email" name = "email" id = "email"></li>
			<li> tel : <input type = "tel" name = "tel" id = "tel"></li>
			<li> URL : <input type = "url" name = "url" id = "url"></li>
		</ul>
</fieldset>
```
<div align = "center">
<img width="744" alt="20240226_123738" src="https://github.com/sooyounghan/Web/assets/34672301/9a136e3e-6af1-4c16-8cd6-2d58cb876d22">
</div>

10. file
    
	- 파일이 전송되는 것이 아니라 파일명에 대한 문자열이 전송
 	- 문자열 데이터를 받아서 클라이언트에게 속한 파일을 복사해 서버에 저장 (복사본 저장) : 인코딩 설정을 다르게 해야함

		   * File 업로드 기능 구현 시 form 태그의 method 방식은 post 방식, enctype = "multipart/form-date" 속성 값 설정
    
<div align = "center">
<img width="148" alt="20240226_124413" src="https://github.com/sooyounghan/Web/assets/34672301/43c1d257-d388-40b3-9e33-4fca49bccda0">
</div>  

```html
http://localhost:8081/webPro/html/ok.jsp?...file=1.txt&tel=&url= <!-- 1.txt 파일명이 문자열로 전송 -->
```

11. number
- 숫자를 입력할 수 있는 입력 필드를 정의 (쿼리스트링에 의해 문자열 값으로 전달)
- max : < input > 요소의 최댓값을 명시함
- min : < input > 요소의 최솟값을 명시함
- step : < input > 요소에 입력할 수 있는 숫자들 사이의 간격을 명시함
- value : < input > 요소의 초깃값(value)을 명시함

```html
<form action="/examples/media/action_target.php" method="get">
    1부터 20까지의 짝수 : <input type="number" name="even" value="1" min="2" max="20" step="2"><br>
    <input type="submit">
</form>
```
<div align = "center">
<img width="182" alt="20240226_140906" src="https://github.com/sooyounghan/Web/assets/34672301/1f886979-bc9d-42bf-8ac5-61637270a561">
</div>    

12. range
- 슬라이드 바를 조정하여 범위 내의 숫자를 선택할 수 있는 입력 필드를 정의
- 기본 범위 : 0 ~ 100까지이지만, 다음 요소와 함께 사용하면 그 범위 설정 가능 (기본 범위에서 벗어날 수 있음)
- max : < input > 요소의 최댓값을 명시함
- min : < input > 요소의 최솟값을 명시함
- step : < input > 요소에 입력할 수 있는 숫자들 사이의 간격을 명시함
- value : < input > 요소의 초깃값(value)을 명시함

```html
<form oninput="x.value=parseInt(a.value)" action="/examples/media/action_target.php" method="get">
    여러분의 나이대를 골라보세요.<br>
    Age : 0<input type="range" id="age" name="age" min="0" max="60" step="10" value = "10">60
    <output name="x" for="a"></output><br>
    <input type="submit">
</form>
```
- 기본값은 0, 최저값은 10, 최댓값은 60, 간격은 10으로 설정
- 범위 양끝단에 최저값과 최고값을 표기하면, 그 범위를 알 수 있음

<div align = "center">
<img width="179" alt="20240226_141917" src="https://github.com/sooyounghan/Web/assets/34672301/1348ba3e-e25a-4269-8a14-5da7d3dde1a0">
</div>   

13. search

  - 검색어를 입력할 수 있는 텍스트 필드를 정의
  - 검색 필드는 텍스트 필드와 기능적으로는 완전히 똑같지만, 브라우저에 의해 다르게 표현 가능
  - 반드시 name 속성을 설정해야 하며, name 속성이 설정되어 있지 않으면 서버로 제출되지 않음
  - name 속성값은 ‘q’

```html
<form action="/examples/media/action_target.php" method="get">
    검색 <input type="search" name="q">
    <input type="submit">
</form>
```

14. hidden (중요)

   - 사용자에게는 보이지 않는 숨겨진 입력 필드를 정의
   - 숨겨진 입력 필드는 렌더링이 끝난 웹 페이지에서는 전혀 보이지 않으며, 페이지 콘텐츠 내에서 그것을 볼 수 있게 만드는 방법도 없음
   - 숨겨진 입력 필드는 폼 제출 시 사용자가 변경해서는 안 되는 데이터를 함께 보낼 때 유용하게 사용
   - 클라이언트에게 노출시키지 않아도 되는 중요 정보이나 개발자에게 반드시 필요한 정보를 사용할 때 사용

```html
<form method="get">
    아이디 : <input type="text" name="user_id"><br>
    비밀번호 : <input type="password" name="user_pw"><br>
    <%!int game_token = 200;">
    <input type="hidden" id="gameToken" name="game_token" value="<%=game_token%>">
    <input type="submit">
</form>
```
```html
http://172.30.1.37:8081/webPro/html/formEx.jsp?user_id=&user_pw=&game_token=200
```

			URL 주소 쿼리스트링에 hidden_name인 gameToken=200가 전달되어 전송 (데이터를 은밀하게 전송할 수 있음)   

15. image
- webapp/imgs에 저장
- 제출 버튼(submit button)으로 사용될 이미지를 정의
- 텍스트가 아닌 이미지 형태로 된 제출 버튼을 생성하며, 이때 해당 이미지의 경로는 src 속성에 명시
- 강제 크기 조정 가능
  
< img src 형태 (순수 image) >
```html
<img src="http://localhost:8081/webPro/imgs/submit-button.gif" alt="submit" title="submit image" style="width:300px;height:100px">
```
	img의 src는 절대경로 또는 상대경로 가능 (절대경로는 위와 같이 명시해야함) / title은 그 image의 이름 / style 속성으로 너비, 크기 조정  

 < input type 형태 (submit 가능) >
 ```html
<input type = "image" src="<%=request.getContextPath()%>/imgs/submit-button.gif" style="width:300px;height:100px">
```
	 img src와 동일하지만, 제출 기능이 추가적으로 존재하며, 상대경로로 표시  

<div align = "center">
<img width="338" alt="20240226_154130" src="https://github.com/sooyounghan/Web/assets/34672301/7d3b35f9-df7b-4993-bc25-3b6120cbc05c">
</div>   

- css 선택자(Collector) 이용
```html
<head>
<meta charset="UTF-8">
	<title> Form Example </title>
	<style>
	/* CSS 주석문 */
	/* Selector (선택자) : { css속성:값;css속성:값;..css속성:값; } */
	/* 선택자에는 tag, .클래스명, #id명 가능 */
	/* img { width:300px;height:200px; } img 태그를 선택해 너비를 100으로 일괄 적용 */
	.c1 { width:200px;height:100px; } /* 클래스 c1인 요소에 대해 너비(width)와 높이(height)에 일괄 적용하겠다는 의미며, 여기에서는 이미지에 대해 submit 역할을 하는 input 요소에 대해 조정 */
	</style>
</head>
```

```html
<img src="http://localhost:8081/webPro/imgs/submit-button.gif" alt="submit" title="submit image" class = "c1">
<input type = "image" src="<%=request.getContextPath()%>/imgs/submit-button.gif" class = "c1">
```

16. button
- 단순한 푸시 버튼으로 렌더링
- 이벤트 처리기 (주로 Click 이벤트)를 부착하여, 클릭 버튼 가능

```html
<!-- button 모양 추가하되, 이름은 click이고, onclick 기능으로 누르면 창이 뜨는데, 그 메세지가 안녕 출력 -->
<input type = "button" value = "click" onclick = "alert('안녕');">
```
	- javaScript : onclick 이벤트는 버튼을 클릭했을 때 특정 기능을 수행하게 해줌
 	- javaScript : alert('표시내용') : alert창 (메세지 창)을 띄우되, 표시내용을 담은 창을 띄움

<div align = "center">
<img width="411" alt="20240226_161456" src="https://github.com/sooyounghan/Web/assets/34672301/ea119ed1-40fd-45bc-bf84-43c81de724a5">
</div>   

-----
### button
-----    
 - button 요소 (submit 역할 수행)
 - type : button (단어 그대로 button 역할) [input type = "button"과 동일, javaScript와 연동]

     		javaScript와 연동해 처리할 수 있는 기능으로 많이 사용

 - type : reset (입력한 값을 초기화) [input type = "reset"과 동일]
 - type : submit (입력한 값을 웹 서버에 전송) [input type = "submit"과 동일]
   
```html
<button type = "button">button (type = "button") 역할</button>
<button type = "reset">reset (type = "reset") 역할</button>
<button type = "submit">submit (type = "submit") 역할</button>
```   

<div align = "center">
<img width="209" alt="20240226_161509" src="https://github.com/sooyounghan/Web/assets/34672301/ca26a7f8-b180-4eec-967d-6991d840e9eb">
</div>   

-----
### output
-----    

- 스크립트 등에 의해 수행된 계산의 결과나 사용자의 액션에 의한 결과를 나타낼 때 사용
```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
  <input type="range" id="b" name="b" value="50" /> +
  <input type="number" id="a" name="a" value="10" /> =
  <output name="result" for="a b">60</output>
  <!-- 60은 for에서 언급한 두 값에 대한 기본 value 값을 의미 -->
</form>
```
1. a.value : name 속성이 a인 요소의 값(value)을 정수화
2. b.value : name 속성이 b인 요소의 값(value)을 정수화
3. output oninput = "result.value = parseInt(a.value) + parseInt(b.value)" : a의 값과 b의 값을 더해서 output name 속성이 result인 속성에 저장
4. out name = "이름" for = "output에서 사용할 변수들을 선언"
   
<div align = "center">
<img width="294" alt="20240226_142312" src="https://github.com/sooyounghan/Web/assets/34672301/aa3491ba-8883-4649-99d3-b89864c0c398">
</div>   

-----
### label
-----   

1. 폼 요소에 이름표를 붙이기 위한 것
2. <label> 요소는 for 속성을 사용하여 다른 요소와 결합
3. <label> 요소의 for 속성값은 결합하고자 하는 요소의 id 속성값과 같아야 함
4. 사용자가 마우스로 해당 텍스트를 클릭할 경우 <label> 요소와 연결된 요소를 곧바로 선택할 수 있어 사용자의 편의성을 높일 수 있음
   
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

: radio나 checkbox 버튼을 누르지 않고, 텍스트를 누르면 곧바로 선택 가능

-----
### select
-----
1. select Attribute : name, id, size, multiple
2. 옵션 메뉴를 제공하는 드롭다운 리스트(drop-down list)를 정의
3. 요소 내부의 < option > ~ < /option > 요소는 드롭다운 리스트(drop-down list)에서 사용되는 각각의 옵션을 정의
   - attribute : value
4. 전송 값 : select name = value

< 단일 선택 >
```html
<select name = "language", id = "select_language">
	<option value = "korean">한국어</option>
	<option value = "english">영어</option>
	<option value = "china">중국어</option>
	<option value = "japan">일본어</option>
</select>
```

< 다중 선택 (multiple) 및 크기 설정 (size) >
```html
<select name = "language", id = "select_language", size = "7" multiple = "multiple"> 
	<option value = "korean">한국어</option>
	<option value = "english">영어</option>
	<option value = "china">중국어</option>
	<option value = "japan">일본어</option>
</select>
```
<div align = "center">
<img width="188" alt="20240226_123525" src="https://github.com/sooyounghan/Web/assets/34672301/55e9e465-92ea-442c-ac13-78d5c30f68a8">
</div>   

  - multiple 속성으로 다중 선택 가능, size 속성으로 총 선택 가능한 수 지정 가능
  - 데이터 전송 값 : language=value1&language=value2

-----
### datalist
-----   

1. <input> 요소에서 사용하기 위한 옵션들의 리스트를 미리 정의할 때 사용
2. 사용자가 <input> 요소에 데이터를 입력할 때 미리 정의된 옵션을 드롭다운 리스트로 보여줌으로써 자동완성 기능을 제공
3. id 속성값을 명시하면, 해당 요소에서 미리 정의한 옵션들을 <input> 요소에서 사용

```html
<form action="/examples/media/action_target.php" method="get">
    학과 : <input type="text" name="st_department" list="depList"><br>
    이름 : <input type="text" name="st_name"><br><br>
    <datalist id="depList">
        <option value="컴퓨터공학과"></option>
        <option value="영어영문과"></option>
        <option value="경영학과"></option>
        <option value="사회체육과"></option>
    </datalist>
    <button type="submit">제출하기</button>
</form>
```

-----
### textarea
-----
1. 여러 줄의 데이터를 입력하고 싶을 때 사용
2. 크기 조절 가능
3. <textarea ...>기본값 설정</textarea> : textarea에 대한 기본값 설정
4. 초기 크기 행의 수와 열의 글자수로 너비와 높이 지정 가능 (rows (= height), cols (= width) Attribute)
5. style로 너비와 높이 지정 가능 (<textarea style = "속성명:값; 속성명:값" ("height:값; width:값")>)
   
```html
<textarea name = "my_self", id = "user_self" rows = "5" cols ="50">Text기본값</textarea>
<textarea name = "my_self_1", id = "user_self_1" style = "height:80px; width:240px">Text기본값</textarea>
```
3. textarea에 개행 후 입력하지 않고, 데이터를 전송하면 다음과 같이 my_self 파라미터에 다음과 같은 값이 등장

   - %0D : 개행 (\n) / %0A : Carriage Return (\r)
```html
http://localhost:8081/webPro/html/ok.jsp?user_name=ID&user_pwd=Password&my_self=12%0D%0A&user_submit=%EB%A1%9C%EA%B7%B8%EC%9D%B8
```

-----
### fieldset
-----   

1. HTML 양식 속에서 그룹을 만들 수 있음
2. < legend > 요소로 그룹의 설명을 제공

```html
<form>
  <fieldset>
    <legend>Choose your favorite monster</legend>

    <input type="radio" id="kraken" name="monster" value="K" />
    <label for="kraken">Kraken</label><br />

    <input type="radio" id="sasquatch" name="monster" value="S" />
    <label for="sasquatch">Sasquatch</label><br />

    <input type="radio" id="mothman" name="monster" value="M" />
    <label for="mothman">Mothman</label>
  </fieldset>
</form>
```
- 결과 : 
<div align = "center">
<img width="170" alt="20240226_121009" src="https://github.com/sooyounghan/Web/assets/34672301/de7eccb3-97e4-4af2-a9c5-81229fb9202e">
</div>   
