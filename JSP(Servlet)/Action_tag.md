<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/508b2d26-c845-4076-b33a-6ebdb3e539b1">
</div>

-----
### jsp : include
-----
1. 위치한 부분에 지정한 페이지를 포함

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/107865b6-15e6-4f7a-8c30-c83e426d57ce">
</div>

      A. main.jsp가 웹 브라우저의 요청을 받음
      B. 출력 내용 A를 출력 버퍼에 저장
      C. <jsp:include>가 실행되면 실행 흐름을 sub.jsp로 이동
      D. 출력 내용 B를 출력 버퍼에 저장
      E. sub.jsp의 실행이 끝나면, 요청 흐름이 다시 main.jsp의 <jsp:include>로 회귀
      F. 이후 부분인 출력 내용 C를 버퍼에 저장
      G. 출력 버퍼의 내용을 응답 데이터로 전송

2. <jsp:include page = "포함할 페이지" autoflush = "true"/>
   - page : 포함할 JSP페이지의 경로 지정
   - flush : 지정한 JSP 페이지를 실행하기 전 출력 버퍼를 플러시할지 여부 결정 (기본값 : false)

         출력 버퍼를 flush하는 것은 출력 내용 A를 <jsp:include>가 실행하는 시점에 출력 버퍼의 내용을 flush하고,
         sub.jsp 페이지의 흐름으로 이동하는 것을 의미. 출력 버퍼의 내용을 flush하게 되면, http 응답 헤더가 웹 브라우저와
         함께 전송되므로, 이후 새롭게 추가되는 헤더 정보는 반영되지 않음

3. 공통 영역을 포함할 수 있음

-----
### jsp : param
-----
1. < jsp : inlcude > 태그를 이용해 포함할 JSP 페이지에 파라미터 추가 가능
2. 자식 태그로 추가하는 의미 (name과 value로 이름과 값을 포함 가능)

```jsp
<jsp:include page = "/top.jsp" flush = "false">
  <jsp:param name = "param1" value = "value1"/>
  <jsp:param name = "param2" value = "value2"/>
</jsp:include>
````

3. 이미 동일한 이름의 파라미터가 존재하면 기존 파라미터 값을 유지하며 새로운 값을 추가
<div align = "center">
<img width="808" alt="image (5)" src="https://github.com/sooyounghan/Web/assets/34672301/2c75beeb-bf0f-4c78-ad57-9fbff77780f5">
</div>

  - < jsp:param > 액션 태그로 추가한 파라미터가 기존 파라미터보다 우선
  - body_sub.jsp에서 request.getParameterValues("name") : 기존 값과 추가된 값 모두 출력
  - 단, < jsp : param > 으로 추가한 파라미터는 < jsp : include > 액션 태그로 포함한 페이지에서만 유효

4. < jsp:include > 액션 태그와 include Directive의 차이점
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/ab23d7b8-c468-42fe-aec1-af1790ca9b56">
</div>


-----
### jsp : forward
-----

-----
### jsp : useBean
-----

-----
### jsp : setProperty
-----

-----
### jsp : getProperty
-----
