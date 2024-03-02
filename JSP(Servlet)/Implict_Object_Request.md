-----
### 내장 객체
-----   

1. JSP 페이지에서 사용할 수 있도록 JSP 컨테이너에 미리 정의된 객체
2. JSP 페이지가 서블릿 프로그램으로 번역될 때 JSP가 자동으로 내장 객체를 멤버 변수, 메서드 매개변수 등의 각종 참조 변수(객체)로 포함
3. 별도의 import문 없이 자유롭게 사용 가능   
4. 스크립틀릿 태그나 표현문 태그 선언을 하거나 객체 생성하지 않고도 직접 호출 사용 가능
   
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/6796cfc6-ded0-4c5f-bedc-05ff15cbe2cd">
</div>

-----
### JSP 기본 객체의 속성 사용
-----
1. 기본 객체가 존재하는 동안은 기본 객체 속성 사용 가능 (정보 공유 목적)
2. 속성은 <속성이름, 값>의 형태

<div align = "center">
<img src= "https://github.com/sooyounghan/Web/assets/34672301/b64fecd1-3b8b-47f6-a550-6f66db2e6642">
</div>

3. 속성의 값의 반환 타입은 Object 이므로 형 변환 필요

-----
### JSP 기본 객체와 영역
-----
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/64082401-d310-4abc-9794-ff1bbac3b951">
</div>

1. page 영역 : 한 번의 클라이언트 요청에 대해서 하나의 JSP 페이지를 범위로 가짐
 
2. request 영역 : 한 번의 웹 브라우저의 요청과 관련
   - 웹 브라우저가 웹 서버에 전송하는 하나의 요청이 request 영역
   - 웹 브라우저의 요청을 보낼 때 마다 새로운 request 영역 생성
   - 하나의 요청을 처리하는데 사용되는 모든 JSP페이지를 포함

3. session 영역 : 하나의 웹 브라우저와 관련된 영역
    - 한 웹 브라우저와 관련된 모든 요청은 이 영역에 포함
  
4. application 영역 : 하나의 웹 어플리케이션과 관련된 전체 영역
   
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b4884425-7833-4994-9e91-047db1df0e6f">
</div>

-----
### Query String
-----
1. 사용자가 입력 데이터를 전달하는 방법중의 하나
2. URL 주소에 미리 협의된 데이터를 파라미터를 통해 넘기는 것
3. = 로 key 와 value 가 구분 (key = value)
4. 형식 
    - 정해진 엔드포인트 주소 이후에 ?를 쓰는것으로 쿼리스트링이 시작함
    - parameter=value가 필요한 파라미터의 값
    -  파라미터가 여러개일 경우 &를 붙여 여러개의 파라미터를 넘기기 가능

           엔드포인트주소/엔드포인트주소(서버 측의 페이지)?파라미터명(변수)=값&파라미터명=값
       
-----
### URL과 URI
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/54dd8839-e033-483c-9ba7-ce3b257ec224)">
</div>   

1. URI (Uniform Resource Identifier) : 자원의 위치 뿐 아니라 자원에 대한 고유식별자로서 URL까지 포함 

  	   A. 인터넷에 있는 자원을 나타내는 유일한 주소.
   	   B. 인터넷에 존재하는 각종 정보들의 유일한 이름이나 위치를 표시하는 식별자

2.  URL (Uniform Resource Locator) : 웹주소로서, 컴퓨터 네트워크 상에서 리소스가 어디있는지 알려주기 위한 규약

-----
### request 내장 객체
-----
1. JSP 페이지에서 가장 많이 사용되는 기본 객체로 웹 브라우저의 요청과 관련
2. 웹 브라우저에서 서버의 JSP 페이지로 전달하는 정보 저장
3. JSP 컨테이너는 웹 브라우저에서 서버로 전달되는 정보를 처리하기 위해 javax.servlet.http.HttpServletRequest 객체 타입의 request 내장 객체를
   사용해 사용자의 요구사항을 얻어냄
4. 웹 브라우저는 해당 웹 서버에 연결한 후 요청 정보를 전송하는데, 이 요청 정보를 제공하는 것이 request 기본 객체
5. request의 범위 : 요청을 받은 request의 범위까지 유지

       - 클라이언트(웹 브라우저)와 관련된 정보 읽기 기능
       - 서버와 관련된 정보 읽기 기능
       - 클라이언트가 전송한 요청 파라미터 읽기 가능
       - 클라이언트가 전송한 요청 헤더 읽기 기능
       - 클라이언트가 전송한 쿠기 읽기 기능
       - 속성 처리 기능

-----
### request 내장 객체 Paramter Method
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/d507d626-efda-4b03-9d58-2b5e8adcd623">
</div>

1. 단일 파라미터 조회 : String getParameter("parameter_name")
  : 요청 파라미터의 값을 얻을 수 있음

<예제 : 아이디와 비밀번호를 JSP에서 request를 통해 받아오기>

```html
<form action = "/login.ok" method = "get" name = "login" id = "login">
	아이디  : <input type = "text" name = "user_id" value = "ID"><br>
	비밀번호 : <input type = "password" name = "user_pw" value = "1234"><br>
	<input type = "submit" value = "로그인">
	<input type = "reset" value = "취소">
</form>
```
```jsp
<%
String id = request.getParameter("user_id") // get 방식으로 넘어오는 데이터를 request 내장 객체의 getParameter() 메서드를 통해 ID 저장
String password = request.getParameter("user_pw") // get 방식으로 넘어오는 데이터를 request 내장 객체의 getParameter() 메서드를 통해 Password 저장
%>
ID : <%=id>, PassWord : <%=password>
```

2. 파라미터의 다중 값 조회 :  String[] getParameterValues("parameter_name")
   - 요청 파라미터의 여러 값을 얻어올 수 있음
   - getParameter("parameter_name") 메서드를 사용하게 되면, request.getParameter("parameter_name")의 첫번째 값만 얻어옴

3. 파라미터의 이름 목록 조회 : Enumeration getParameterNames()

4. 파라미터의 맵 조회 : Map getParameterMap()
   - 맵은 <파라미터 이름, 값> 쌍으로 구성
   
-----
### request 내장 객체 주요 Method
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/13e6c5fc-bfbd-47ca-83ab-096df4cfe80c">
</div> 

<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/37a5446d-dd24-459d-897d-6af1153e2ef7">
</div> 
	   
1. String getRemoteAddr()
 
 	   * 웹 서버에 연결한 클라이언트의 IP 주소를 구함 (IPv4형태) / localhost : IPv6 방식으로 표현
	   * 게시판이나 방명록 등 글 작성자의 IP주소가 자동으로 입력되기도 하는데, 이 때의 IP 주소가 이 메서드로 사용
	   
2. long getContentLength()

	   * 클라이언트가 전송한 요청 정보의 길이
	   * 전송된 데이터의 길이를 알 수 없는 경우 -1

3. String getCharacterEncoding()

	   * 클라이언트가 요청 정보를 전송할 때 사용한 인코딩

4. String getContentType()

	   * 클라이언트가 요청 정보를 전송할 때 사용한 컨텐츠 타입

5. String getProtocol()

	   * 클라이언트가 요청한 프로토콜

6. String getMethod()

	   * 웹 브라우저가 정보를 전송할 때 사용한 방식

7. String getRequestURI()
  : 웹 브라우저가 요청한 URI에서 경로

	   * JSP : /webPro/ch03/request.jsp

8. String getContextPath()
  : JSP 페이지가 속한 웹 어플리케이션의 Context Path

	   * JSP : /webPro
   	   * ContextPath : 특정 웹 애플리케이션을 가리키는 URL의 일부로 웹 어플리케이션을 구분하기 위한 용도

10. String getServerName()

	- 연결할 때 사용한 서버의 이름
   	- 일반적으로 IP주소를 의미
     
10. int getServerPort()
   : 서버가 실행중인 포트 번호를 구함

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
   <head>
   <meta charset="UTF-8">
   <title>request 객체</title>
   </head>
	
   <body>
   <h3>request 객체</h3>
	<%
	String uri = request.getRequestURI();
	String contextPath = request.getContextPath();
```

------
### 간단한 회원 가입 Form을 요청을 통한 Request 객체 이용
------
< 회원가입 Form >
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<body>
<h2 align = "center"> 회원 가입 </h2>
<form action = "/RequestJoinProc.jsp" method = "post">
	<table border = "1" align = "center">
		<tr height = "50">
			<td width = "150" align = "center"> 아이디 </td>
			<td width = "150" align = "center"> <input type = "text" name = "id" size = "40"> </td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 비밀번호 </td>
			<td width = "150" align = "center"> <input type = "password" name = "pwd" size = "40"> </td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 비밀번호 확인 </td>
			<td width = "150" align = "center"> <input type = "password" name = "pwd_check" size = "40"> </td>
		</tr>			
		<tr height = "50">
			<td width = "150" align = "center"> E-mail </td>
			<td width = "150" align = "center"> <input type = "email" name = "email" size = "40"> </td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 전화번호 </td>
			<td width = "150" align = "center"> <input type = "tel" name = "tel" size = "40"> </td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 당신의 관심 분야 </td>
			<td width = "150" align = "center"> 
				<input type = "checkbox" name = "interest" size = "40" value = "캠핑"> 캠핑
				<input type = "checkbox" name = "interest" size = "40" value = "수영"> 수영
				<input type = "checkbox" name = "interest" size = "40" value = "독서"> 독서
				<input type = "checkbox" name = "interest" size = "40" value = "영화"> 영화 
			</td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 나이대</td>
			<td width = "150" align = "center"> 
				<input type = "radio" name = "age" size = "40" value = "20"> 20대
				<input type = "radio" name = "age" size = "40" value = "30"> 30대
				<input type = "radio" name = "age" size = "40" value = "40"> 40대
				<input type = "radio" name = "age" size = "40" value = "50"> 50대 
			</td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 당신의 직업은? </td>
			<td width = "150" align = "center"> 
				<select name = "job">
					<option value = "teacher">교사</option>
					<option value = "lawer">변호사</option>
					<option value = "doctor">의사</option>
				</select>
			</td>
		</tr>
		<tr height = "50">
			<td colspan = "2" width = "150" align = "center"> 
				<input type = "submit" name = "submit" value = "가입">
				<input type = "reset" name = "reset" value = "취소">
			</td>
			<td></td>
		</tr>
	</table>
</form>
</body>
</html>
```
< Login 처리 폼 >
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>

<body>
	<%
	String id = request.getParameter("id");
	String pwd = request.getParameter("pwd");
	String pwd_check = request.getParameter("pwd_check");
	String email = request.getParameter("email");
	String tel = request.getParameter("tel");
	
	String[] hobby = request.getParameterValues("interest");
	String job = request.getParameter("job");
	String age = request.getParameter("age");
	

	if(!pwd.equals(pwd_check)) {
	%>
	<script type = "text/javascript"> // javaScript 영역
		alert("비밀번호가 틀립니다."); // 경고창
		history.go(-1); // 이전 페이지로 이동
	</script>
	<%
	}
	%>
	
	<table width = "400" border = "1">
		<tr height = "50">
			<td width = "150" align = "center"> 아이디 </td>
			<td width = "150" align = "center"> <%=id %> </td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> E-mail </td>
			<td width = "150" align = "center"> <%=email %> </td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 전화번호 </td>
			<td width = "150" align = "center"> <%=tel %> </td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 당신의 관심 분야 </td>
			<td width = "150" align = "center"> 
				<%
				for(int i = 0; i < hobby.length; i++) {
				%>
				<%=hobby[i] %>
				<%
				}
				%>
			</td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 나이대</td>
			<td width = "150" align = "center"> <%=age %>
			</td>
		</tr>
		<tr height = "50">
			<td width = "150" align = "center"> 당신의 직업은? </td>
			<td width = "150" align = "center"> <%=job %>
			</td>
		</tr>
		</table>
</body>
</html>
```
-----
### request 기본 객체의 Header 관련 메서드
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/07ddffe9-5415-44f2-ab45-fd87877eb349">
</div>

1. 지정한 이름의 헤더 값 : String getHeader(String name)
2. 지정한 이름의 헤더 목록 : Enumeration getHeaders(String name)
3. 모든 헤더의 이름 목록 : Enumeration getHeaderNames()
4. 지정한 헤더의 값을 정수 값 : int getIntHeader(String name)
5. 지정한 헤더 값을 시간 값 : long getDateHeader(String name)
6. 모든 쿠기 값을 가져옴 : Cookies[] getCookies()
