-----
### MVC MODEL 2
-----

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/22b17049-6089-4d31-a9a3-43e21d6f4933">
</div>

<간단한 로그인 데이터 받기>

1. 로그인 폼 (Request)
```html
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
	</head>

	<body>
	<form action = "LoginProc" method = "post">
	<table border = "1" align = "center">
		<tr height = "40">
			<td width = "120" align = "center">아이디</td>
			<td width = "180" align = "center"><input type = "text" name = "id"></td>
		</tr>
		<tr height = "40">
			<td width = "120" align = "center">비밀번호</td>
			<td width = "180" align = "center"><input type = "password" name = "pwd"></td>
		</tr>
		<tr height = "40">
			<td colspan = "2" align = "center"><input type = "submit" value = "로그인"></td>
		</tr>
	</table>	
	</form>
	</body>
</html>
```

2. LoginProc Servlet (Controller)
```java
import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/LoginProc")
public class LoginProc extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		process(request, response);
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		process(request, response);
	}
	
	public void process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		String id = request.getParameter("id");
		String pwd = request.getParameter("pwd");
		
		request.setAttribute("id", id);
		request.setAttribute("pwd", pwd);
		RequestDispatcher rd = request.getRequestDispatcher("LoginProc.jsp");
		rd.forward(request, response);
	}
}
```

3. LoginProc.jsp (View)
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	넘어온 데이터 : ${id} / ${pwd}
</body>
</html>
```
