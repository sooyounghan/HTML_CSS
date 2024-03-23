-----
### 기본적인 웹 서버 - WAS - Servlet Container의 Logic
-----
<div align ="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ebcbf8fe-7a2e-40dd-af03-8a2920ae9c7f">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d6170a2c-a50c-414a-8ead-277578c380d7">
</div>
1. 웹 서버(=WAS)는 Cilent의 request에 따라 해당 WAS Container에서 URL Mapping을 통해 해당되는 Servlet을 Maaping
2. 해당되는 Servlet을 발견 후, 이에 대해 처리 후 reponse 해주는 방식이 기본적인 방식
3. 그렇다면, UTF-8과 같이 한글 문서가 들어간 부분에 대해서는 setCharacterEncoding을 공통적으로 처리해줘야하는 부분을 공통적으로 처리할 방법은?

-----
### Servlet Filter
-----
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/02225e7f-08ac-482a-bc96-dc271cc2d751">
</div>

1. Servler Container로 request가 진입되기 전, 일종의 Filter 역할을 통해 먼저 그 조건에 대해 확인 
2. 실행된 후에, 해당 Servlet이 실행될 여부까지 유효성 검사 까지 가능
3. 또한, Servlet이 처리된 후 response로 전송되기 전에도 다시 한 번 유효성 검사까지 가능

-----
### Servlet Filter
-----
1. 다음과 같은 코드가 있다고 하자.
```java
import java.io.*;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/*
 * Browser에 문자열 출력 웹 문서 (@WebServlet)
 */

// http://localhost:8081/webPro/hello
@WebServlet(urlPatterns = "/hello")
public class ServletEx extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	    response.setCharacterEncoding("UTF-8");
	    response.setContentType("text/html; charset=UTF-8");
	    request.setCharacterEncoding("UTF-8");
	
			PrintWriter out = response.getWriter();
	
	    for(int i = 0; i < 100; i++) {
	  		  out.println((i+1) + ": 안녕 Servlet!");
    }
  }
}
```

2. 해당 UTF-8 작업에 대해서는 모든 Servlet에 공통적으로 적용하고 싶다면, Filter Class(CharacterEncodingFilter)를 생성
   - Filter Class가 속한 Package의 이름 : ServletFilterEx.Filter
   - Filter Class 이름 : CharacterEncodingFilter
   - Interface 추가 : javax.servlet.Filter
   - Filter Interface의 추가로 다음과 같이 클래스 생성
```java
package ServletFilterEx.Filter;

import java.io.IOException;

import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;

public class CharacterEncodingFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {

	}
}
```

3. Filter는 설정을 하면, 어떠한 request가 와도 Filter 처리를 위해 실행
4. WAS가 처음 실행될 때도 한 번 실행

-----
### Servlet Filter 설정
-----
1. web.xml 설정

3. Annotation 설정

   
