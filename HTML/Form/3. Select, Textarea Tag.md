-----
### select
-----
1. 다수의 옵션(선택지)을 포함할 수 있는 선택 메뉴
2. 옵션 메뉴를 제공하는 Drop-down list를 정의
3. 요소 내부 < option > < /option > 요소로 각각의 옵션을 정의
4. 속성

   - value

          + <select> 태그로 목록의 시작과 끝을 표시하고 그 안에 <option> 태그를 사용해 원하는 항목 추가
          + <option> 태그는 value 속성을 이용해 서버로 넘겨주기 위한 값을 지정
            * 쿼리스트링 전달 값 : select_name = value

    - name, id, size, multiple

           + size : 화면에 표시될 메뉴의 항목 개수 지정
           + multiple : 여러 개의 옵션이 브라우저 화면에 함께 표시되어 여러 항목 선택 가능
<div align = "center">
<img width="188" alt="20240226_123525" src="https://github.com/sooyounghan/Web/assets/34672301/55e9e465-92ea-442c-ac13-78d5c30f68a8">
</div>   

 5. < option > 속성
    - value : 옵션을 선택했을 때 서버로 넘겨질 값 지정
    - selected : 화면에 표시될 때 기본적 선택되어있는 옵션 지정

-----
### select 단일 선택 예제
-----
```html
<select name = "language", id = "select_language">
	<option value = "korean" selected = "selected">한국어</option>
	<option value = "english">영어</option>
	<option value = "china">중국어</option>
	<option value = "japan">일본어</option>
</select>
```
    데이터 전송 값 : language=value1

-----
### select 다중 선택
-----
```html
<select name = "language", id = "select_language", size = "7" multiple = "multiple"> 
	<option value = "korean" selected = "selected">한국어</option>
	<option value = "english">영어</option>
	<option value = "china">중국어</option>
	<option value = "japan">일본어</option>
</select>
```

    데이터 전송 값 : language=value1&language=value2

-----
### optgroup : select option 그룹
-----

1. 목록에서 여러 항목들을 그룹으로 묶을 수 있는 입력 요소
2. label 속성을 이용해 그룹의 제목을 붙임

```html
<select id = "class">
	<optgroup label = "공과대학">
		<option value = "archi"> 건축공학과 </option>
		<option value = "elec"> 전기전자공학과 </option>
	</optgroup>
	<optgroup label = "인문대학">
		<option value = "lang"> 어문학부 </option>
		<option value = "philo"> 철학과 </option>
	</otpgroup>
</select>
```

-----
### datalist
-----   
1. 입력 필드 요소에서 사용하기 위한 옵션들의 리스트를 미리 정의할 때 사용
2. 사용자가 입력 필드에 데이터를 입력할 때 미리 정의된 옵션을 리스트로 보여줌으로써 자동완성 기능을 제공
    - 텍스트 필드와 함께 사용(type = "text")
      
3.  < datalist > ~ < /datalist >로 데이터 목록의 시작과 끝을 표시하고, 그 사이 < option > 태그로 각 데이터 옵션 표시
4.  id 속성값을 명시하면, 해당 요소에서 미리 정의한 옵션들을 <input> 요소에서 사용

```html
학과 : <input type="text" name="st_department" list="depList"><br>
이름 : <input type="text" name="st_name"><br><br>
<datalist id="depList">
   <option value="컴퓨터공학과"></option>
   <option value="영어영문과"></option>
   <option value="경영학과"></option>
   <option value="사회체육과"></option>
</datalist>
<button type="submit">제출하기</button>
```

-----
### textarea
-----
1. 여러 줄의 데이터를 입력할 수 있는 입력 요소 (웹에서 크기 조절 가능)


       <textarea 속성 = "속성값">기본값 설정</textarea>
   
3. 속성 : rows, cols
    - 초기 크기 행의 수와 열의 글자수로 너비와 높이 지정 가능
      
```html
<textarea name = "my_self", id = "user_self" rows = "5" cols ="50">Text기본값</textarea>
```

3. style로 너비와 높이 지정 가능

       <textarea style = "속성명:값;속성명:값" ("height:값;width:값")>

```html
<textarea name = "my_self_1", id = "user_self_1" style = "height:80px; width:240px"> Text기본값 </textarea>
```
  
    < 개행과 캐리지리턴 값 >
     - %0D : 개행 (\n) 
     - %0A : Carriage Return (\r)
     
```html
http://localhost:8081/webPro/html/ok.jsp? ... my_self=12%0D%0A ...
```
