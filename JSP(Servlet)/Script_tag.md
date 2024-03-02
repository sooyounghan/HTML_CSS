-----
### 스크립트릿 (Scriptlet)
-----
1. 일반적으로 JSP페이지에서 가장 많이 쓰이는 스크립트 요소
2. Scriptlet에서 선언한 변수는 JSP 페이지가 Servlet으로 변환될 때 지역 변수로 사용 [Servlet에서 service() 메서드 내에서 변환]

```jsp
<%
  자바코드;
  자바코드;
%>
```

-----
### 선언문 (Declaration)
-----
1. 일반적으로 JSP페이지에서 자바의 멤버 변수 또는 멤버 메서드로 사용하고자 할 때 주로 사용
2. 선언문의 변수는 Servlet으로 변환될 때 멤버 변수로 변환 / 메서드는 Servlet에서 메서드로 만들어짐 [Servlet에서 service() 메서드 내에서 변환]

```jsp
<%!
  int a = 100;

  public int sum(int a, int b) {
    return a + b;
  }
%>
```

-----
### 표현식 (Expression)
-----
1. 일반적으로 JSP 페이지에서 자바의 System.out.println()과 유사하게 사용
2. 데이터를 출력할 때 주로 사용

```jsp
<%= 값%>
```

