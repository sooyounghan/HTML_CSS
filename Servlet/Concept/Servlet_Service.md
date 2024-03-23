-----
### service 함수
-----
1. JSP PAGE 내에서 FORM을 통해 GET / POST 방식으로 받게 되었을 때, doGet()과 doPost() 방식으로 처리할 수 있음
2. 하지만, service() 내에서 GET / POST 방식에 대해 처리도 가능
```java
package ServletEx;

import javax.servlet.http.HttpSession;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;


@WebServlet("/hello")
public class ServletEx extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	    if(request.getMethod().equals("GET") {
        ...
      } else if(request.getMothod().equals("POST") {
        ...
      }
	}
}
```

3. service 메서드 내에서 request에 대해 getMethod()를 호출하면, request로 전달받은 FORM에 대한 method 방식에 대한 String 값을 얻을 숭 ㅣㅆ음
4. 이에 대해 equals() 함수를 이용해 GET / POST 방식을 확인하여 나눠서 처리 가능
   - 단, GET / POST는 대문자로 작성
   - equalsIgnoreCase() 메서드를 사용 : 대 / 소문자 구분 없이 처리 가능

-----
### super.service(reqeust, response)
-----
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b04175a1-a123-49a4-a480-0800f4a1e20f">
</div>

1. 위의 코드의 경우에는 service Method를 HttpServlet으로부터 상속받아 오버라이딩 한 것
2. 그렇다면, 오버라이딩을 하지 않고 사용한다면? (즉, super.service(request, response) 호출)
   - 사용자로부터 request가 발생하면, doGet / doPost 방식만을 오버라이딩을 하면, 해당 오버라이딩 부분에 대해 처리가 가능
   - 하지만, doGet / doPost 방식을 오버라이딩 하지 않는다면, 오류가 발생 (http status 405 - 허용되지 않는 메서드 오류 발생)

```java
package ServletEx;

import javax.servlet.http.HttpSession;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;


@WebServlet("/hello")
public class ServletEx extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	    if(request.getMethod().equals("GET") {
        ...
      } else if(request.getMothod().equals("POST") {
        ...
      }
      super.service(request, response);
	}
}
```
   - 즉, 위와 같이 service를 통해 get / post 방식에 대해 처리했으나, super.service()를 만나게 되면, 오버라이딩된 doGet()과 doPost()를 확인
   - 하지만, 오버라이딩된 메서드가 없으므로, http status 405 오류 발생

5. 다음과 같이, doGet(), doPost()를 오버라이딩하면, 오류 미발생
```java
package ServletEx;

import javax.servlet.http.HttpSession;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;


@WebServlet("/hello")
public class ServletEx extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	    if(request.getMethod().equals("GET") {
        ...
      } else if(request.getMothod().equals("POST") {
        ...
      }
      super.service(request, response);
	}

	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	  ...  
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	  ...  
	}
}
```
   - super.service()는 get / post 방식에 따라 오버라이딩된 doGet() / doPost() 방식에 맞춰 처리
