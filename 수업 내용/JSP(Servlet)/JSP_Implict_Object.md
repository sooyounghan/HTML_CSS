-----
### 내장 객체
-----   

1. JSP 페이지에서 사용할 수 있도록 JSP 컨테이너에 미리 정의된 객체
   
2. JSP 페이지가 서블릿 프로그램으로 번역될 때 JSP가 자동으로 내장 객체를 멤버 변수, 메서드 매개변수 등의 각종 참조 변수(객체)로 포함

3. 별도의 import문 없이 자유롭게 사용 가능
   
4. 스크립틀릿 태그나 표현문 태그 선언을 하거나 객체 생성하지 않고도 직접 호출 사용 가능
   
<div align = "center">
<img width="389" alt="2134" src="https://github.com/sooyounghan/JAVA/assets/34672301/6796cfc6-ded0-4c5f-bedc-05ff15cbe2cd">
</div>

-----
### request 기본 객체
-----
1. JSP 페이지에서 가장 많이 사용되는 기본 객체로 웹 브라우저의 요청과 관련
2. 웹 브라우저에서 서버의 JSP 페이지로 전달하는 정보 저장
3. JSP 컨테이너는 웹 브라우저에서 서버로 전달되는 정보를 처리하기 위해 javax.servlet.http.HttpServletRequest 객체 타입의 request
   내장 객체를 사용해 사용자의 요구사항을 얻어냄
4. 웹 브라우저는 해당 웹 서버에 연결한 후 요청 정보를 전송하는데, 이 요청 정보를 제공하는 것이 request 기본 객체

   		1. 클라이언트(웹 브라우저)와 관련된 정보 읽기 기능
		2. 서버와 관련된 정보 읽기 기능
		3. 클라이언트가 전송한 요청 파라미터 읽기 가능
		4. 클라이언트가 전송한 요청 헤더 읽기 기능
		5. 클라이언트가 전송한 쿠기 읽기 기능
		6. 속성 처리 기능
5. 주요 메서드
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/13e6c5fc-bfbd-47ca-83ab-096df4cfe80c">
</div> 
- String getRemoteAddr()
 
 	* 웹 서버에 연결한 클라이언트의 IP 주소를 구함 (IPv4형태)
	* 게시판이나 방명록 등 글 작성자의 IP주소가 자동으로 입력되기도 하는데, 이 때의 IP 주소가 이 메서드로 사용하여 구함
	* localhost : IPv6 방식으로 표현

 - long getContentLength()

	   * 클라이언트가 전송한 요청 정보의 길이를 구함
	   * 전송된 데이터의 길이를 알 수 없는 경우 -1

 - String getCharacterEncoding()

	   * 클라이언트가 요청 정보를 전송할 때 사용한 인코딩을 구함

 - String getContentType()

	   * 클라이언트가 요청 정보를 전송할 때 사용한 컨텐츠 타입을 구함

 - String getProtocol()

	   * 클라이언트가 요청한 프로토콜을 구함

 - String getMethod()

	   * 웹 브라우저가 정보를 전송할 때 사용한 방식을 구함

 - String getRequestURI()

	   * jsp 내에서는 /webPro/ch03/request.jsp

  : 웹 브라우저가 요청한 URI에서 경로를 구함

   + URI (Uniform Resource Identifier) : 자원의 위치 뿐 아니라 자원에 대한 고유식별자로서 URL까지 포함 

	A. 인터넷에 있는 자원을 나타내는 유일한 주소.
   	B. 인터넷에 존재하는 각종 정보들의 유일한 이름이나 위치를 표시하는 식별자

   + URL (Uniform Resource Locator) : 웹주소로서, 컴퓨터 네트워크 상에서 리소스가 어디있는지 알려주기 위한 규약
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/54dd8839-e033-483c-9ba7-ce3b257ec224)">
</div>   

<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/13e6c5fc-bfbd-47ca-83ab-096df4cfe80c">
</div> 

 - String getContextPath()
  : JSP 페이지가 속한 웹 어플리케이션의 Context Path를 구함
   + jsp에서는 /webPro
   + ContextPath : 특정 웹 애플리케이션을 가리키는 URL의 일부로 웹 어플리케이션을 구분하기 위한 용도
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/37a5446d-dd24-459d-897d-6af1153e2ef7">
</div> 
	   
    * getServerName()은 곧 서버 이름이지만, 여기서는 IP주소!
 
 - String getServerName()
  : 연결할 때 사용한 서버의 이름을 구함\

 - int getServerPort()
  : J서버가 실행중인 포트 번호를 구함

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		
		<title>request 객체</title>
		
	</head>
	
	<body>
		<h3>request 객체</h3>
		<h3>http://localhost:8081/webPro/ch03/request.jsp</h3>
		<hr>
		<%
			String uri = request.getRequestURI();
			String contextPath = request.getContextPath();
			
			out.print(uri.substring(contextPath.length() + 1));
		%>
		<li> request.getRemoteAddr() : <%=request.getRemoteAddr() %> </li>
		<li> request.getContentLength() : <%=request.getContentLength() %> </li>
		<li> request.getCharacterEncoding() : <%=request.getCharacterEncoding() %> </li>
		<li> request.getContentType() : <%=request.getContentType() %> </li>
		<li> request.getProtocol() : <%=request.getProtocol() %> </li>
		<li> request.getMethod() : <%=request.getMethod() %> </li>
		<li> request.getRequestURI() : <%=request.getRequestURI() %> </li>
		<li> request.getContextPath() : <%=request.getContextPath() %> </li>
		<li> request.getServerName() : <%=request.getServerName() %> </li>
		<li> request.getServerPort() : <%=request.getServerPort() %> </li>
	</body>
</html>
```

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>Link</title>
	</head>
	
	<body>
			<%
				String uri = request.getRequestURI();
				String contextPath = request.getContextPath();
				String path = uri.substring(contextPath.length());
				out.print(path + "</br>");
			%>
			<h4>http://localhost:8081/webPro/ch03/link.jsp</h4>
			<ul>
				<li type = "disc"><a href = "http://localhost:8081/webPro/ch03/request.jsp">request 기본객체 (절대경로)</a> </li>
				<li type = "disc"><a href = "./request.jsp">request 기본객체 (상대경로)</a> </li>
				<li type = "disc"><a href = "<%=request.getContextPath()%>/ch03/request.jsp">request 기본객체 (상대경로의 절대경로화 : request.getContextPath()/ch03/request.jsp)</a> </li>
		</ul>
	</body>
</html>
```

-----
### Context Path 변경
-----
1. Context Path 변경 (Servers - Tomcat - server.xml 진입)
```jsp
...
     <Context docBase="webPro" path="/webPro" reloadable="true" source="org.eclipse.jst.jee.server:webPro"/></Host>
// Context docBase : 현재 진행중 프로젝트 / path : context Path
...
```
   : 현재 Context Path은 /webPro
```jsp
http://localhost:8081/webPro/ch03/link.jsp
// request.getContextPath() : /webPro
```

2. 
```jsp
...
     <Context docBase="webPro" path="/Pro" reloadable="true" source="org.eclipse.jst.jee.server:webPro"/></Host>
// Context docBase : 현재 진행중 프로젝트 / path : context Path
...
```
   : 현재 Context Path는 /Pro
```jsp
http://localhost:8081/pro/ch03/link.jsp
// 진입방법은 위와 같이 context path가 변경되었으므로 pro로 진입해야함
// request.getContextPath() : /pro
```

3. <Context path=" "docBase=" "> 

       A. path 는 URL상의 주소
       B. docBase 는 어플리케이션의 서버상 위치\
          (만일 docBase가 상대경로면 appBase 부터의 상대경로가 되며, 절대경로로 설정되면 서버의 절대경로)

-----
### 요청 파라미터
-----
1. 사용자가 폼 페이지에 데이터를 입력한 후 서버에 전송할 때 전달되는 폼 페이지의 입력된 정보 형태
2. <name = value> 형식으로 웹 브라우저에서 서버의 JSP 페이지로 전달

<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/d507d626-efda-4b03-9d58-2b5e8adcd623">
</div>

-----
### 요청 HTTP 헤더
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/07ddffe9-5415-44f2-ab45-fd87877eb349">
</div>

-----
### 속성 공유 유효 범위
-----
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/64082401-d310-4abc-9794-ff1bbac3b951">
</div>

 * a.jsp를 통해 b.jsp를 요청할 경우?   
     : 이럴 때는, request 영역(결과적으로 클라이언트가 요청한 것은 a.jsp를 통해 b.jsp를 얻는 것이므로)

-----
### response 기본 객체
-----
1. response  내장 객체
	- request 기본 객체와 반대의 기능 수행
	- 웹 브라우저에 보내는 응답 정보를 담음
	- 헤더 정보 입력, 리다이렉트 하기와 같은 기능 제공
	- 사용자의 요청을 처리한 결과를 서버에서 웹 브라우저로 전달하는 정보를 저장하고, 서버는 응답 헤더와 요청 처리 결과
	   데이터를 웹 브라우저로 보냄
	- JSP 컨테이너는 서버에서 웹 브라우저로 응답하는 정보 처리를 위해 javax.servlet.http.HttpServletResponse
	  객체 타입의 내장 객체를 사용해 사용자 요청에 응답

 2. 페이지 이동 (Redirection)
	- 사용자가 새로운 페이지를 요청할 때 같이 페이지를 강제 이동하는 것
	- 서버는 웹 브라우저에 다른 페이지로 강제 이동하도록 redirection 메서드 제공
	- 페이지 이동 시 문자 인코딩을 알맞게 설정해야함
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/db886e28-d96e-47b2-ba4f-2fca5ce4690b">
</div>

```jsp
	<%
		final String FORM_VIEW = "loginForm.jsp"; // Redirect 주소를 상수로 지정
	
		if(request.getMethod().equalsIgnoreCase("GET")) {
			response.sendRedirect(FORM_VIEW); // Redirect을 통해 로그인 폼 페이지로 이동
			// = out.print("<br><a href = 'loginForm.jsp'> 로그인 폼 이동 </a>");
		}
		else if(request.getMethod().equalsIgnoreCase("POST")) {
			out.print(request.getMethod() + " : 로그인 처리 방식으로 이동");
		}
	%>
```

3. 예제 (link_response_sendRedirect.jsp -> a.jsp -> b.jsp)

   		- link_response_sendRedirect.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
	<html>
		<head>
		<meta charset="UTF-8">

		<title>link_response_sendRedirect</title>
		</head>

		<body>
			<a href = "a.jsp" target = "_self">a.jsp</a>
		</body>
</html>
```

   		- a.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
	</head>

	<body>
		<% 
		System.out.print("redirecting");
		response.sendRedirect("b.jsp"); 
		%>
	</body>
</html>
```

		- b.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>Insert title here</title>
	</head>
	
	<body>
		<h3>b.jsp</h3>
	</body>
</html>
```

  - link_response_sendRedirect.jsp에서 name과 age의 값을 전달 -> a.jsp 전달하나 b.jsp에는 전달되지 못함
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
	<html>
		<head>
		<meta charset="UTF-8">

		<title>link_response_sendRedirect</title>
		</head>

		<body>
			<a href = "a.jsp?name=a&age=20" target = "_self">a.jsp</a>
		</body>
</html>
```
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
	</head>

	<body>
		<% 
		System.out.println("redirecting");
		System.out.println(request.getParameter("name"));
		System.out.println(request.getParameter("age"));
		response.sendRedirect("b.jsp");
		<!-- a 20 -->
		%>
	</body>
</html>
```
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>Insert title here</title>
	</head>
	
	<body>
		<%
		System.out.println(request.getParameter("name"));
		System.out.println(request.getParameter("age"));
		<!-- null null -->
		%>
		<h3>b.jsp</h3>
	</body>
</html>
```

<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/836839ae-c4e2-47d8-8c69-5507a5e58926">
</div>


-----
### redirect 방법
-----
1. html
```html
   <a href = "URL" target = "_self">URL</a>
   <a href = "URL" target = "_blank">URL</a>
```

2. javaScript
```javascript
  <span onclick = "location.href = 'URL'"></span>
  <span onclick = "window.open('URL')"></span>
```
```jsp
<jsp:forward = "URL">
- pageContext.forward("URL");
- requestDispatcher rd = request.getRequestDispatcher("URL");
  rd.forward(reqeust, resopnse);
```

	: 위 코드에서 1번은 일반적인 jsp 방식, 2번은 servlet 방식
-----
### 웹 브라우저에 헤더 정보 전송
-----
< 헤더 추가 메서드 >   

	- addDateHeader(String name, long date) : name 헤더에 date 추가 (date : 1970/1/1 이후 흘러간 시간을 1/1000초 단위)
	- addHeader(String name, String value) : name 헤더에 value값 추가
	- addIntHeader(String name, int value) : name 헤더에 정수 값 value 값 추가
	- setDateHeader(String name, long Date) : name 헤더 값을 date로 지정
   	      * setDateHeader는 System.currentTimeMillis 나 Date 객체의 getTime로부터 반환되는 값을 GMT 시간 문자열 변경
	- setHeader(String name, String value) : name 헤더의 값을 value로 저장
	- setIntHeader(String name, int value) : name 헤더의 값을 정수 값 value로 저장
	- containsHeader(String name) : 이름이 name인 헤더를 포함하면 true, 그렇지 않으면 false

-----
### 응답 콘텐츠 관련 메서드
-----
: response 내장 객체는 웹 브라우저 응답을 위해 MIME 유형, 문자 인코딩, 오류 메시지, 상태 코드 등 설정하고 가져오는   
  응답 콘텐츠 관련 메서드 제공
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/5792cc11-c1f0-4954-819d-00cbc8b648cf">
</div>

-----
### 캐시 (Cache)
-----
1. 웹 브라우저 WAS에 a.jsp 실행 요청 후 다시 한 번 a.jsp 실행 요청을 하면, 두 요청 사이에 출력한 결과에 차이가 없다면
   웹 브라우저는 불필요하게 동일한 응답 결과를 두 번 요청
2. 동일한 데이터를 중복해서 로딩하지 않도록 사용
3. 웹 브라우저는 첫 요청 시 응답 결과를 로컬 PC의 임시 보관소인 캐시에 저장하고, 이후 동일 URL에 대한 요청이
   있으면 WAS에 접근하지 않고 로컬 PC에 저장된 응답 결과를 웹 브라우저에 출력
4. 변경이 발생하지 않는 JSP의 응답 결과나 이미지, 정적 HTML 등은 캐시에 보관함으로 웹 브라우저의 속도를 향상시키기 가능

-----
### out 기본 객체
-----
1. 웹 브라우저에 데이터를 전송하는 출력 스트림 객체
2. JSP 컨테이너는 JSP 페이지에 사용되는 모든 표현문 태그와 HTML, 일반 텍스트 등을 out 내장 객체를 통해 웹 브라우저에 그대로 전달
3. 스크립틀릿 태그에 사용하여 단순히 값을 출력하는 표현문 태그와 같은 결과를 얻을 수 있음
<div align = "center">
<img src = "https://github.com/sooyounghan/JAVA/assets/34672301/6c88b74e-d38d-4056-8e23-97d65cfb3d5d">
</div>
