-----
### label
-----   

1. 폼 요소에 이름표를 붙이기 위한 것

    	    	- label이란 입력 창 옆의 붙여 놓은 텍스트를 의미
   	     	- 폼 요소와 레이블 텍스트가 서로 연결되어 있다는 것을 브라우저가 알 수 있음
   	  
3. <label> 요소는 for 속성을 사용하여 다른 요소와 결합

   		- 즉, id 속성을 이용해 서로 연결하는 것이며, id 속성 값을 <label> 태그의 for 속성에게 알려주는 방법
   	   	- <label> 태그와 <input> 소스가 떨어져 있더라도 둘 사이를 쉽게 연결할 수 있음
   	
5. <label> 요소의 for 속성값은 결합하고자 하는 요소의 id 속성값과 같아야 함

     		< label [속성 = "값" ] > 레이블 < input .. >< /label >
   		< label for = "id이름" > 레이블 < /label>
   		< input id = "id이름" [ 속성 = "속성 값" ]>
   
6. 사용자가 마우스로 해당 텍스트를 클릭할 경우 <label> 요소와 연결된 요소를 곧바로 선택할 수 있어 사용자의 편의성을 높일 수 있음

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

1. 옵션 메뉴를 제공하는 드롭다운 리스트(drop-down list)를 정의
2. 요소 내부의 < option > ~ < /option > 요소는 드롭다운 리스트(drop-down list)에서 사용되는 각각의 옵션을 정의
   - attribute : value
   - < select > 태그로 드롭 다운 목록의 시작과 끝을 표시하고 그 안에 < option > 태그를 사용해 원하는 항목 추가
   - < option > 태그는 value 속성을 이용해 서버로 넘겨주기 위한 값을 지정
3. 전송 값 : select name = value
4. select Attribute : name, id, size, multiple
   - size : 화면에 표시될 드롭다운 메뉴의 항목 개수 지정
   - multiple : 여러 개의 옵션이 브라우저 화면에 함께 표시되어 여러 항목 선택 가능
5. option Attribute : value, selected
   - value : 옵션을 선택했을 때 서버로 넘겨질 값 지정
   - selected : 화면에 표시될 때 기본적 선택되어있는 옵션 지정
   
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

6. optgroup 태그
   - 드롭다운 목록에서 여러 항목들을 몇 가지 그룹으로 묶어야 할 경우 사용
   - label 속성을 이용해 그룹의 제목을 붙임

```html
<selected id = "class">
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

1. <input> 요소에서 사용하기 위한 옵션들의 리스트를 미리 정의할 때 사용
2. 사용자가 <input> 요소에 데이터를 입력할 때 미리 정의된 옵션을 드롭다운 리스트로 보여줌으로써 자동완성 기능을 제공
3. id 속성값을 명시하면, 해당 요소에서 미리 정의한 옵션들을 <input> 요소에서 사용
4. 텍스트 필드와 함께 사용하기 때문에 < input > 태그를 함께 사용 (주로 type = "text")
5. < datalist > ~ < /datalist >로 데이터 목록의 시작과 끝을 표시하고, 그 사이 < option > 태그로 각 데이터 옵션 표시

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

1. HTML 양식 속에서 그룹을 만들 수 있음, 즉 폼 요소를 그룹으로 묶는 것을 의미
2. < legend > 요소로 그룹의 설명(이름)을 제공
3. 즉, 하나의 폼 안에서 여러 구역을 나누어 표시하려고 할 때 < fieldset >, < legend > 태그 사용
4. < fieldset > ~ < /fieldset > 태그 사이의 폼들을 하나의 영역으로 묶어 외곽선을 그려주고,
   < legend > 태그는 < fieldset > 태그로 묶은 그룹에 제목을 붙여줌 

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

-----
### button
-----    
 - button 요소 (submit 역할 수행)
 - type : button (단어 그대로 button 역할) [input type = "button"과 동일, javaScript와 연동]

     		javaScript와 연동해 처리할 수 있는 기능으로 많이 사용

 - type : reset (입력한 값을 초기화) [input type = "reset"과 동일]
 - type : submit (입력한 값을 웹 서버에 전송) [input type = "submit"과 동일] (기본값)
   
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

- 입력하는 값이 계산 결과라는 것을 브라우저에게 알려줌
- 스크립트 등에 의해 수행된 계산의 결과나 사용자의 액션에 의한 결과를 나타낼 때 사용
- < output > 태그로 묶인 부분이 일반 텍스트가 아니라 계산의 결과값

```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
  <input type="range" id="b" name="b" value="50" /> +
  <input type="number" id="a" name="a" value="10" /> =
  <output name="result" for="a b"></output>
</form>
```
1. a.value : name 속성이 a인 요소의 값(value)을 정수화
2. b.value : name 속성이 b인 요소의 값(value)을 정수화
3. input oninput = "result.value = parseInt(a.value) + parseInt(b.value)" : a의 값과 b의 값을 더해서 output name 속성이 result인 속성에 저장
4. out name = "이름" for = "output에서 사용할 변수들을 선언"
   
<div align = "center">
<img width="294" alt="20240226_142312" src="https://github.com/sooyounghan/Web/assets/34672301/aa3491ba-8883-4649-99d3-b89864c0c398">
</div>   

-----
### iframe
-----    
1. inline frame의 약자로써 해당 웹 페이지 안에 다른 html 파일을 불러와서 삽입할 수 있는 기능을 제공
2. iframe 태그 src 속성에 삽입할 웹 문서의 경로를 작성
3. width, height 속성을 통해 iframe의 크기를 조절 가능

```html
<iframe name = "inner" src = "http://www.daum.com">다음</iframe>
```

-----
### 추가 정보 필요 : 표를 만드는 태그 / map 태그 / progress 태그 / meter 태그
-----    
