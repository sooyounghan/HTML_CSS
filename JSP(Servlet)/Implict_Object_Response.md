-----
### response 기본 객체
-----
1. response  내장 객체
	- request 기본 객체와 반대의 기능 수행
	- 웹 브라우저에 보내는 응답 정보를 담음
	- 헤더 정보 입력, 리다이렉트 하기와 같은 기능 제공
	- 사용자의 요청을 처리한 결과를 서버에서 웹 브라우저로 전달하는 정보를 저장하고, 서버는 응답 헤더와 요청 처리 결과 데이터를 웹 브라우저로 보냄
	- JSP 컨테이너는 서버에서 웹 브라우저로 응답하는 정보 처리를 위해 javax.servlet.http.HttpServletResponse 객체 타입의 내장 객체를 사용해 사용자 요청에 응답

 2. 페이지 이동 (Redirection)
	- 사용자가 새로운 페이지를 요청할 때 같이 페이지를 강제 이동하는 것
	- 서버는 웹 브라우저에 다른 페이지로 강제 이동하도록 redirection 메서드 제공
	- 페이지 이동 시 문자 인코딩을 알맞게 설정해야함

-----
### response 객체 : 웹 브라우저에 헤더 정보 전송하기
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/2f4770a2-6a30-43da-b400-18830d2b58d4">
</div>

1. addDateHeader(String name, long date) : name 헤더에 date 추가 (date : 1970/1/1 이후 흘러간 시간을 1/1000초 단위)
2. addHeader(String name, String value) : name 헤더에 value값 추가
3. addIntHeader(String name, int value) : name 헤더에 정수 값 value 값 추가
4. setDateHeader(String name, long Date) : name 헤더 값을 date로 지정
    
   	      * setDateHeader는 System.currentTimeMillis 나 Date 객체의 getTime로부터 반환되는 값을 GMT 시간 문자열 변경
5. setHeader(String name, String value) : name 헤더의 값을 value로 저장
6. setIntHeader(String name, int value) : name 헤더의 값을 정수 값 value로 저장
7. containsHeader(String name) : 이름이 name인 헤더를 포함하면 true, 그렇지 않으면 false
