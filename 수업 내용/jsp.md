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
3. 
