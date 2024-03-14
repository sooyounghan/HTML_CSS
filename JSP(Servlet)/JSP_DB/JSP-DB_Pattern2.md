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

-----
### MemberList 작성 (SELECT 활용)
-----
1. MemberDAO클래스 (allMemberList (모든 유저 정보 가져오는 메서드) 추가)
```java
package Model;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.util.*;
import Model.MemberBean;

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
	
	// 모든 회원의 정보를 Return해주는 메서드
	public List<MemberBean> allMemberList() {
		List<MemberBean> memberList = new ArrayList<MemberBean>();
		
		try {
			
			// 1. Connection 연결
			getConn();
			
			conn = DriverManager.getConnection(url, id, password);
			
			// 2. SELECT Query 작성
			String sql = "SELECT * FROM MEMBER";
			pstmt = conn.prepareStatement(sql);
			
			// 3. SELECT Query의 결과를 ResultSet 객체로 받음
			rs = pstmt.executeQuery();
			
			// 4. ResultSet에 저장된 데이터를 추출 
			while(rs.next()) { // 4-1. 저장된 데이터만큼 까지 반복문 실행
				
				// 4-2. ArrayList memberList에 저장할 MemberBean 객체 생성
				MemberBean memberBean = new MemberBean();
				
				// 4-3. DB에서 받아온 값들을 Setter 함수를 통해 저장
				memberBean.setId(rs.getString(1));
				memberBean.setPass1(rs.getString(2));
				memberBean.setEmail(rs.getString(3));
				memberBean.setTel(rs.getString(4));
				memberBean.setHobby(rs.getString(5));
				memberBean.setJob(rs.getString(6));
				memberBean.setAge(rs.getString(7));
				memberBean.setInfo(rs.getString(8));
				
				// 4-4. ArrayList에 저장
				memberList.add(memberBean);
			}
			
			conn.close();
		} catch(Exception e) {
			
		}
		return memberList;
	}
}
```

2. MemberList.jsp (MemberList 출력 페이지)
```jsp
<%@ page import="Model.MemberBean, Model.MemberDAO, java.util.*"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
	
	<style>
	
	h2 {
	display:flex;
	flex-direction:row;
	justify-content:center; 
	align-items:center;
	}
	
	</style>
	
</head>

<body>
	<!-- 1. DB에서 모든 회원의 정보를 가져옴
		 2. HTML 태그를 이용해 화면에 회원정보 출력 -->

				
	<%
	MemberDAO mDAO = new MemberDAO();
	
	// 회원들의 정보가 얼마나 저장되어있는지 모르기에, 가변길이인 ArrayList 또는 Vector 이용
	List<MemberBean> memberList = mDAO.allMemberList();
	%>
	
	<h2>회원 가입</h2>
	<table border="1">
		<tr height="50">
			<td width="150" align="center">아이디</td>
			<td width="150" align="center">패스워드</td>
			<td width="150" align="center">이메일</td>
			<td width="150" align="center">전화 번호 </td>
			<td width="150" align="center">관심 분야</td>
			<td width="150" align="center">직업</td>
			<td width="150" align="center">연령</td>
			<td width="150" align="center">소개</td>
		</tr>
	<%
	for(int i = 0; i < memberList.size(); i++) {
		MemberBean member = memberList.get(i);

	%>
		<tr height="50">
			<td width="350" align="center"><%=member.getId()%></td>
			<td width="350" align="center"><%=member.getPass1()%></td>
			<td width="350" align="center"><%=member.getEmail()%></td>
			<td width="350" align="center"><%=member.getTel()%></td>
			<td width="350" align="center"><%=member.getHobby()%></td>				
			<td width="350" align="center"><%=member.getJob()%></td>
			<td width="350" align="center"><%=member.getAge()%></td>
			<td width="350" align="center"><%=member.getInfo()%></td>
		</tr>
		<%
	}
		%>
		
	</table>
</body>
</html>
```
-----
### 회원 상세보기 설정
-----
1. 회원의 아이디를 클릭하면, 그 회원에 대한 정보 출력
