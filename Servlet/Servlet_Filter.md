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
### Servlet Filter 예제
-----
1. 다음과 같은 코드가 있다고 하자.
   
