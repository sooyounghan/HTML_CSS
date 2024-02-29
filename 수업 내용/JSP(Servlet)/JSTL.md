-----
### jar 파일 추가
-----
: src - webapp - WEB-INF - lib

-----
### JSTL (Java Standard Tag Library)
-----
```jsp
<%@ taglib uri = "http://java.sun.com/jsp/jstl/core" %>
```
1. 항상 위의 태그가 붙어있어야 함

```jsp
<%@ taglib prefix="uri 주소를 대체할 접두사" uri="JSTL 태그 사용 주소"%>

<http://java.sun.com/jsp/jstl/core:out value = "내용"/>
```
```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%> <!-- uri 주소를 c로 대체 -->
<c:out value = "내용"/>
```

1. Core Tag : 변수 설정, 반복문, 조건문 에 해당하는 기능 제공
   + < c:out value = "내용" > Tag : 브라우저에 출력해주는 태그문
      - out.print(< %= % >) = < c:out value = "내용">

               out : JSP 내장 객체를 이용해 브라우저로 출력
               < c:out value = "내용" > : JSTL의 core의 out 태그를 이용해 브라우저 출력 (JSP 표현식 이용)
      - 예시) < c:out value = "${'<tag> , &'}" > : &{ }에서 ' '안에 내용을 브라우저에 출력 (1회성)

   + < c:set var = "변수명" scope = "영역" value = "값"> : var 이름에 해당하는 변수를 선언하고, 그 영역과 값을 지정
```jsp
<c:set var = "salary" scope = "session" value = "${2000*2}"/>
<c:out value = "${salary}"/>
```

       1. 변수 salary를 선언, 값은 ${2000*2} = 2000*2이며, scope는 범위로, session
       2. 즉, var = 2000*2; 와 동일하며, 그 영역은 session 영역까지 적용 가능

       
   + < c:remove var = "변수명" scope = "영역" value = "값"> : var에 해당하는 변수를 삭제
```jsp
<c:remove var = "salary"/>
```
   + < c:if test = "조건식" > 조건식이 참 < /c:if >: if문에 해당
```jsp
<c:if test = "${salary > 2000}">
<p>My salary is:  <c:out value = "${salary}"/><p>
</c:if>
```

  + < c:choose > ~ < /c : choose > : switch문
 
      - < c:when test = "조건식" > ~ < /c:when > : 조건식에 해당하면 진입
      - < c:otherwise > ~ < /c:otherwise > : 어떠한 조건식에도 일치하지 않으면, 진입 (else)
  ```jsp
<c:choose>
         
  <c:when test = "${salary <= 0}">
    Salary is very low to survive.
  </c:when>
         
  <c:when test = "${salary > 1000}">
     Salary is very good.
  </c:when>
         
  <c:otherwise>
     No comment sir...
  </c:otherwise>

</c:choose>
```

   + < c:forEach var = "변수명" begin = "시작포인트" end = "종료포인트" > ~ < /c:forEach > : 반복문 (시작 포인트 ~ 종료 포인트
```jsp
<c:forEach var = "i" begin = "1" end = "5">
      Item <c:out value = "${i}"/><p>
</c:forEach>
```

         다중 for문
```jsp
<c:forEach var = "i" begin = "1" end = "5">
   <c:forEach var = "j" begin = "1" end = "5">
      Item <c:out value = "${i, j}"/><p>
   </c:forEach>
</c:forEach>
```

  + < c:forTokens items = "값1, 값2, 값3,..." delims = "구분자", var = "name" > ~ < /c:forTokens > : 값들의 묶음에 대해 구분자로 구분해 변수명 var에 저장

                텍스트와 같이 대량의 데이터를 저장할 때 구분자로 사용
```jsp
<c:forTokens items = "Zara,nuha,roshy" delims = "," var = "name">
    <c:out value = "${name}"/><p>
</c:forTokens>
```

   + < c:param name = "name" value = "value"> : URL 태그와 import 태그가 동시에 사용되며, URI에 정보를 전송할 때, 해당 parameter를 같이 전송 (예제 참고)

```jsp
<c:url value = "/index.jsp" var = "myURL">
   <c:param name = "trackingId" value = "1234"/>
   <c:param name = "reportType" value = "summary"/>
</c:url>
<c:import url = "${myURL}"/>
```
      결과 : "/index.jsp?trackingId=1234;reportType=summary" : <c:param ..>의 정보가 같이 담김

2. Formmating Tage

         <%@ taglib prefix = "fmt" uri = "http://java.sun.com/jsp/jstl/fmt" %>

   - formatNumber
```jsp
      <h3>Number Format:</h3>
      <c:set var = "balance" value = "120000.2309" />
         
      <p>Formatted Number (1): <fmt:formatNumber value = "${balance}" type = "currency"/></p>

      <!-- 정수 세자리 -->
      <p>Formatted Number (2): <fmt:formatNumber type = "number" maxIntegerDigits = "3" value = "${balance}" /></p>

      <!-- 소수점 세자리 -->
      <p>Formatted Number (3): <fmt:formatNumber type = "number" maxFractionDigits = "3" value = "${balance}" /></p>

      <!-- 120,000에서 ,제거 -->
      <p>Formatted Number (4): <fmt:formatNumber type = "number" groupingUsed = "false" value = "${balance}" /></p>

      <!-- 100을 곱한 후 (%) 정수 세자리 %-->
      <p>Formatted Number (5): <fmt:formatNumber type = "percent" maxIntegerDigits="3" value = "${balance}" /></p>

      <!-- 100을 곱한 후 (%) 소수점 10자리 (빈공간은 0) %-->
      <p>Formatted Number (6): <fmt:formatNumber type = "percent" minFractionDigits = "10" value = "${balance}" /></p>

      <!-- 100을 곱한 후 (%) 정수 세자리 -->
      <p>Formatted Number (7): <fmt:formatNumber type = "percent" maxIntegerDigits = "3" value = "${balance}" /></p>

      <!-- pattern 형태로 표현-->
      <p>Formatted Number (8): <fmt:formatNumber type = "number" pattern = "###.###E0" value = "${balance}" /></p>
   
      <!-- 원화 표시 // setLocale vale = "지역" // type = "화폐 -->
      <p>Currency in USA : <fmt:setLocale value = "en_US"/> <fmt:formatNumber value = "${balance}" type = "currency"/>
```

   - formatDate
```jsp
      <h3>Date Number Format:</h3>
      <c:set var = "now" value = "<% = new java.util.Date()%>" />

      <!-- 현재 시간 출력 -->
      <p>Formatted Date (1): <fmt:formatDate type = "time" value = "${now}" /></p>

      <!-- 연월일 출력 -->      
      <p>Formatted Date (2): <fmt:formatDate type = "date" value = "${now}" /></p>

      <!-- 연월일, 현재시간 출력-->
      <p>Formatted Date (3): <fmt:formatDate type = "both" value = "${now}" /></p>

      <!-- 연월일, 현재시간 출력 2/29/24, 2:50 PM -->
      <p>Formatted Date (4): <fmt:formatDate type = "both" dateStyle = "short" timeStyle = "short" value = "${now}" /></p>

      <!-- 연월일, 현재시간 출력 Feb 29, 2024, 2:50:34 PM -->
      <p>Formatted Date (5): <fmt:formatDate type = "both" dateStyle = "medium" timeStyle = "medium" value = "${now}" /></p>

      <!-- 연월일, 현재시간 출력 February 29, 2024 at 2:50:34 PM KST -->
      <p>Formatted Date (6): <fmt:formatDate type = "both" dateStyle = "long" timeStyle = "long" value = "${now}" /></p>

      <!-- pattern에 맞게 출력 -->
      <p>Formatted Date (7): <fmt:formatDate pattern = "yyyy-MM-dd" value = "${now}" /></p>
```
