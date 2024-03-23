-----
### MVC Controller : Servlet
-----
<div align ="center">
<img src ="https://github.com/sooyounghan/Web/assets/34672301/ff45a3f8-699e-4411-87ac-83170efdab41">
</div>

1. 웹 브라우저가 전송한 HTTP 요청을 받아 서블릿의 doGet() 메서드나 doPost() 메서드가 호출
2. 웹 브라우저가 어떤 기능을 요청했는지 분석
3. Model을 사용해 요청한 기능을 수행
4. Model로부터 전달받은 결과물을 알맞게 가공한 후, request나 session의 setAttribute() 메서드를 사용해 결과값을 속성에 저장 (JSP에서 사용)
5. 웹 브라우저에 결과를 전송할 JSP를 선택한 후, 해당 JSP View Page로 Forwarding 또는 Redirect

-----
### 전형적인 Controller Servlet의 구현
-----
```java
import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class SimpleController extends HttpServlet {
  // 1. 1단계 : HTTP의 요청을 받음
  	@Override
  	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
  		  service(request, response);
  	}
  	
  	@Override
  	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
  		  service(request, response);
  	}
  	
    // 2. 2단계 : 요청 분석 (request 객체로부터 사용자의 요청을 분석)
  
    // 3. 3단계 : Model을 사용해 요청한 기능 수행
  
    // 4. 4단계 : request나 session에 처리 결과를 저장
  	req.setAttribute("result", resultObject);
  		

    // 5단계 : RequestDispatcher를 사용해 알맞은 View로 Forwarind 또는 Redirect
		RequestDispatcher dispatcher = req.getRequestDispatcher(viewPage);
		dispatcher.forward(req, res);
	}
}
```

-----
### MVC View : JSP
-----
1. Controller에서 request 또는 session 기본 객체에 저장된 데이터를 사용해 웹 브라우저에 알맞은 결과를 출력
2. 웹 브라우저가 요청한 결과를 보여주는 역할, Controller에게 전달해주는 매개체 역할

-----
### MVC Model
-----
1. 비즈니스 로직을 처리해주는 것
2. 즉, 제공해줘야 하는 기능은 웹 브라우저의 요청을 처리하는 데 필요한 기능
<div align ="center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/5d7e3507-bb33-44ce-8b93-b82035b9ff95">
</div>

3. Model의 기능은 Controller Servlet이 웹 브라우저의 요청을 분석해 알맞은 Model을 호출하면서 모델의 기능 시작
4. Model은 Controller가 요청한 작업을 처리한 후 알맞은 결과를 Controller에게 전달하는데, 이 때 처리한 결과값을 저장하는 객체로 JavaBean 이용
5. Model은 Service 클래스나 DAO 클래스를 이용해 비즈니스 로직 수행
