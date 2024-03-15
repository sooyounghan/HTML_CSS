-----
### JSB-DB Pattern 2 : DAO(Data Access Object) 패턴 적용
-----
1. MemberDAO Pattern 적용
   - 데이터베이스 작업을 처리할 MemberDAO Class를 생성
   - JSP는 MemberDAO Class 객체를 통해 DB 작업을 처리 하도록 설정

         - Pattern1은 JSP 페이지 내에서 JAVA 코드를 삽입해 구현
      
2. MemberDAO Class 생성
```java
package Model;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

/*
 * Oracle DB 연결 및 SELECT, INSERT, DELETE, UPDATE 작업, 즉 DB에 접근하고 처리할 DAO 클래스
 */

public class MemberDAO {
	// Oracle 접속 
	String id = "dbPractice"; // DB ID
	String password = "1234"; // DB Password
	String url = "jdbc:oracle:thin:@localhost:1521:xe"; // DB Connect URL
	
	// DB에 접근 클래스 객체
	Connection conn = null;
	
	// 데이터베이스 쿼리 처리 클래스 객체
	PreparedStatement pstmt = null;
	
	// 데이터베이스에서 쿼리 질의 후, 받은 결과에 대해 클래스 객체
	ResultSet rs = null;
	
	/*
	 * DB 연결
	 */
	public void getConnection() {
		try {
			
			// 1. 데이터 베이스 사용 선언
			Class.forName("oracle.jdbc.driver.OracleDriver");
			
			// 2. 데이터 베이스 접속
			conn = DriverManager.getConnection(url, id, password);
			
		} catch(Exception e) {
			
			e.printStackTrace();
			
		}
	}
	
	/*
	 *  DB에 한 사람의 회원 정보 삽입
	 */
	public void insertMember(Member member) {
		try {
			
			getConnection();
			
			String sql = "INSERT INTO MEMBER VALUES(?, ?, ?, ?, ?, ?, ?, ?)";
		
			pstmt = conn.prepareStatement(sql);
			
			pstmt.setString(1, member.getId());
			pstmt.setString(2, member.getPass1());
			pstmt.setString(3, member.getEmail());
			pstmt.setString(4, member.getTel());
			pstmt.setString(5, member.getHobby());
			pstmt.setString(6, member.getJob());
			pstmt.setString(7, member.getAge());
			pstmt.setString(8, member.getInfo());
		
			pstmt.executeUpdate();
			
			conn.close();
			
		} catch(Exception e) { 
			
			e.printStackTrace();
			
		}
	}
}
```

3. MemberJoinProc JSP Page (SQL 처리 문장 간소화)
```jsp
<%@page import="Model.MemberDAO, java.sql.PreparedStatement, java.sql.DriverManager, java.sql.Connection"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>

<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Member Join Processing</title>
</head>

<body>
<%
	String[] hobby = request.getParameterValues("hobby"); // Hobby : Multi-choice, 배열 단위
	
	String text_hobby = ""; // Hobby를 하나의 String으로 결합
	for(int i = 0; i < hobby.length; i++) {
		text_hobby += hobby[i] + " ";
	}
%>

<!-- useBean : MemberJoin Data 저장 -->
<jsp:useBean id="member" class = "Model.Member">
	<jsp:setProperty name = "member" property ="*"/>
</jsp:useBean>

<%
	member.setHobby(text_hobby); // 하나의 String으로 결합된 Hobby를 Member 객체에 저장

	// 1. 데이터베이스 객체 생성
	MemberDAO mDAO = new MemberDAO();
		
	// 2. DB에 데이터 삽입
	mDAO.insertMember(member);
	
	// 3. 회원 가입이 되었으면, 회원 정보 페이지로 이동 시킴
	response.sendRedirect("MemberList.jsp");
%>
</body>
</html>
```

-----
### MemberList 작성 (SELECT 활용)
-----
1. MemberDAO Class (allMemberList : 모든 유저 정보 데이터를 가져오는 메서드)
```java
package Model;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.util.*;

/*
 * Oracle DB 연결 및 SELECT, INSERT, DELETE, UPDATE 작업, 즉 DB에 접근하고 처리할 DAO 클래스
 */

public class MemberDAO {
	// Oracle 접속 
	String id = "dbPractice"; // DB ID
	String password = "1234"; // DB Password
	String url = "jdbc:oracle:thin:@localhost:1521:xe"; // DB Connect URL
	
	// DB에 접근 클래스 객체
	Connection conn = null;
	
	// 데이터베이스 쿼리 처리 클래스 객체
	PreparedStatement pstmt = null;
	
	// 데이터베이스에서 쿼리 질의 후, 받은 결과에 대해 클래스 객체
	ResultSet rs = null;
	
	/*
	 * DB 연결
	 */
	public void getConnection() {
		try {
			
			// 1. 데이터 베이스 사용 선언
			Class.forName("oracle.jdbc.driver.OracleDriver");
			
			// 2. 데이터 베이스 접속
			conn = DriverManager.getConnection(url, id, password);
			
		} catch(Exception e) {
			
			e.printStackTrace();
			
		}
	}
	
	/*
	 *  DB에 한 사람의 회원 정보 삽입
	 */
	public void insertMember(Member member) {
		try {
			
			getConnection();
			
			String sql = "INSERT INTO MEMBER VALUES(?, ?, ?, ?, ?, ?, ?, ?)";
		
			pstmt = conn.prepareStatement(sql);
			
			pstmt.setString(1, member.getId());
			pstmt.setString(2, member.getPass1());
			pstmt.setString(3, member.getEmail());
			pstmt.setString(4, member.getTel());
			pstmt.setString(5, member.getHobby());
			pstmt.setString(6, member.getJob());
			pstmt.setString(7, member.getAge());
			pstmt.setString(8, member.getInfo());
		
			pstmt.executeUpdate();
			
			conn.close();
			
		} catch(Exception e) { 
			
			e.printStackTrace();
			
		}
	}
	
	/*
	 * 모든 회원 정보 확인
	 */
	public List<Member> allMemberList() {
		List<Member> memberList = new ArrayList<Member>();
		
		try {
			
			getConnection();
			
			String sql = "SELECT * FROM MEMBER";
			pstmt = conn.prepareStatement(sql);
			
			rs = pstmt.executeQuery();
			
			while(rs.next()) { // 1. 저장된 데이터만큼 까지 반복문 실행
				
				// 2. memberList에 저장할 Member 객체 생성
				Member member = new Member();
				
				// 3. DB 처리 결과를 Member Setter로 DB 처리 결과 저장
				member.setId(rs.getString(1));
				member.setPass1(rs.getString(2));
				member.setEmail(rs.getString(3));
				member.setTel(rs.getString(4));
				member.setHobby(rs.getString(5));
				member.setJob(rs.getString(6));
				member.setAge(rs.getString(7));
				member.setInfo(rs.getString(8));
				
				memberList.add(member);
			}
			
			conn.close();
			
		} catch(Exception e) {
			
			e.printStackTrace();
			
		}
		
		return memberList;
	}
}
```

2. MemberList JSP Page
```jsp
<%@ page import="Model.Member, Model.MemberDAO, java.util.*"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>

<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
	<title>Member List</title>
	
	<style>	
	
		h2 {
			display:flex;
			flex-direction:row;
			justify-content:center; 
			align-items:center;
		}
		
		div {
			display:flex;
			flex-direction:row;
			justify-content:center; 
			align-items:center;
		}
		
		table {
			width:600px;
			height:150px;
			text-align:center;
			border:1px solid black;
		}
		
		td, tr {
			border:1px solid black;
			font-size:13px;
		}
		
		a {
			color:black;
			font-weight:600;
			text-decoration:none;
		}
	
	</style>
	
</head>

<body>

	<!-- 1. DB에서 모든 회원의 정보
		 2. 화면에 회원정보 출력 -->
	<%
	MemberDAO mDAO = new MemberDAO();
	
	// ArrayList 또는 Vector 이용
	List<Member> memberList = mDAO.allMemberList();
	
	%>
	
	<h2>All Member Information</h2>
	
	<div>
	<table>
		<tr>
			<td>ID</td>
			<td>Password</td>
			<td>Email</td>
			<td>H.P.</td>
		</tr>
		
	<%
	
	for(int i = 0; i < memberList.size(); i++) {
		Member member = memberList.get(i);

	%>
		<tr>
			<td>
			<td><%=member.getPass1()%></td>
			<td><%=member.getEmail()%></td>
			<td><%=member.getTel()%></td>
		</tr>
		<%
		
	}
	
		%>
		
	</table>
	</div>
		
</body>
</html>
```
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/9dcafc25-3f91-44f0-ad95-571f3421c4ca">
</div>

-----
### 회원 상세보기 설정
-----
1. 회원의 아이디를 클릭하면, 그 회원에 대한 정보 출력 (MemberList → MemberInfo)
   
2. MemberList JSP Page
```jsp
<%@ page import="Model.Member, Model.MemberDAO, java.util.*"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>

<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
	<title>Member List</title>
	
	<style>	
	
		h2 {
			display:flex;
			flex-direction:row;
			justify-content:center; 
			align-items:center;
		}
		
		div {
			display:flex;
			flex-direction:row;
			justify-content:center; 
			align-items:center;
		}
		
		table {
			width:600px;
			height:150px;
			text-align:center;
			border:1px solid black;
		}
		
		td, tr {
			border:1px solid black;
			font-size:13px;
		}
		
		a {
			color:black;
			font-weight:600;
			text-decoration:none;
		}
	
	</style>
	
</head>

<body>

	<!-- 1. DB에서 모든 회원의 정보
		 2. 화면에 회원정보 출력 -->
	<%
	MemberDAO mDAO = new MemberDAO();
	
	// ArrayList 또는 Vector 이용
	List<Member> memberList = mDAO.allMemberList();
	
	%>
	
	<h2>All Member Information</h2>
	
	<div>
	<table>
		<tr>
			<td>ID</td>
			<td>Password</td>
			<td>Email</td>
			<td>H.P.</td>
		</tr>
		
	<%
	
	for(int i = 0; i < memberList.size(); i++) {
		Member member = memberList.get(i);

	%>
		<tr>
			<td>
			<!-- 회원 ID를 클릭하면, 그 회원의 정보 페잊지로 이동 -->
			<a href = "MemberInfo.jsp?id=<%=member.getId()%>"><%=member.getId()%></a></td>
			<td><%=member.getPass1()%></td>
			<td><%=member.getEmail()%></td>
			<td><%=member.getTel()%></td>
		</tr>
		<%
		
	}
	
		%>
		
	</table>
	</div>
		
</body>
</html>
```

3. MemberDAO Class에 한 회원에 대한 정보를 볼 수 있는 oneMemberList 구현
```java
package Model;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.util.*;

/*
 * Oracle DB 연결 및 SELECT, INSERT, DELETE, UPDATE 작업, 즉 DB에 접근하고 처리할 DAO 클래스
 */

public class MemberDAO {
	// Oracle 접속 
	String id = "dbPractice"; // DB ID
	String password = "1234"; // DB Password
	String url = "jdbc:oracle:thin:@localhost:1521:xe"; // DB Connect URL
	
	// DB에 접근 클래스 객체
	Connection conn = null;
	
	// 데이터베이스 쿼리 처리 클래스 객체
	PreparedStatement pstmt = null;
	
	// 데이터베이스에서 쿼리 질의 후, 받은 결과에 대해 클래스 객체
	ResultSet rs = null;
	
	/*
	 * DB 연결
	 */
	public void getConnection() {
		try {
			
			// 1. 데이터 베이스 사용 선언
			Class.forName("oracle.jdbc.driver.OracleDriver");
			
			// 2. 데이터 베이스 접속
			conn = DriverManager.getConnection(url, id, password);
			
		} catch(Exception e) {
			
			e.printStackTrace();
			
		}
	}
	
	/*
	 *  DB에 한 사람의 회원 정보 삽입
	 */
	public void insertMember(Member member) {
		try {
			
			getConnection();
			
			String sql = "INSERT INTO MEMBER VALUES(?, ?, ?, ?, ?, ?, ?, ?)";
		
			pstmt = conn.prepareStatement(sql);
			
			pstmt.setString(1, member.getId());
			pstmt.setString(2, member.getPass1());
			pstmt.setString(3, member.getEmail());
			pstmt.setString(4, member.getTel());
			pstmt.setString(5, member.getHobby());
			pstmt.setString(6, member.getJob());
			pstmt.setString(7, member.getAge());
			pstmt.setString(8, member.getInfo());
		
			pstmt.executeUpdate();
			
			conn.close();
			
		} catch(Exception e) { 
			
			e.printStackTrace();
			
		}
	}
	
	/*
	 * 모든 회원 정보 확인
	 */
	public List<Member> allMemberList() {
		List<Member> memberList = new ArrayList<Member>();
		
		try {
			
			getConnection();
			
			String sql = "SELECT * FROM MEMBER";
			pstmt = conn.prepareStatement(sql);
			
			rs = pstmt.executeQuery();
			
			while(rs.next()) { // 1. 저장된 데이터만큼 까지 반복문 실행
				
				// 2. memberList에 저장할 Member 객체 생성
				Member member = new Member();
				
				// 3. DB 처리 결과를 Member Setter로 DB 처리 결과 저장
				member.setId(rs.getString(1));
				member.setPass1(rs.getString(2));
				member.setEmail(rs.getString(3));
				member.setTel(rs.getString(4));
				member.setHobby(rs.getString(5));
				member.setJob(rs.getString(6));
				member.setAge(rs.getString(7));
				member.setInfo(rs.getString(8));
				
				memberList.add(member);
			}
			
			conn.close();
			
		} catch(Exception e) {
			
			e.printStackTrace();
			
		}
		
		return memberList;
	}
	
	/*
	 * 한 회원 정보 확인
	 */
	public Member oneMemberList(String id) {
		Member member = new Member();
		
		try {
			
			getConnection();
			
			String sql = "SELECT * FROM MEMBER WHERE ID = ?";
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, id);
			
			rs = pstmt.executeQuery();
			
			if(rs.next()) {
				member.setId(rs.getString(1));
				member.setPass1(rs.getString(2));
				member.setEmail(rs.getString(3));
				member.setTel(rs.getString(4));
				member.setHobby(rs.getString(5));
				member.setJob(rs.getString(6));
				member.setAge(rs.getString(7));
				member.setInfo(rs.getString(8));
			}
			
			conn.close();
			
		} catch(Exception e) {
			
			e.printStackTrace();
			
		}
		
		return member;
	}
}
```

4. 한 회원 정보를 볼 수 있는 MemberInfo JSP Page 생성
```jsp
<%@page import="Model.Member, Model.MemberDAO"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>

<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Member Information</title>

	<style>
	
		h2 {
		display:flex;
		flex-direction:row;
		justify-content:center; 
		align-items:center;
		}
		
		div {
			display:flex;
			flex-direction:row;
			justify-content:center; 
			align-items:center;
		}
		
		table {
			width:600px;
			height:300px;
			text-align:center;
			border:1px solid black;
		}
		
		td, tr {
			border:1px solid black;
			font-size:13px;
		}
		
	</style>

</head>

<body>

	<%
	// 1. MemberList에서 통해 전달받은 ID 값 받기
	String id = request.getParameter("id");
	
	// 2. 데이터베이스에서 한 회원의 정보를 가져옴
	MemberDAO mDAO = new MemberDAO();
	
	// 3. 해당하는 ID의 회원 정보 반환
	Member member = mDAO.oneMemberList(id); 
	%>
	<!-- 3. Table 태그를 이용해 화면에 회원의 정보 출력 -->
	
	<h2>Member Information</h2>
	
	<div>
	<table>
		<tr>
			<td>ID</td>
			<td><%=member.getId() %></td>
		</tr>
		<tr>
			<td>PassWord</td>
			<td><%=member.getPass1() %></td>
		</tr>
		<tr>
			<td>Email</td>
			<td><%=member.getEmail() %></td>
		</tr>
		<tr>
			<td>H.P.</td>
			<td><%=member.getTel() %></td>
		</tr>
		<tr>
			<td>Hobby</td>
			<td><%=member.getHobby() %></td>
		</tr>
		<tr>
			<td>Job</td>
			<td><%=member.getJob() %></td>
		</tr>
		<tr>
			<td>Age</td>
			<td><%=member.getAge() %></td>
		</tr>
		<tr>
			<td>Info.</td>
			<td><%=member.getInfo() %></td>
		</tr>
	</table>
	</div>
	
</body>
</html>
```
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/cc257690-c351-4f30-8a78-ac2f7e1a05b5">
</div>

