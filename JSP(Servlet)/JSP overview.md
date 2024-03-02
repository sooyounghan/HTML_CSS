-----
### JSP 처리 과정
-----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d5e8fc42-75c3-453a-8e11-9b928f0549f5">
</div>

1. Client가 Web Broswer에서 URL을 입력
2. 요청된 URL에 대해 Domain Name Server에서 해당 Domain Name을 IP 주소로 변환
3. 변환된 IP 주소와 Port 번호, 그리고 해당하는 JSP 페이지에 대해 WAS(Web Aplication Server)에게 JSP 페이지 요청

       Port 8080은 Apache에서 사용되는 Port Number

4. WAS는 JSP/Servlet Container 내에서 해당하는 JSP 페이지를 요청
5. Servlet Container에서 JSP 파일을 java 파일로 번역(Servlet 파일)
6. java파일을 class 파일로 Complie [Servlet 파일]한 후, 실행 결과를 WAS에 전송
7. WAS에서 Web Browser에게 Buffer를 출력해 결과 페이지(HTML) 전송
8. HTML 태그를 분석하고, 변환하여 화면을 구성

