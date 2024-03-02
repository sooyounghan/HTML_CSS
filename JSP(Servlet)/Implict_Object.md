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
### request 기본 객체
-----
1. JSP 페이지에서 가장 많이 사용되는 기본 객체로 웹 브라우저의 요청과 관련
2. 웹 브라우저에서 서버의 JSP 페이지로 전달하는 정보 저장
3. JSP 컨테이너는 웹 브라우저에서 서버로 전달되는 정보를 처리하기 위해 javax.servlet.http.HttpServletRequest 객체 타입의 request
   내장 객체를 사용해 사용자의 요구사항을 얻어냄
4. 웹 브라우저는 해당 웹 서버에 연결한 후 요청 정보를 전송하는데, 이 요청 정보를 제공하는 것이 request 기본 객체

       - 클라이언트(웹 브라우저)와 관련된 정보 읽기 기능
       - 서버와 관련된 정보 읽기 기능
       - 클라이언트가 전송한 요청 파라미터 읽기 가능
       - 클라이언트가 전송한 요청 헤더 읽기 기능
       - 클라이언트가 전송한 쿠기 읽기 기능
       - 속성 처리 기능
   
6. 주요 메서드
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
