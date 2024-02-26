-----
### 웹의 동작 원리
-----
1. 클라이언트 - 서버 방식
2. 웹 프로그래밍 언어 : 클라이언트 측 실행 언어 / 서버 측 실행 언어
   
-----
### 정적 웹 페이지
-----
1. 컴퓨터에 저장된 텍스트 파일 그대로 보는 것
2. HTML(HyperText Markup Language)
<div align = "center">
<img width="351" alt="다운로드 (12)" src="https://github.com/sooyounghan/JAVA/assets/34672301/3eae30f3-effb-42b7-8c0c-20cb60369d84">
</div>

-----
### 동적 웹 페이지
-----
1. 저장된 내용을 다른 변수로 가공 처리하여 보는 것
2. PHP(Personal Home Page), ASP(Active Server Page), JSP
<div align = "center">
<img width="353" alt="다운로드 (13)" src="https://github.com/sooyounghan/JAVA/assets/34672301/9e04a952-33be-472a-a16b-09d6876fde61">
</div>

-----
### Servlet
-----
1. 자바를 사용해 웹 페이지를 동적으로 생성하는 서버 측 웹 프로그래밍
2. 웹 서버 성능 향상을 위해 사용 되는 자바 클래스 일종
3. 자바 코드 안에 HTML 포함 (JSP : HTML 코드 내 Java 코드 포함)
4. 특징 

       - 이식 가능
       - 효율적으로 확장 가능
       - 견고함
<div align = "center">
<img width="289" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/26f1eeda-d2ee-4dfb-bf09-dca42e9bfa75">
</div>

-----
### JSP (Java Server Pages / Jakarta Server Pages)
-----
1. 자바 언어를 기반으로 하는 스크립트 언어
2. HTML 내 자바 코드를 삽입 해 동적으로 웹 페이지를 생성해 웹 브라우저에 전달하는 서버측 스크립트 언어

       * 개발환경 : jDK / 웹 서버 : Tomcat / 통합 개발 환경 : Eclipse

3. 특징 

       - 서블릿 기술의 확장
       - 유지 관리 용이
       - 빠른 개발 가능
       - 코드의 간결함 가능

<div align = "center">
<img width="297" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/206dc33a-77f7-494b-a5cd-a4c2dedeb058">
</div>

-----
### 동적 웹 프로젝트의 구조
-----
<div align = "center">
<img width="330" alt="다운로드 (14)" src="https://github.com/sooyounghan/JAVA/assets/34672301/e2762a9a-7ff7-4704-9919-6016e488e7a2">
</div>

-----
### JSP 기본 실행 환경
-----
1. 자바 웹 작업 환경 : project - src - webapp - JSP 파일
2. [서버 내 프로젝트 탑재 (add and remove)

       Tomcat - webPro (Synchronized) : 프로젝트를 서버 내에 탑재
   
3. Run as - Run on server (현재 프로젝트 서버 내 실행) -> http://ip주소(localhost):8081/webPro/hello.html (예측 URL) 

          ** 프로토콜://IP주소(도메인네임):Port번호/Context Path/파일명.확장자 
              = 프로토콜://IP주소:Port번호/Directory(경로)
              (http://ip주소:8081/webPro/파일.확장자)
              (Localhost = 나의 Host 주소 = 내 IP 주소)

```jsp
<!-- page : 지시어(directive) // language, contentType, pageEncoding : 속성(Attribute) -->
<%@page import="org.apache.naming.java.javaURLContextFactory"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"
    import="java.util.*, java.text.SimpleDateFormat"%> // java import문은 다음과 같이 작성하고, ","로 구분
<% // Java Code 영역 
SimpleDateFormat sdf = new SimpleDateFormat("yyyy");
Date today = new Date();
String strDate = sdf.format(today);
%>
<!--  HTML5 Comment -->

<!-- HTML5 버전 문서 타입 선언부 -->
<!DOCTYPE HTML>
<HTML>
	<HEAD>
		<meta charset = "UTF-8"> 
		<title> <%=strDate%> </title>
	</HEAD>
	
	<BODY>
		<h1> hello.jsp </h1>
		<h2> URL 형식 </h2>
		<h3> http://IP주소(Domain Name/내 IP : LocalHost):포트번호/경로 :디렉토리 </h3>
		<h4> http://IP주소(Domain Name/내 IP : LocalHost):포트번호/컨택스트패스/파일명.확장자 </h4>
		<h5> http://IP주소(또는 Domain Name):8081/webPro/hello.html)</h5>
		<h6> http://localhost:8081/webPor/hello.html </h6>
		
		<hr> <!-- 수평선, 구별 역할 -->
		
		<pre> <!-- Preformatted 태그 -->
		br 태그 : 단순 줄바꿈, 반복 / p 태그 : 문단, p 요소 앞뒤로 빈 줄 삽입
		</pre>
		
		<hr><!-- 수평선, 구별 역할 -->
			<ul> 
				<li> ul : unordered list : 순서가 없는 목록 (무순서 목록) </li>
			 	<li type = "disc"> Frontend - HTML, CSS, JavaScipt, jQuery, Ajax, JSON 등 </li>
			 	<li type = "circle"> Backend - Java, JSP/Servlet </li>
			 	<li type = "square"> DBMS - Oracle, MySQL, MariaDB 등 </li>
			</ul>
			<ol>
				<li> ol : ordered list : 순서가 있는 목록 (순서 목록) </li>
				<li type = "1"> 요구사항 개발 프로세스 </li>
				<ol>
					<li type = "A"> 요구사항 도출 </li>
					<li type = "a"> 요구사항 분석 </li>
					<li type = "I"> 요구사항 명세 </li>
					<li type = "i"> 요구사항 확인 </li>
				</ol>
			</ol>
		
		
		Hello<br><br><br> : <!-- <br></br> = </br> --> 사이에는 비어있음 (EmptyTag) 
		
		HTML : HyperText Markup Language 
		(웹 문서의 내용, 골격 담당)
		
		<p> XML - eXtensible Markup Language (확장가능한 마크업 언어로, 작은 DB역할 (데이터 역할)) </p>
		    - 다른 언어들과 연동(다른 언어에 종속되지 않음)하며, 주로 환경 설정용으로 많이 사용
	</BODY>
</HTML>
```
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"
    import = "java.util.*, java.util.stream.*, java.text.SimpleDateFormat"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title> list </title>
	</head>
	
	<body>
		<h2> 회원 명단 </h2>
		<h3> 프로토콜://IP주소(도메인네임):Port번호/Context Path/파일명.확장자 </h3>
		<h3> http://172.30.1.33:8081/webPro/cf/listEx01.jsp </h3>
		<% // Java Code Area
		// ArrayList 객체 생성하여 임의의 이름 5개를 저장하여 console 창에 출력
		List<String> nameList = new ArrayList<String>();
		
		nameList.add("A");
		nameList.add("B");
		nameList.add("C");
		nameList.add("D");
		nameList.add("E");
		
		nameList.stream().forEach((name) -> System.out.print(name)); // Stream을 이용해 Console에 출력
		System.out.println();
		Stream<String> name = nameList.stream(); 
		name.forEach(System.out::print); // Stream을 이용해 Console에 출력
		
		%>
		
		<%=nameList%><br> // nameList를 Web에 출력

		<hr> 
		<h2> 회원명단 (ArrayList 구현 클래스 사용) </h2>
		<%
		for(int i = 0; i < nameList.size(); i++) {
			String str = nameList.get(i);
			%>
			<%=str %><br> // nameList 요소들을 web에 출력
		<%	
		}
		%>
	</body>
</html>
```
```jsp
<%@ page import = "java.util.*, java.util.stream.*, java.text.SimpleDateFormat"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title> Set </title>
	</head>
	
	<body>
		<h2> 회원 명단 </h2>
		<h3> 프로토콜://IP주소(도메인네임):Port번호/Context Path/파일명.확장자 </h3>
		<h3> http://172.30.1.33:8081/webPro/cf/SetEx01.jsp </h3>
		<% // Java Code Area
		// ArrayList 객체 생성하여 임의의 이름 5개를 저장하여 console 창에 출력
		Set<String> hashSet = new HashSet<>();
		
		hashSet.add("라");
		hashSet.add("가");
		hashSet.add("다");
		hashSet.add("마");
		hashSet.add("바");
		hashSet.add("바");
		
		hashSet.stream().forEach((name) -> System.out.print(name)); // Stream을 이용해 Console에 요소 출력
		System.out.println();
		Stream<String> name = hashSet.stream();
		name.forEach(System.out::print); // Stream을 이용해 Console에 요소 출력
		System.out.println();
		
		%>
		
		<%=hashSet%><br> // hashSet 요소를 Web에 출력

		<hr> 
		<h2> 회원명단 (HashSet 구현 클래스 사용) </h2>
		<%
		Iterator<String> it = hashSet.iterator();
		while(it.hasNext()) {
			String str = it.next();
			System.out.print(str + " "); // 요소를 Console에 출력
			out.print(str + "<br>"); // 브라우저에 출력 (줄 바꿈 : "<br>")
		}
		%>
	</body>
</html>
```
```jsp
<%@ page import = "java.util.*, java.util.stream.*, java.text.SimpleDateFormat"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title> Map </title>
	</head>
	
	<body>
		<h2> 회원 명단 </h2>
		<h3> 프로토콜://IP주소(도메인네임):Port번호/Context Path/파일명.확장자 </h3>
		<h3> http://172.30.1.33:8081/webPro/cf/MapEx01.jsp </h3>
		<% // Java Code Area
		// ArrayList 객체 생성하여 임의의 이름 5개를 저장하여 console 창에 출력
		Map<String, String> hashMap = new HashMap<>();
		
		hashMap.put("001", "abc");
		hashMap.put("002", "bcd");
		hashMap.put("003", "cde");
		hashMap.put("004", "efg");
		hashMap.put("005", "hij");;
		hashMap.put("001", "jkm");;
	
		%>

		<hr> 
		<h2> 회원명단 (HashMap 구현 클래스 사용) </h2>
		<%
		hashMap.entrySet().stream().forEach((e) -> System.out.println(e.getKey() + " : " +e.getValue())); // Stream을 이용한 Console 출력
		System.out.println();
		
		Set<String> keySet = hashMap.keySet(); // keySet 이용
		Iterator<String> iter = keySet.iterator();
		
		while(iter.hasNext()) {
			String key = iter.next();
			out.println(key + " : " + hashMap.get(key) + "<br>"); // KeySet을 이용한 key, value web에 출력
		}
		System.out.println();
		
		Collection<String> c = hashMap.values(); // values() 이용
		out.println(c + "<br>"); // Web에 value 출력
		
		Set<Map.Entry<String, String>> entrySet = hashMap.entrySet();
		Iterator<Map.Entry<String, String>> it = entrySet.iterator();
		while(it.hasNext()) {
			Map.Entry<String, String> e = (Map.Entry<String, String>)it.next();
			System.out.println(e.getKey() + " : " + e.getValue()); // Console에 출력
			out.print(e.getKey() + " : " + e.getValue() + "<br>"); // Web에 출력
		}
		%>
	</body>
</html>
```
```jsp
<%@ page import = "java.util.*, java.util.stream.*, java.text.SimpleDateFormat"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title> HashTable </title>
	</head>
	
	<body>
		<h2> 회원 명단 </h2>
		<h3> 프로토콜://IP주소(도메인네임):Port번호/Context Path/파일명.확장자 </h3>
		<h3> http://172.30.1.33:8081/webPro/cf/MapEx02.jsp </h3>
		<% // Java Code Area
		// ArrayList 객체 생성하여 임의의 이름 5개를 저장하여 console 창에 출력
		Hashtable<String, String> hashtable = new Hashtable<>();
		
		hashtable.put("001", "abc");
		hashtable.put("002", "bcd");
		hashtable.put("003", "cde");
		hashtable.put("004", "efg");
		hashtable.put("005", "hij");;
		hashtable.put("001", "jkm");;
	
		%>

		<hr> 
		<h2> 회원명단 (HashTable 구현 클래스 사용) </h2>
		<%
		hashtable.entrySet().stream().forEach((e) -> System.out.println(e.getKey() + " : " +e.getValue())); // Stream을 이용한 Console 출력
		System.out.println();
		
		Set<String> keySet = hashtable.keySet(); // keySet 이용
		Iterator<String> iter = keySet.iterator();
		
		while(iter.hasNext()) {
			String key = iter.next();
			out.println(key + " : " + hashtable.get(key) + "<br>"); // KeySet을 이용한 key, value web에 출력
		}
		System.out.println();
		
		Collection<String> c = hashtable.values(); // values() 이용
		out.println(c + "<br>"); // Web에 value 출력
		
		Set<Map.Entry<String, String>> entrySet = hashtable.entrySet();
		Iterator<Map.Entry<String, String>> it = entrySet.iterator();
		while(it.hasNext()) {
			Map.Entry<String, String> e = (Map.Entry<String, String>)it.next();
			System.out.println(e.getKey() + " : " + e.getValue()); // Console에 출력
			out.print(e.getKey() + " : " + e.getValue() + "<br>"); // Web에 출력
		}
		%>
	</body>
</html>
```

-----
### 스크립트 태그 (Script Tag)
-----
1. JSP페이지(.jsp)가 서블릿 프로그램(.java)에서 서블릿 클래스(.class)로 변환할 때, JSP 컨테이너가 자바 코드가
2. 삽입되어 있는 스크립트 태그를 처리하고 나머지는 HTML 코드나 일반 텍스트로 간주
<div align = "center">
<img width="384" alt="다운로드" src="https://github.com/sooyounghan/JAVA/assets/34672301/83794b19-f54d-49ee-b468-6da7ef963e90">
</div>

3. 주석문(Commenet) : <%-- --%>
4. 지시자(Directrive) : <%@ %> [페이지 속성 지정] : 주로 import 목적
5. jsp 내 src/main/java에 있는 java 파일 을 import 하는 방법

       A. java 파일은 src/main/java에 저장 (java 파일을 import 가능 (Import - Import - General - File system - Directory 선택)
       B. <%@ page import ="패키지명.클래스명"%>

```jsp
<%@ page import="member.Member" %> // "패키지이름 . 클래스이름"
```

```jsp
<%@ page import="java.util.*" %>
<%@ page import="student.StudentDTO" %> // src/main/java 내에 있는 Directory 중 student에 있는 StudentDTO 클래스 파일 import
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>

<!DOCTYPE html>
	<html>
		<head>
			<meta charset="UTF-8">
			<title> Student List </title>
		</head>
	
		<body>
			<h3> studentList.jsp with StudentDTO</h3>
			<h4> http://172.30.1.43:8081/webPro/cf/studentList.jsp </h4>
			<%
			out.print("====List에 StudentDTO 객체 추가====" + "<br>");
			
			List<StudentDTO> list_dto = new ArrayList<StudentDTO>(); // 객체 StudentDTO를 담는 ArrayList
			
			list_dto.add(new StudentDTO("123456", "ABC", new Date())); // 객체 생성과 동시에 ArrayList에 삽입
			list_dto.add(new StudentDTO("345678", "BCD", new Date()));
			list_dto.add(new StudentDTO("900554", "CDF", new Date()));
		
			for(int i = 0; i < list_dto.size(); i++) {
				out.print(list_dto.get(i).toString() + "<br>"); // toString() Override을 통해 ArrayList 요소 출력
			}
			
			out.print("====Set에 StudentDTO 객체 추가====" + "<br>");
			
			Set<StudentDTO> set_dto = new HashSet<StudentDTO>();
			
			StudentDTO student1 = new StudentDTO(); // 기본 생성자를 통한 StudentDTO 객체 생성
			student1.setSno("123456");
			student1.setSname("ABC");
			student1.setEnrollmentDate(new Date()); // Setter를 통한 초기화
			
			StudentDTO student2 = new StudentDTO(); // 기본 생성자를 통한 StudentDTO 객체 생성
			student2.setSno("345678");
			student2.setSname("BCD");
			student2.setEnrollmentDate(new Date()); // Setter를 통한 초기화
			
			StudentDTO student3 = new StudentDTO(); // 기본 생성자를 통한 StudentDTO 객체 생성
			student3.setSno("900554");
			student3.setSname("CDF");
			student3.setEnrollmentDate(new Date()); // Setter를 통한 초기화
			
			set_dto.add(student1); // student1 객체 삽입
			set_dto.add(student2);
			set_dto.add(student3);
		
			for(StudentDTO student : set_dto) { // 향상된 for문을 통한 set 요소 추출
				out.print(student.toString() + "<br>");
			}
			
			Iterator<StudentDTO> iterator = set_dto.iterator();
			while(iterator.hasNext()) {
				out.print(iterator.next().toString() + "<br>");		
			}
		
			out.print("====Map에 StudentDTO 객체 추가====" + "<br>");
			
			Map<String, StudentDTO> map_dto = new HashMap<String, StudentDTO>(); // Key는 학생의 학번
			
			map_dto.put(student1.getSno(), student1);
			map_dto.put(student2.getSno(), student2);
			map_dto.put(student3.getSno(), student3);
			
			Set<Map.Entry<String, StudentDTO>> entrySet = map_dto.entrySet();
			Iterator<Map.Entry<String, StudentDTO>> iter = entrySet.iterator();
			
			while(iter.hasNext()) {
				Map.Entry<String, StudentDTO> entry = iter.next();
				out.print(entry.getValue().toString() + "<br>");
		}%>
		</body>
	</html>
```
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
