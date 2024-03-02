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
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/3eae30f3-effb-42b7-8c0c-20cb60369d84">
</div>

-----
### 동적 웹 페이지
-----
1. 저장된 내용을 다른 변수로 가공 처리하여 보는 것
2. PHP(Personal Home Page), ASP(Active Server Page), JSP
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/9e04a952-33be-472a-a16b-09d6876fde61">
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
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/26f1eeda-d2ee-4dfb-bf09-dca42e9bfa75">
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
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/206dc33a-77f7-494b-a5cd-a4c2dedeb058">
</div>

-----
### 동적 웹 프로젝트의 구조
-----
<div align = "center">
<img src="https://github.com/sooyounghan/JAVA/assets/34672301/e2762a9a-7ff7-4704-9919-6016e488e7a2">
</div>

-----
### MVC Model 1
-----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/feddce06-2f9d-4944-b6a2-ccb83b1035ed">
</div>

- 클라이언트의 요청을 JSP가 받아 JavaBean에 의해 DB에게 데이터에 접근해 데이터를 가져온 뒤, JSP가 Broswer에게 Response
- 핵심은 JSP가 결국 Reqeust와 Response 모두 처리하는 것

1. Client가 Browser를 통해 Web Applciation Server에게 Request 전달
   
2~3. WAS가 Request에 의해 JavaBeans을 이용해 DB 서버에 접속해서 데이터를 가져옴   

4. 가져온 데이터에 대해 Broswer에게 Response 전달

-----
### MVC Model 2
-----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/22b17049-6089-4d31-a9a3-43e21d6f4933">
</div>

1. Client가 Browser를 통해 발생한 Request에 의해 Servlet(Controller)이 처리 (JSP와 분리 가능)
2. 이에 대한 Model 역할을 하는 JavaBeans에 의해 DB에 접근해 데이터를 접근하여 가져옴
3. Model에 가져온 데이터를 Controller에 의해 보여질 View(JSP)와 함께 처리하여 Client의 Browser에게 응답

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

4. Port Number 및 URIEncoding 설정 (server.xml)
   - port : Tomcat의 server.xml의 커넥터 설정 중 Port Number를 변경
   - URIEncoding : Tomcat의 server.xml의 커넥터 설정 중 URIEncoding를 UTF-8 설정 (GET 방식 한글 깨짐 문제)
     
```jsp
    <!-- Port Number Change (8080 -> 8081), 기본 방식은 Get 방식이므로 이를 요청 시 한글 깨짐 방지 -->
    <Connector connectionTimeout="20000" maxParameterCount="1000" URIEncoding ="UTF-8" port="8081" protocol="HTTP/1.1" redirectPort="8443"/>
```

   - 모든 URL에 대해 아래의 Set Character Encoding Filter를 거치도록 설정 (web.xml 내)
```jsp
  <!-- The mapping for the Set Character Encoding Filter -->
<!-- -->
    <filter-mapping>
        <filter-name>setCharacterEncodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```

   - Tomcat의 web.xml에서 filter 설정 중 POST 방식 한글 깨짐 문제 해결  	
    
```jsp
  <!-- A filter that sets character encoding that is used to decode -->
  <!-- parameters in a POST request -->
 <!-- post 요청 방식일 때, Decoding 과정에서의 character encoding을 처리하는 부분 = 한글 깨짐 문제 방지 -->
    <filter>
        <filter-name>setCharacterEncodingFilter</filter-name>
        <filter-class>org.apache.catalina.filters.SetCharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <async-supported>true</async-supported>
    </filter>
```
