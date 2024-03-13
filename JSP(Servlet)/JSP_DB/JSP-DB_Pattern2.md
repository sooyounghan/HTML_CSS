-----
### JSB-DB Pattern 2 : DAO(Data Access Object) 패턴 적용
-----
1. MemberDAO 패턴 적용
   - 데이터베이스에 접근할 memberDAO 자바 클래스를 생성
   - JSP가 이 클래스의 객체를 호출해서 하도록 설정

         - 현재, JSP 페이지 내에서 JAVA 코드를 삽입해 구현
         - memberBean이라는 외부 클래스를 통해서 JSP 페이지 내 데이터를 DB에 삽입

2. MemberDAO 클래스 생성
```java
package Model;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

/*
 * Oracle DB에 연결하고, SELECT, INSERT, DELETE, UPDATE 작업을 실행할 클래스
 */

public class MemberDAO {
	// Oracle 접속 소스 작성
	String id = "dbPractice"; // ID
	String password = "1234"; // 비밀번호
	String url = "jdbc:oracle:thin:@localhost:1521:xe"; // 접속 URL
	
	// DB에 접근할 수 있도록 도와주는 클래스의 객체
	Connection conn = null;
	
	// 데이터베이스에서 쿼리를 실행시켜줄 클래스의 객체
	PreparedStatement pstmt = null;
	
	// 데이터베이스에서 쿼리를 질의하여 받은 결과를 Return하여 이를 저장할 클래스의 객체
	ResultSet rs = null;
	
	/*
	 * DB에 접근할 수 있도록 도와주는 메서드 
	 */
	public void getConn() {
		try {
			// 1. 해당 데이터 베이스 사용하는 것을 선언 (클래스 등록 = 오라클 사용)
			Class.forName("oracle.jdbc.driver.OracleDriver");
			
			// 2. 해당 데이터 베이스에 접속
			conn = DriverManager.getConnection(url, id, password);
			
		} catch(Exception e) {
			
		}
	}
	
	// DB에 한 사람의 회원 정보를 저장하는 메서드
	public void insertMember(MemberBean memberBean) {
		// 3. 접속 후 쿼리를 준비
		try {
			// getConn() 메서드 호출
			getConn();
			
			String sql = "INSERT INTO MEMBER VALUES(?, ?, ?, ?, ?, ?, ?, ?)";
		
			// 4. 쿼리를 사용하도록 설정
			pstmt = conn.prepareStatement(sql);
			
			// 5. ?에 맞게 데이터를 변경
			pstmt.setString(1, memberBean.getId());
			pstmt.setString(2, memberBean.getPass1());
			pstmt.setString(3, memberBean.getEmail());
			pstmt.setString(4, memberBean.getTel());
			pstmt.setString(5, memberBean.getHobby());
			pstmt.setString(6, memberBean.getJob());
			pstmt.setString(7, memberBean.getAge());
			pstmt.setString(8, memberBean.getInfo());
		
			pstmt.executeUpdate();
			
			conn.close();
		} catch(Exception ex) { 
		
		}
	}
}
```

3. MemberJoinProc.jsp 페이지 변경 (SQL 처리 문장 간소화)
```jsp
<%@page import="Model.MemberDAO"%>
<%@page import="java.sql.PreparedStatement"%>
<%@page import="java.sql.DriverManager"%>
<%@page import="java.sql.Connection"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
</head>

<body>
<%
	String[] hobby = request.getParameterValues("hobby"); // hobby는 배열 단위로 받으므로 이를 처리
	
	String text_hobby = ""; // String 하나로 처리
	for(int i = 0; i < hobby.length; i++) {
		text_hobby += hobby[i] + " ";
	}
%>

<!-- useBean을 이용해 한꺼번에 데이터를 받음 -->
<jsp:useBean id="memberBean" class = "Model.MemberBean">
	<jsp:setProperty name = "memberBean" property ="*"/>
</jsp:useBean>

<%
	memberBean.setHobby(text_hobby); // String형으로 완성된 hobby를 다시 MemberBean 객체에 저장

	// 1. 데이터베이스 객체 생성
	MemberDAO mDAO = new MemberDAO();
		
	// 2. DB에 데이터 삽입
	mDAO.insertMember(memberBean);
%>

	오라클 접속 완료
</body>
</html>
```

