-----
### MVC 
-----

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/22b17049-6089-4d31-a9a3-43e21d6f4933">
</div>

1. Model : 비즈니스 영역의 로직을 처리 (JavaBean, Logic 처리 Class)
2. View : 비즈니스 영역에 대한 사용자가 보게 될 결과 화면을 담당 (JSP Page)
3. Controller : 사용자의 입력 처리와 흐름 제어를 담당 (Servlet)
4. 비즈니스 로직을 처리하는 Model과 결과 화면을 보여주는 View를 분리
   - Model의 내부 로직이 변경되더라도 View의 영향을 받지 않음
   - View와 Model이 직접 연결되어 있지 않으므로 내부 구현 로직에 상관없이 View 변경 가능
5. 어플리케이션의 흐름 제어나 사용자의 처리 요청은 Controller에 집중
   - Controller는 사용자의 요청에 대해 알맞은 Model을 사용
   - 사용자에게 보여줄 View를 선택 

-----
### 간단한 로그인 데이터 받기
-----
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
