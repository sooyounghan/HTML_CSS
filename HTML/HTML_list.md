-----
### 목록 : 모두 블록 레벨 요소를 만드는 태그
-----
1. 연관 있는 항목(item)들을 나열한 것
2. HTML은 '순서 있는 목록(Unordered List)'과 '순서 있는 목록(Ordered List)'으로 구분

-----
### 순서 없는 목록 태그 : (ul)
-----
1. 정렬되지 않은 목록으로, 불릿(Bullet)으로 표현 (< ul > < /ul >)
2. < ul type = "값" > 명시 가능, ul 안에 또 다른 ul 삽입 가능
3. 속성 : type
   
       <ul>
         <li type = "disc">(Default type)</li>
         <li type = "circle">(원)</li>
         <li type = "square">(사각형) 등 type 지정 가능</li>
       </ul>
   
-----
### 순서 있는 목록 태그 : (ol)
-----
1. 정렬된 목록으로, 보통 숫자목록으로 표현 (< ol > < /ol >)
2. < ol type = "값" > 명시 가능, ol 안에 또 다른 ol 삽입 가능
3. 속성 : start와 reversed
   - start 속성 : 순서 목록은 기본적 1부터 시작, start 속성으로 중간 번호부터 시작 가능
   - reversed 속성 : 항목을 역순으로 표시
4. 속성 : type

        <ol>
          <li type =  "1">(숫자)(Default type)</li>
          <li type = "A">(대문자)</li>
          <li type = "a">(소문자)</li>
          <li type = "I">(로마자 대문자)</li>
          <li type = "i">(로마자 소문자) 등</li>
        </ol>
   
-----
### 항목 태그 : (li)
-----
1. < li > : 목록에 들어가는 항목 하나 하나를 표현할 때 사용 (< li > < / li >)
2. 항목들(< li > 태그들)을 감싸는 태그가 무엇이냐에 따라 기호가 달라짐 (즉, 정렬 목록(<ol>), 비정렬 목록(<ul> 안에 위치)


```html
<!DOCTYPE HTML>
<HTML>
	<HEAD>
		<meta charset = "UTF-8"> 
		<title> Title </title>
	</HEAD>
	<BODY>
			<ul> 
				<li> ul : unordered list : 순서가 없는 목록 (무순서 목록) </li>
			 	<li type = "disc">  </li>
			 	<li type = "circle">  </li>
			 	<li type = "square">  </li>
			</ul>
			<ol>
				<li> ol : ordered list : 순서가 있는 목록 (순서 목록) </li>
				<li type = "1">  </li>
				<ol>
					<li type = "A">  </li>
					<li type = "a">  </li>
					<li type = "I">  </li>
					<li type = "i">  </li>
				</ol>
			</ol>
	</BODY>
</HTML>
```
