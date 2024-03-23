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

1. Servler Container로 request가 진입되기 전, Filter 역할을 통해 먼저 그 조건에 대해 확인 
2. 실행된 후에, 해당 Servlet이 실행될 여부까지 유효성 검사 까지 가능
3. Servlet이 처리된 후 response로 전송되기 전에도 다시 한 번 유효성 검사까지 가능

-----
### Servlet Filter
-----
1. 다음과 같이 ServletEx Serlvet 있다고 하자. (Package명 : ServletEx)
```java
import java.io.*;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

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

2. 이 Servlet에 Filter를 적용하고 싶다면, 해당 Filter Class(MyFilter)를 생성
   - Filter Class가 속한 Package의 이름 : ServletEx.MyFilter.MyFilter
   - Filter Class 이름 : MyFilter
   - Interface 추가 : javax.servlet.Filter
   - Filter Interface의 추가로 다음과 같이 클래스 생성
     
```java
package ServletEx.MyFilter;

import java.io.IOException;

import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;

public class MyFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {
		System.out.println("Filter!");
	}
}

```

3. Filter 설정을 하면, request에 대해 Filter 처리를 위해 실행
4. WAS가 처음 실행될 때, 해당 WAS Continaer에 Fitler 적재

-----
### Servlet Filter 설정 - Web.xml
-----
1. web.xml 설정
   - 전체적으로 설정해야 할 Filter라면, Servers의 web.xml에 설정
   - 특정 프로젝트에 설정할 것이라면, 특정 프로젝트의 web.xml에 설정
   - 위의 MyFilter의 경우에는 해당 프로젝트가 속한 Filter 프로젝트의 web.xml에 다음과 같이 설정

```jsp
  	<filter>
		<filter-name>MyFilter</filter-name>
		<filter-class>ServletEx.MyFilter.MyFilter</filter-class>
	</filter>
	
	<filter-mapping>
		<filter-name>MyFilter</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>
```

+ filter 태그 내에는 해당 Filter의 이름, 속한 패키지명.클래스명을 명시
+ filter-mapping은 해당 Filter의 이름에 대해 어떠한 URL의 요청을 받았을 때, Filter가 적용될 지 결정

2. 해당 Servlet Filter가 설정되어 실행되면, 어떠한 URL에 대해 요청해도 Filter가 실행되나, 현재 Filter에는 특정 Filter 또는 Servlet으로 전이시킬지 표시하지 않았으므로, 해당 Filter에서 계속 유지

3. FilterChain : Servlet의 흐름을 결정하는 역할
   
4. 다음과 같이 FilterChain chain에 대해 설정하면,
```java
package ServletEx.MyFilter;

import java.io.IOException;

import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;

public class MyFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {
		chain.doFilter(request, response);
		System.out.println("Filter!");
	}
}
```

+ Filter의 흐름을 다음 filter나 Servlet이 실행되도록 설정하는 것이며, 해당 페이지로 request를 전달 (즉, 조건을 통해 설정 부분 설정 가능)
+ 이에 따라 처리 후 그 결과를 response로 다시 전달받음
+ 그리고 다음 문장인 콘솔 출력 문장 실행

5. 조금 더 명확한 흐름을 보기 위해 다음과 같이 설정하면,
```java
package ServletEx.MyFilter;

import java.io.IOException;

import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;

public class MyFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {
		System.out.println("Before Filter!");
		chain.doFilter(request, response);
		System.out.println("After Filter!");
	}
}
```
+ Before Filter! 출력 - 다음 Filter 또는 Servlet으로 request 전달 - 처리 후 response 전달 - After Filter! 출력
  

-----
### Servlet Filter 예제
-----
1. Encoding 작업 Filter를 통해서 하고 싶다면, 다음과 같이 가능
```java
package ServletEx.MyFilter;

import java.io.IOException;

import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;

public class MyFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {
		request.setCharcterEncoding("UTF-8");
		chain.doFilter(request, response);
	}
}
```

2. 즉, 다음 Servlet 또는 Filter로 이동하기 전에 request에 해당 characterEncoding 타입을 결정하여 전달

-----
### Servlet Filter 설정 - Annotation
-----
1. web.xml에 설정하지 않고도, Annotation을 이용해 가능한데, 다음과 같이 설정
```java
package ServletEx.MyFilter;

import java.io.IOException;

import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import javax.servlet.annotation.WebFilter;

@WebFilter("/*")
public class MyFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {
		request.setCharacterEncoding("UTF-8");
		chain.doFilter(request, response);
	}
}
```

2. Annotation을 설정하면 web.xml을 통해 설정한 방법과 동일
