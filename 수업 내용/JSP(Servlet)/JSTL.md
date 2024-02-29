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
