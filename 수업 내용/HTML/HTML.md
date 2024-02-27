-----
### HTML(HyperText Markup Language) 5
-----
1. 웹페이지를 기술하기 위한 마크업 언어
2. 내용(Content) + 구조(Structrue) 담당 언어

```html
<!DOCTYPE html> // HTML5는 <!DOCTYPE html>으로 시작해 문서 형식을 HTML5로 지정

<html> // 실질적인 HTML Document 시작(<html> ~ </html>

    <head> // Document Tile, 외부 파일 참조, 메타데이터 설정 등 위치 (단, 브라우저 표시 X)

     </head>

     <body> // 웹브라우저에 출력되는 모든 요소가 위치
 
     </body>

</html>
```
  - DOCTYPE : 선언된 페이지의 HTML 버전이 무엇인지 웹 브라우저에 알려주는 선언문
  - html : HTML의 루트 요소 정의 (다른 HTML 요소 포함을 위한 컨테이너이며, HTML 문서임을 알려줌)

    		- lang 속성 : 문서에서 사용할 언어를 지정
    		- 예) <html lang = "ko">
    		- <meta> 태그 : 문자 세트 지정 등 사용 (<meta charset = "UTF-8">)
    
  - head : 해당 문서에 대한 정보인 메타데이터의 집합 정의

        * <title>, <style>, <base>, <link>, <meta>, <script>, <noscript>(<body>요소에도 포함 가능)
  - body : HTML의 모든 콘텐츠를 포함하는 영역을 정의
  - 주석(Comment) : 주로 개발자에게 코드를 설명하기 위해 사용되며 브라우저에 미표시

        예) <!--Comment-->

-----
### 상대경로와 절대경로
-----
1. 절대 경로 (모든 주소 작성)

        현재 문서 URL : http://172.30.1.33:8081/webPro/cf/LoginForm.jsp 
        이동 문서 URL : http://172.30.1.33:8081/webPro/cf/Map_Login.jsp 

2. 상대 경로

        . : 현재 Directory
        .. : 상위 Directory
         * 현재 문서 URL : http://172.30.1.33:8081/webPro/cf/LoginForm.jsp 
         * 이동 문서 URL : Map_Login.jsp
              A. ./Map_Login.jsp (.은 현재 디렉토리 = 여기서는 cf Directory)
              B. ../cf/Map_Login.jsp (..은 상위 디렉토리 = 여기서는 webPro)
   
-----
### 제목(Headings) 태그
-----
1. 제목을 나타낼 때 사용
2. h1 ~ h6까지의 태그 존재 (h1이 가장 중요한 제목 의미)

       * 제목 이외에는 사용하지 않는 것이 좋음
```html
<!DOCTYPE HTML>

<html>

  <body>

    <h1> Heading 1 </h1>
    <h2> Heading 2 </h2>
    <h3> Heading 3 </h3> 
    <h4> Heading 4 </h4>
    <h5> Heading 5 </h5>
    <h6> Heading 6 </h6>

</body>

</html>
 

# br : 강제 개행(link break) → empty element로 종료 태그가 없음 (</br> 존재 하지 않음)

<!DOCTYPE html>

<html>

  <body>
     
     <p>This is<br>a para<br>graph with line breaks</p>

   </body>

</html>
```

-----
### p 태그
-----
```html
<!DOCTYPE html>

	<html>
		<body>
			<h1>This is a heading.</h1>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
			<!-- <p>~</p> 후 자동 개행 -->
			<p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
		</body>
	</html>
```
-----
### pre 태그
-----
  - 형식화(Preformatted) text 지정 → pre 태그 내 content는 작성된 그대로 브라우저에 표시

```html
<!DOCTYPE html>
	<html>
	<body>

		<p>HTML은 1개 이상의 연속된 공백(space)과 1개 이상의 연속된 줄바꿈(enter)을 1개의 공백으로 표시한다.</p>

		<pre>
		var myArray = [];
		console.log(myArray.length); // 0

		myArray[1000] = true; // [ , , ... , , true ]
		console.log(myArray.length); // 1001
		console.log(myArray[0]); // undefined
		</pre>
	</body>
	</html>
```
-----
### strong, b
-----
1. < strong > 굵게 강조할 텍스트 < /strong >
2. < b > 굵게 표시할 텍스트 < /b >

-----
### em, i
-----
1. < em > 이탤릭체로 표시할 텍스트 < /em >
2. < i > 이탤릭체로 강조할 텍스트 < /i >

-----
### blockquote, q
-----
1. blockquote : 한 문단이나 내용 전체가 인용문일 때 사용
2. q :  문장 내 들어가는 인용문에 대해 사용 (속성 : cite = "주소")

-----
### mark
-----
: 배경색이 노란색이 되며, 형광펜으로 그어 놓은 듯한 효과

-----
### span
-----
1. 텍스트 단락 안에서 줄 바꿈 없이 일부 텍스트만 묶어서 스타일 적용
2. div : 단락 전체를 묶고 싶을 때 사용
      
-----
### hr
----
: 수평줄 삽입
```html
<!DOCTYPE html>
	<html>	
		<body>
        
		<h1>HTML</h1>
        
		<p>HTML is a language for describing web pages.</p>
        
		<hr>
        
		<h1>CSS</h1>
        
		<p>CSS defines how to display HTML elements.</p>
        
		</body>
</html>
```

-----
### ul, ol, li
-----
1. ul  : unordered list(무순서 목록), 순서가 없는 목록 →  정렬되지 않은 목록을 나타내며, 보통 불릿으로 표현

       * <ul type = ""> 명시 가능
       * <li type = "disc">( Default type ), <li type = "circle">(원),
         <li type = "square">(사각형) 등 type 지정 가능 
2. ol : ordered list(순서 목록), 순서가 있는 목록 → 정렬된 목록을 나타내며,  보통 숫자 목록으로 표현현

       * <ol type = ""> 명시 가능
       * <li type =  "1">(숫자)(Default type), <li type = "A">(대문자),
         <li type = "a">(소문자), <li type = "I">(로마자 대문자), <li type = "i">(로마자 소문자)  등 type 지정 가능 
       * <ol> 안에 또 다른 <ol> 삽입 가능

	- start 속성 : 순서 목록은 기본적 1부터 시작하는데, start 속성 이용해 중간 번호부터 시작 가능
 - 	- reversed 속성 : 항목을 역순으로 표시
    
3. li : 목록의 항목 

       * 반드시 정렬 목록(<ol>), 비정렬 목록(<ul>, 혹은 메뉴(<menu> (en-US)) 안에 위치

4. dt, dl, dd
   	- dl : 제목과 설명이 한 쌍인 설명 목록 (Description List)
   	- dt : 제목 설명 부분
   	- dd : 설명을 표시
   	- 하나의 dt 태그 내 여러 개의 dd 가능, 여러 개의 dt도 가능
```html
<!--  HTML5 Comment -->

<!-- HTML5 버전 문서 타입 선언부 -->
<!DOCTYPE HTML>
<HTML>
	<HEAD>
		<meta charset = "UTF-8"> 
		<title> Title </title>
	</HEAD>
	
	<BODY>
		<h1> hello.html </h1>
		<h2> URL 형식 </h2>
		<h3> http://IP주소(Domain Name/내 IP : LocalHost):포트번호/경로 :디렉토리 </h3>
		<h4> http://IP주소(Domain Name/내 IP : LocalHost):포트번호/컨택스트패스/파일명.확장자 </h4>
		<h5> http://IP주소(또는 Domain Name):8081/webPro/hello.html)</h5>
		<h6> http://localhost:8081/webPor/hello.html </h6>
		
		<hr> <!-- 수평선, 구별 역할 -->
		
		<pre> <!-- Preformatted 태그 -->
		br 태그 : 단순 줄바꿈, 반복 / p 태그 : 문단, p 요소 앞뒤로 빈 줄 삽입
		</pre>
		
		<hr><!-- 수평선, 구별 역할 -->
			<ul> 
				<li> ul : unordered list : 순서가 없는 목록 (무순서 목록) </li>
			 	<li type = "disc"> Frontend - HTML, CSS, JavaScipt, jQuery, Ajax, JSON 등 </li>
			 	<li type = "circle"> Backend - Java, JSP/Servlet </li>
			 	<li type = "square"> DBMS - Oracle, MySQL, MariaDB 등 </li>
			</ul>
			<ol>
				<li> ol : ordered list : 순서가 있는 목록 (순서 목록) </li>
				<li type = "1"> 요구사항 개발 프로세스 </li>
				<ol>
					<li type = "A"> 요구사항 도출 </li>
					<li type = "a"> 요구사항 분석 </li>
					<li type = "I"> 요구사항 명세 </li>
					<li type = "i"> 요구사항 확인 </li>
				</ol>
			</ol>
		
		
		Hello<br><br><br> : <!-- <br></br> = </br> --> 사이에는 비어있음 (EmptyTag) 
		
		HTML : HyperText Markup Language 
		(웹 문서의 내용, 골격 담당)
		
		<p> XML - eXtensible Markup Language (확장가능한 마크업 언어로, 작은 DB역할 (데이터 역할)) </p>
		    - 다른 언어들과 연동(다른 언어에 종속되지 않음)하며, 주로 환경 설정용으로 많이 사용
	</BODY>
</HTML>
```

-----
### a
-----
1. 하이퍼링크를 걸어주는 태그
2. Attribute : href(클릭 시 이동할 경로)
3. Attribute : target
   - target = "_blank"는 기본속성 중 하나로 클릭시 계속해서 새로운 창이 열리게 됨
   - target = "blank"(="_self") 는 클릭하면 한번 열린 탭에서(새로운 탭이 열리는 것 X) 계속 새로운 페이지가 열림 
4. a 태그 뒤에 img 태그 삽입 가능

```html
<a href = "주소"><img src ="경로"> </a>
```

5. 앵커 기능
```html
<태그 id = "앵커 이름"> 텍스트 또는 이미지 </태그>
<a href = "#앵커 이름"> 텍스트 또는 이미지 </a>
```
```html
<ul id = "menu">
	<li><a href = "#content1">메뉴1</a></li>
</ul>

<h2 id = "content1">내용1</h2>
<p><a href = "#menu">[메뉴로]</a></p>
```

```html
<a href = "https://www.w3schools.com/html/html_forms.asp" target = "_blank"> form 참고 </a>
```
```html
<html>

	<head>
		<meta charset="UTF-8">
		<title> HashTable을 이용한 로그인 구현 </title>
	</head>

	<body>
		<h3> 프로토콜://IP주소(도메인네임):Port번호/Context Path/파일명.확장자 (= 프로토콜://IP주소(도메인네임):Port번호/Directory(경로))</h3>
		<h3> http://172.30.1.33:8081/webPro/cf/Map_Login.jsp </h3>
		
		<h2> Login 처리 화면 </h2>
		<a href = "http://172.30.1.33:8081/webPro/cf/LoginForm.jsp"> 로그인 페이지로 이동 (절대 경로) </a> <br>
		<a href = "LoginForm.jsp"> 로그인 페이지로 이동 (상대 경로 1) </a> <br>
		<a href = "./LoginForm.jsp"> 로그인 페이지로 이동 (상대 경로 2) </a> <br>
		<a href = "../cf/LoginForm.jsp"> 로그인 페이지로 이동 (상대 경로 3) </a> <br>
	</body>
	
</html>
```
-----
### xmp
-----
: html 태그를 실행안하고 문장 소스 그대로 보여주는 태그
```html
		<xmp>
			<a href = ""> Text 또는 이미지 등 가능한 형태 </a> // 태그 무시하고 그대로 출력
		</xmp>
		
		<h2> 로그인 화면(LoginForm.jsp) </h2>
		<pre> 
			절대 경로
			현재 문서 URL : http://172.30.1.33:8081/webPro/cf/LoginForm.jsp 
			이동 문서 URL : http://172.30.1.33:8081/webPro/cf/Map_Login.jsp
		</pre>
		
		<a href = "http://172.30.1.33:8081/webPro/cf/Map_Login.jsp"> Map_Login</a> // href에 지정한 주소로 이동하며, Map_Login에 링크가 걸림
```

-----
### img
-----
1. img 태그 : 웹 문서 상 이미지 삽입 (< img src = "경로" [속성 = 값] >
2. src 속성 : 이미지 파일 경로 지정 (웹 문서 파일의 위치를 기준으로 시작)
3. 웹 상의 이미지는 이미지 주소 복사로 가능
4. alt 속성 : 이미지를 설명하는 대체 텍스트를 삽입할 때 사용
	- 연결 속도가 느리거나 이미지가 제대로 표시가 되지 않는 상황에서 유용
	- Bullet 이미지나 작은 아이콘의 경우는 alt =""로 지정
5. width, height 속성 : 원하는 너비와 높이로 지정

-----
### figure
-----
1. figure 태그 : 설명 글을 붙일 대상 지정
	- 웹 문서 안에서 한 단위가 되는 요소를 묶을 때 사용
	- 한 단위가 되는 요소를 나타내기 위해 사용
	- 설명 글을 사용하기 위해서는 < figure > 태그 안에 < figcaption > 태그로 설명 글 표시
2. figcaption : 설명 글 붙이기

```html
<figure>
	<img src = "/pic.jpg" alt = "사진">
	<figcaption>사진</figcaption>
</figure>
```
-----
### Query String
-----
1. 사용자가 입력 데이터를 전달하는 방법중의 하나로, url 주소에 미리 협의된 데이터를 파라미터를 통해 넘기는 것
2. = 로 key 와 value 가 구분 (key = value)
3. 형식 
    - 정해진 엔드포인트 주소 이후에 ?를 쓰는것으로 쿼리스트링이 시작함
    - parameter=value가 필요한 파라미터의 값
    -  파라미터가 여러개일 경우 &를 붙여 여러개의 파라미터를 넘기기 가능

           엔드포인트주소/엔드포인트주소(서버 측의 페이지)?파라미터명(변수)=값&파라미터명=값

-----
### 요청 파라미터 값 받기
-----
1. request 내장 객체는 웹 브라우저가 서버로 보낸 요청에 대한 다양한 정보를 담고 있음
2. [단일 파라미터 조회]
  - getParameter() 메서드를 통해 요청 파라미터의 값을 얻을 수 있음 (Return type : String) <- Query String

        String getParameter("parameter_name"); (매개변수명에 문자열으로 들어가야함 주의!)
```html
			<HTML>
아이디  : <input type = "text" name = "user_id" value = "ID"><br>
비밀번호 : <input type = "password" name = "user_pw" value = "1234"><br><br>
            
            <reques page - JSP>
String id = request.getParameter("user_id") // get 방식으로 넘어오는 데이터를 request 내장 객체의 getParameter() 메서드를 통해 ID 저장
String password = request.getParameter("user_pw") // get 방식으로 넘어오는 데이터를 request 내장 객체의 getParameter() 메서드를 통해 Password 저장
```

3. [이름이 중복되는 파라미터 조회]

       String[] request.getParameterValues("parameter_name")

  - 이러한 경우, getParameter("parameter_name")을 사용하면, request.getParameterValues("parameter_name")의 첫번째값 반환

   ```html
    <%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>

<!DOCTYPE html>

<html>

	<head>
		<meta charset="UTF-8">
		<title> 로그인 화면 </title>
	</head>

	<body>
		<xmp>
			<a href = ""> Text 또는 이미지 등 가능한 형태 </a>
		</xmp>
		
		<h2> 로그인 화면(LoginForm.jsp) </h2>
		
		<form name = "Login Form" action = "./Map_Login.jsp", method = "get">
			아이디  : <input type = "text" name = "user_id" value = "ID" required = "required"><br>
			비밀번호 : <input type = "password" name = "user_pw" value = "1234" required = "required"><br><br>
			<input type = "submit" value = "로그인">
			<input type = "reset" value = "취소">
		</form>
		<br>
		<hr>
		<br>
		
		<pre> 
			절대 경로
			현재 문서 URL : http://172.30.1.33:8081/webPro/cf/LoginForm.jsp 
			이동 문서 URL : http://172.30.1.33:8081/webPro/cf/Map_Login.jsp
			
			상대 경로
			- . : 현재 Directory
			- .. : 상위 Directory
			현재 문서 URL : http://172.30.1.33:8081/webPro/cf/LoginForm.jsp 
			이동 문서 URL : 1. Map_Login.jsp
			              2. ./Map_Login.jsp (.은 현재 디렉토리 = 여기서는 cf Directory)
			              3. ../cf/Map_Login.jsp (..은 상위 디렉토리 = 여기서는 webPro)
		</pre>
		<hr>
		
		<a href = "http://172.30.1.33:8081/webPro/cf/Map_Login.jsp"> 절대 경로 : Map_Login</a> <br>
		
		<a href = "Map_Login.jsp"> 상대 경로 1 : Map_Login</a> <br>
		<a href = "./Map_Login.jsp"> 상대 경로 2  : Map_Login</a><br>
		<a href = "../cf/Map_Login.jsp"> 상대 경로 3 : Map_Login</a>
	</body>
	
</html>

```html
<%@ page import="java.util.*"%> <!-- Map, Scanner를 위한 Package import -->
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>

<html>

	<head>
		<meta charset="UTF-8">
		<title> 로그인 구현 </title>
	</head>

	<body>
		<h2> Login 처리 화면 </h2>
		
		<!-- html 주석문 -->
		<%-- jsp 주석문 
			1. Client의 Data를 입력한 내용을 받아서 처리하는 서버측 페이지
		    2. Client가 전송한 Data를 받아 회원 정보를 비교한 후 결과 출력--%>
		
		<% // Login 처리 코드
			Map<String, String> user = new Hashtable<String, String>();
		
			user.put("aid", "123");
			user.put("bid", "1234");
			user.put("cid", "12345");
			user.put("did", "123456");
			
			String id = request.getParameter("user_id"); // get 방식으로 넘어오는 데이터를 request 내장 객체의 getParameter() 메서드를 통해 ID 저장
			String password = request.getParameter("user_pw"); // get 방식으로 넘어오는 데이터를 request 내장 객체의 getParameter() 메서드를 통해 Password 저장
				
			if(id.equals("")) { // ID 미입력
				out.print("아이디를 입력하지 않았습니다. ");
				out.print("다시 아이디를 입력해주시길 바랍니다. ");
			}
			
			else {
				if(user.containsKey(id)) { // ID가 존재하는 경우
					if(password.equals("")) { // 비밀번호를 입력하지 않은 경우
						out.print("비밀번호를 입력하지 않았습니다. "); 
						out.print("다시 입력해주시길 바랍니다. ");
					}
					
					else { // 비밀번호 입력한 경우
						if(user.get(id).equals(password)) { // ID와 비밀번호가 일치하는 경우
							out.print("로그인에 성공했습니다. ");
						}
						
						else if(!password.equals(user.get(id))){ // 비밀번호가 일치하지 않는 경우
							out.print("로그인에 실패했습니다. ");
							out.print("사유 : 비밀번호가 틀립니다.");
						}
					}
				}
				
				else if(!user.containsKey(id)){ // ID가 없는 경우
					out.print("로그인에 실패했습니다. ");
					out.print("사유 : ID가 존재하지 않거나 틀립니다.");
				}
			}
		%>

		<h3> 프로토콜://IP주소(도메인네임):Port번호/Context Path/파일명.확장자 (= 프로토콜://IP주소(도메인네임):Port번호/Directory(경로))</h3>
		<h3> http://172.30.1.33:8081/webPro/cf/Map_Login.jsp </h3>
		
		<a href = "http://172.30.1.33:8081/webPro/cf/LoginForm.jsp"> 로그인 페이지로 이동 (절대 경로) </a> <br>
		<a href = "LoginForm.jsp"> 로그인 페이지로 이동 (상대 경로 1) </a> <br>
		<a href = "./LoginForm.jsp"> 로그인 페이지로 이동 (상대 경로 2) </a> <br>
		<a href = "../cf/LoginForm.jsp"> 로그인 페이지로 이동 (상대 경로 3) </a> <br>
	</body>
	
</html>
```
