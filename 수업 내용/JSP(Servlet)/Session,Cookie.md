 -----
### Session
-----

1. 클라이언트와 웹 서버 간 상태를 지속적 유지
2. 웹 서버만에서만 접근 가능하므로 보안 유지에 유리, 데이터 저장에 한계가 없음
3. 오직 웹 서버에만 존재하는 객체
4. 웹 브라우저마다 하나씩 존재하므로 웹 서버의 서비스를 제공받는 사용자를 구분하는 단위가 됨
5. 웹 브라우저를 닫기 전까지 웹 페이지를 이동하더라도 사용자의 정보가 웹 서버에 보관되어 있어 정보를 잃지 않음

<div align = "center" >
<img src = "https://github.com/sooyounghan/Web/assets/34672301/f63dbea0-3390-4f28-90e0-3bb05c65189b">
</div>

6. Session 메서드
<div align = "center" >
<img src = "https://github.com/sooyounghan/Web/assets/34672301/41115fb1-6975-4bb6-a365-ffcd525ce680">
</div>

-----
### Session 생성
-----

< setAttribute >

      void setAttribute(String name, Object value)
      
1. session 내장 객체의 setAttribute() 메서드 사용 [MVC에서 Model 역할]
2. 세션의 속성을 설정하면 계속 세션 상태 유지 가능
3. 동일한 세션 속성 이름으로 세션을 생성하면, 마지막에 설정한 것이 세션 속성 값
    - name : 세션에서 사용할 세션 속성의 이름, 세션에 저장된 특정한 값 찾아오기 위한 키로 사용
    - value : 세션의 속성값 (Object 타입으로, 형변환 필요)

          session.setAttribute("memberId", "admin");

< getAttribute >

1. 세션에 저장된 하나의 세션 속성 이름에 대한 속성 값 가져오기
2. 반환 타입은 Object형이므로 형변환 필요

          Object getAttribute(String name)
   
3. name은 속성 이름 / 해당 속성에 이름이 없는 경우 null 반환

5. 다중 세션 정보 얻기
   - 세션에 저장된 여러 개 세션 속성 이름에 대한 속성 값을 얻기 위해 getAttributeNames()
   - 반환 타입 : Enumeration 객체 타입

  
-----
### Session 유효 시간 설정
-----
1. 세션 유지를 위한 세션의 일정 시간
2. 웹 브라우저에 마지막 접근 시간부터 일정 시간 이내 다시 웹 브라우저에 접근하지 않으면 자동 세션 종료
3. 세션 유효 시간 설정

         void setMaxInactiveInterval(int interval)
         - interval : 세션 유효 시간
         - 세션 유효 시간 기본값 : 1,800초 (초 단위 설정)
         - 예) session.setMaxInactiveInterval(60 * 60)

4. 세션 유효 시간이 음수이면, 세션 유효 시간이 없는 상태
   (세션 삭제했을 때, session.invalidate()를 호출하지 않으면, 세션 속성이 웹 서버에서 제거 되지 않고 유지)
5. session.invaildate() 메서드를 명시적으로 실행하지 않으면, 이 세션 떄문에 메모리 부족현상 발생 가능

-----
### 로그인 간단 구현
-----
1. Login Form
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
	<html>
	<head>
		<meta charset="UTF-8">
		<title> 로그인 </title>
	</head>

	<body>
		<a href = "<%=request.getContextPath()%>/index.jsp">Index</a>
		<!--  Model 내용 : ${errMSG} --> <br>
		<%
		if(request.getAttribute("errMSG") != null) {
			out.print((String)request.getAttribute("errMSG"));
			out.print("<br>");			
		}
		 %>
		<fieldset style = "width:400px;height:150px">
		<legend> Login </legend>
		<form action = "<%=request.getContextPath() %>/ch10/loginOk.jsp" method = "post" id = "loginForm" name = "loginForm">
		
		<div>
			<div>
			아이디 <input type = "text" id = "id" name = "id" value = "">
			</div>
			<div>
			비밀번호 : <input type = "password" id = "password" name = "password">
			</div>		
			<div>
			<input type = "submit" name = "submit" value = "Login">
			<input type = "reset" name = "reset" value = "Cancel">
			</div>
			
		</form>
		</fieldset> 
	</body>
</html>
```

2. LoginOk
```jsp
<%@ page import = "java.util.*, java.text.*" %>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>Insert title here</title>
	</head>

	<body>
		<a href = "<%=request.getContextPath()%>/index.jsp">Index</a>
		<h4> Client가 보낸 ID, PW을 받아 처리하는 Server 측 페이지 </h4>
		<%
			// MVC 패턴 : Client - 요청(Request) - Sever (Server는 요청에 따라 Business Logic 수행) : Controller 호출
			// Controller의 역할
			//	1. getParameter
			String id = (String)request.getParameter("id");
			String pwd = (String)request.getParameter("password");
			//  2. 비즈니스 로직 수행 (Service <>-> DAO <>-> DB) [회원 DB의 ID를 java / PW를 qwert라 하고, 이를 모두 만족하면 세션에 정보를 저장]
			// 둘중 하나라도 불일치하면, ID 또는 PWD가 불일치함을 표시
			String db_id = "java";
			String db_pwd = "qwert";

			//	3. Model - Session 이용
			if(db_id.equals(id) && db_pwd.equals(pwd)) {
				session.setAttribute("AUTH_USER_ID", (String)request.getParameter("id"));
				session.setAttribute("AUTH_USER_PWD", (String)request.getParameter("password")); // Session에서 비밀번호를 포함하지 않는 것이 웹 보안 관행
			%>
			<ol>
 			<li> session에 저장된 ID : <%=session.getAttribute("AUTH_USER_ID") %></li>
 			<li> <%=session.getAttribute("AUTH_USER_ID")%>님 <a href = "<%=request.getContextPath() %>/index.jsp">Log-out</a></li> <!-- ../index.jsp -->
 			</ol>
			<% 
			} 	
			else {
				//	3. Model - request 이용
				//	4. View 지정
				request.setAttribute("errMSG", "ID or PassWord Mismatch");
				RequestDispatcher rd = request.getRequestDispatcher("loginForm.jsp"); // 2번. forward : 본래 요청 주소 존속 (요청 주소 : loginForm.jsp)
				rd.forward(request, response);
				System.out.println(request.getAttribute("errMSG"));

				// redirect의 경우 model은 session으로 전달 
				//session.setAttribute("errMSG", "ID or PassWord Mismatch");
				//response.sendRedirect(request.getContextPath()+"/ch10/loginForm.jsp"); //1번. redirect : 본래 요청 주소 소멸  마지막 응답 주소 (주소 : loginForm.jsp)
			}
			
			long ct = session.getCreationTime();
			Date session_date = new Date(ct);
			SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");		
	 	%>
 		<ul>
 			<li> session ID 출력 : <%=session.getId() %></li>
 			<li> session 생성 시간 : <%=session.getCreationTime() %></li>
 			<li> session 생성 시간 : <%=session_date %></li>
 			<li> session 생성 시간 : <%=sdf.format(session_date) %></li>
 			<li> session 접근 시간 : <%=sdf.format(new Date(session.getLastAccessedTime())) %> </li>
 			<li> request ID : <%=request.getParameter("id") %>
 		</ul>
 		
	</body>
</html>
```

3. LogOut
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
		session.invalidate(); // session의 정보를 유지하고 싶지 않다면 실행 (로그아웃 의미에서는 이 부분이 반드시 포함)
		RequestDispatcher rd = request.getRequestDispatcher("/index.jsp");
		rd.forward(request, response);
		out.print("Log-Out");
		%>	
		<h4>로그아웃 기능 구현을 담당하는 LogoutHandler 작업</h4>
	</body>
</html>
```

4. Main
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
	<%-- 로그인 전 화면 --%>
	<%
		if(session.getAttribute("AUTH_USER_ID") == null) {
	%>	
		<h1>Main Page(index.jsp)</h1>
		http://localhost:8081<%=request.getContextPath()%>/index.jsp
		<ul>
			<li><a href = "<%=request.getContextPath()%>/ch10/loginForm.jsp">로그인 폼</a></li>
			<li><input button = "button" value = "회원가입" id = "user_join"></li>
		</ul>	
	<%
		} else {
	%> 
	<%-- 로그인 후 화면 --%>
			<li><%=(String)session.getAttribute("AUTH_USER_ID")%>님 어서오세요.
			<%=request.getContextPath() %>
			<a href = "<%=request.getContextPath()%>/ch10/logOut.jsp">Log-out</a></li>
	<%
		}
	 %>
	</body>
</html>
```

 -----
### Cookie
-----
1. 클라이언트와 웹 서버 간 상태를 지속적 유지하는 방법
2. 쿠키는 세션과 달리 정보를 웹 서버가 아닌 클라이언트에 저장

   		예) 웹 사이트를 처음 방문한 사용자가 로그인 인증을 하고 나면, 아이디/비밀번호를 기록한 쿠키 생성
   		    그 다음부터 사용자가 그 웹 사이트에 접속하면 별도의 절차를 거치지 않고 쉽게 접속할 수 있음

3. 장점 : 클라이언트의 일정 폴더에 정보를 저장하므로 웹 서버의 부하를 줄일 수 있음
4. 단점 : 웹 브라우저가 접속했던 웹 사이트에 대한 정보의 개인정보가 기록되므로 보안 문제 발생
<div align = "center" >
<img src = "https://github.com/sooyounghan/Web/assets/34672301/aadfd287-187e-420e-ade7-139bc28287f4">
</div>

5. Cookie 메서드
<div align = "center" >
<img src = "https://github.com/sooyounghan/Web/assets/34672301/196dfaf2-c403-4247-ac93-785b304282a0">
</div>

6. 쿠키 생성
   - Cookie() 메서드 사용
   - 쿠키를 생성한 후에는 반드시 response 내장 객체의 addCookie() 메서드로 쿠키 설정

      		Cookie Cookie(String name, String value)
     		- name : 쿠키 식별 이름
     		- value : 쿠키 값
```jsp
Cookice cookie = new Cookie("memberId", "admin");
response.addCookie(cookie);
```

7. 쿠키 객체 얻기

    - 클라이언트에 저장된 모든 쿠키 객체를 가져오려면 request 내장 객체의 getCookies() 메서드 사용
    - 쿠키 객체가 여러 개일 때, 배열 형태로 가져옴

      		Cooke[] request.getCookies()
      		> Cookie[] cookies = request.getCookies();

8. 쿠키 객체 정보 얻기

	- 쿠키 객체에 저장된 쿠키 이름과 값을 가져오기 위해 getName(), getValue() 메서드 사용

 		  String getName()
   		  String getValue()
```jsp
Cookie[] cookies = request.getCookies();
for(int i = 0; i < cookies.length; i++) {
	out.println(cookies[i].getName() + " : " + cookies[i].getValue() + "<br>");
}
```

9. 쿠키 삭제

   - 쿠키의 유효 기간을 결정 : setMaxAge() 메서드에 유효 기간을 0으로 설정하면, 쿠키 삭제 가능
```jsp
Cookie cookie = new Cookie("memberId", "admin);
cookie.setMaxAge(0);
response.addCookie(cookie);
```                                                                                                            
 -----
### Session과 Cookie
-----
<div align = "center" >
<img src="https://github.com/sooyounghan/Web/assets/34672301/63dc715b-e388-48e9-81b7-6844e1b5fde8">
</div>
