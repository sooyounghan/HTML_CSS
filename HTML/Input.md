-----
### 입력 요소 태그 : input
-----
1. 사용자로부터 입력을 받을 수 있는 입력 필드(input filed)를 정의할 때 사용 (기본적으로 인라인 요소이며, 단일 태그)
2. 사용자가 데이터를 입력할 수 있는 입력 필드를 선언하기 위해 <form> 요소 내부에서 사용

<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/850696b9-f7b5-431e-85cc-8b507e9137dd">
</div>

-----
### input 속성
-----
1. id 속성
    - 고유 식별자로 중복 불가
    - page 안에서 중복으로 사용할 수 없으며, 주로 JavaScript에서 다루기 위해 지정

2. name 속성
    - 입력 양식(변수)을 식별하는 이름 (요소를 구별하기 위한 이름)
    - 중복 설정 가능
  
3. checked 속성
   - 페이지가 로드될 때 미리 선택될 input 요소를 명시 (하나를 선택해야 하는 경우에는 default 값에만 지정)
```html
<input type = "radio" name = "snsYN" id = "snsY" value = "Y" checked = "checked"> 수신허용
<input type = "radio" name = "snsYN" id = "snsN" value = "N"> 수신불허
```

4. required 속성
   - 반드시 입력해야 할 정보에 대해 부여하는 속성
   - 반드시 입력해야 할 정보를 입력하지 않을 때,

```html
<input type = "text" name = "name" id = "name" required = "required">
```
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/5bdca2a4-4a3f-49ee-aefd-9c77c7265b82">
</div>

5. autofocus 속성
	- 입력 커서를 표시
	- 페이지를 불러오자마자 입력 요소 중에서 원하는 요소에 마우스 커서 표시 

```html
<input type = "text" id = "name" autofocus required>
```

6. readonly 속성
   	- 읽기 전용 필드
   	- 사용자에게 내용을 보여주기만 하고 입력은 받을 수 없음
   	- true, false 값 중 하나만 사용

```html
<input type = "text" id = "subj" value = "오전 9시 ~ 11시" readonly = "true">
```

7. placeholder 속성
	- 사용자가 텍스트를 입력할 때 도움이 되도록 입력란에 적당한 힌트 내용을 표시
	- 그 필드를 클릭하면 내용이 사라지도록 함

```html
<input type = "text" id = "subj" value = "오전 9시 ~ 11시" readonly = "true" placeholder = "수업시간">
```

-----
### input 속성 : type
-----
1. type 값에 따라 입력 요소의 형태나 입력 데이터 유형이 달라짐
2. 사용 가능한 type은 20여가지이며, 기본값은 text
3. input type 종류 참조 : https://www.w3schools.com/html/html_form_input_types.asp

-----
### input type 기본
-----
1. line
   - 한 줄 짜리 일반 텍스트를 입력하는 필드

       		<input type = "text" [속성 = "속성 값"]>
     
   - 속성

          name : 텍스트 필드를 구별할 수 있도록 이름 부여
          size : 텍스트 필드의 길이 지정 (즉, 화면에 몇 글자가 보일지 결정)
          value : 텍스트 필드 요소가 화면에 표시될 때 텍스트 필드 부분에 표시될 내용
          maxlength : 텍스트 필드에 입력할 수 있는 최대 문자 개수

```html
<input type="text" name="user_id" id = "id" size = "10" value = "default" maxlength = "7"><br>
```

2. password
   - 비밀번호 입력 필드
   - value 속성이 없음

       		<input type = "password" [속성 = "속성 값"]>

```html
<input type="password" name="user_pw" id = "pw">
```

3. submit
   : 사용자가 입력한 정보를 서버로 전송 

4. reset
   : 요소에 입력된 모든 정보를 초기화 

```html
<input type="submit" value = "제출" name = "submit" id = "submit">
<input type="reset" value = "취소" name = "reset" id = "reset">
```

-----
### input type 종류
-----
1. number
	- 숫자를 입력할 수 있는 입력 필드 정의 (쿼리스트링에 의해 문자열 값으로 전달)
	- 스핀 박스로 표시

          스핀 박스 : 입력 창 오른쪽 작은 화살표를 표시해 화살표 클릭에 따라 숫자 증감 가능
<div align = "center">
<img width="182" alt="20240226_140906" src="https://github.com/sooyounghan/Web/assets/34672301/1f886979-bc9d-42bf-8ac5-61637270a561">
</div>    
	
 
   - 속성

          max : 요소의 최댓값을 명시함
          min : 요소의 최솟값을 명시함
          step : 요소에 입력할 수 있는 숫자들 사이의 간격을 명시함
          value : 요소의 초깃값(value)을 명시함
 
```html
1부터 20까지의 짝수 : <input type = "number" name = "even" id = "even" value = "1" min = "2" max = "20" step = "2">
```

2. range
	- 슬라이드 막대를 조정하여 범위 내의 숫자를 선택

<div align = "center">
<img width="179" alt="20240226_141917" src="https://github.com/sooyounghan/Web/assets/34672301/1348ba3e-e25a-4269-8a14-5da7d3dde1a0">
</div>   

	
  - 기본값 : 0 ~ 100
  - 속성을 통해 기본 범위에서 벗어날 수 있음
  - 속성 
	
          max : 요소의 최댓값을 명시함
          min : 요소의 최솟값을 명시함
          step : 요소에 입력할 수 있는 숫자들 사이의 간격을 명시함
          value : 요소의 초깃값(value)을 명시함
            * 범위 양끝단에 최저값과 최고값을 표기하면, 그 범위를 알 수 있음

```html
Age : 0<input type = "range" id = "age" name = "age" min = "0" max = "100" step = "1" value = "0">100
```

3. radio, checkbox
	- radio : 두 개 이상의 선택 중 하나만 선택할 때 사용
	- checkbox : 두 개 이상 여러 가지를 선택해도 될 경우 사용
	- 속성

           name : 라디오 버튼이나 체크박스를 구분하기 위해 이름 지정
           value : 선택한 라디오 버튼이나 체크박스를 서버로 알려줄 때 넘길 값 지정
           checked : 처음 아무것도 선택되지 않은 상태로 화면에 표시 (기본으로 선택해놓은 항목이 있어야 한다면 사용)

```html
<input type = "radio" name = "snsYN" id = "snsY" value = "Y" checked = "checked"> 수신허용
<input type = "radio" name = "snsYN" id = "snsN" value = "N"> 수신불허

<input type = "checkbox" name = "spring" id = "spring" value = "spring" checked = "checked"> 봄
<input type = "checkbox" name = "summer" id = "summer" value = "summer"> 여름
<input type = "checkbox" name = "autumn" id = "autumn" value = "autumn" checked = "checked"> 가을
<input type = "checkbox" name = "winter" id = "winter" value = "winter"> 겨울
```

5. color
	: 색상표에서 사용자가 색상을 선택할 수 있도록 제공

```html
color : <input type = "color" name = "color" id = "color"></li>
```
```html
http://localhost:8081/webPro/html/ok.jsp?...&color=%23000000
```

    - %23 : #
    - 00 / 00 / 00 : RGB 값 의미

6. hidden (중요)
   - 사용자에게 보이지 않는 숨겨진 입력 필드 정의
   - 숨겨진 입력 필드는 렌더링이 끝난 웹 페이지에서는 전혀 보이지 않음
   - 페이지 콘텐츠 내에서 그것을 볼 수 있게 만드는 방법도 없음
   - 숨겨진 입력 필드는 제출 시 사용자가 변경해서는 안 되는 데이터를 함께 보낼 때 유용하게 사용
   - 클라이언트에게 노출시키지 않아도 되는 중요 정보이나 개발자에게 반드시 필요한 정보를 사용할 때 사용

         <input type = "hidden" name = "이름" value = "서버로 넘길 값">

```html
<%!int game_token = 200;">
<input type="hidden" id="gameToken" name="game_token" value="<%=game_token%>">
```
```html
http://172.30.1.37:8081/webPro/html/formEx.jsp? ... game_token=200
```
			URL 주소 쿼리스트링에 hidden_name인 gameToken=200가 전달되어 전송 (데이터를 은밀하게 전송할 수 있음)   

-----
### input type : 분화된 텍스트 필드
-----   
1. search

	  - 검색어를 입력할 수 있는 텍스트 필드 정의
	  - 텍스트 필드와 기능적으로는 완전히 똑같지만, 브라우저에 의해 다르게 표현 가능
	  - 반드시 name 속성을 설정, name 속성이 설정되어 있지 않으면 서버로 제출되지 않음


```html
<input type = "search" name =" search" id = "search" placeholder = "검색어를 입력하세요.">
<input type = "submit" value = "제출">
```

2. url

 	- 텍스트 필드로 웹 주소 별도 지정 가능 (URL 입력란 만들기)
 	- 반드시 http://로 시작하는 사이트 주소를 입력

3. email : 메일 주소 입력 필드
4. tel : 전화번호 입력 필드

< email, tel, url 속성은 DB와 연동하여 유효성 검사 필요 >

```html
E-mail : <input type = "email" name = "email" id = "email"></li>
tel : <input type = "tel" name = "tel" id = "tel"></li>
URL : <input type = "url" name = "url" id = "url"></li>
<input type = "submit" value = "제출">
```

<div align = "center">
<img width="744" alt="20240226_123738" src="https://github.com/sooyounghan/Web/assets/34672301/9a136e3e-6af1-4c16-8cd6-2d58cb876d22">
</div>


5. image
	- 텍스트가 아닌 이미지 형태로 된 제출 버튼을 생성
  	- 제출 버튼(submit button)으로 사용될 이미지를 정의
	- 크기 조정 가능

          webapp/imgs에 저장
    
```html
<input type = "image" src="/imgs/submit-button.gif" style="width:300px;height:100px">
```

6. file
    
	- 파일이 전송되는 것이 아니라 파일명에 대한 문자열이 전송
<div align = "center">
<img width="148" alt="20240226_124413" src="https://github.com/sooyounghan/Web/assets/34672301/43c1d257-d388-40b3-9e33-4fca49bccda0">
</div>  
	 - 파일 전송 : 문자열 데이터를 받아서 클라이언트에게 속한 파일을 복사해 서버에 저장 (복사본 저장) : 인코딩 설정을 다르게 해야함

		* File 업로드 기능 구현 시 form 태그의 method 방식은 post 방식, enctype = "multipart/form-data" 속성 값 설정
 
```html
<input type - "file" name = "file" id = "file">
http://localhost:8081/webPro/html/ok.jsp?...file=1.txt&tel=&url= <!-- 1.txt 파일명이 문자열로 전송 -->
```

7. button
	- 단순한 Push 버튼 (폼 안에 버튼 형태를 만듬)
	- submit이나 reset 같은 자체 기능이 없이 오직 버튼만 넣음 : 스크립트 함수 등을 연결해 사용
	- 이벤트 처리기 (주로 Click 이벤트)를 부착하여, 클릭 버튼 가능
	- 속성 value : 버튼에 표시할 내용 지정

```html
<!-- button 모양 추가하되, 이름은 click이고, onclick 기능으로 누르면 창이 뜨는데, 그 메세지가 안녕 출력 -->
<input type = "button" value = "click" onclick = "alert('안녕');">
```
	* javaScript : onclick 이벤트는 버튼을 클릭했을 때 특정 기능을 수행하게 해줌
 	* javaScript : alert('표시내용') : alert창 (메세지 창)을 띄우되, 표시내용을 담은 창을 띄움

<div align = "center">
<img width="411" alt="20240226_161456" src="https://github.com/sooyounghan/Web/assets/34672301/ea119ed1-40fd-45bc-bf84-43c81de724a5">
</div> 

8. 시간 관련 속성

```html
date : <input type = "date" name = "date1" id = "date1">
datetime-local : <input type = "datetime-local" name = "date2" id = "date2">
month : <input type = "month" name = "month" id = "month">
time : <input type = "time" name = "time" id = "time">
week : <input type = "week" name = "week" id = "week">
```
<div align = "center">
<img width="758" alt="20240226_122058" src="https://github.com/sooyounghan/Web/assets/34672301/dcb94480-9744-4dd1-be1b-2aebd9ba31b6">
</div>

```html
<!-- %3A는 : 를 의미 -->
http://localhost:8081/webPro/html/ok.jsp?...date1=2024-02-26&date2=2024-02-27T12%3A18&month=2024-07&time=12%3A22&week=2024-W10
```
