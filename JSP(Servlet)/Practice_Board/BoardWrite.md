-----
### BoardWrite 구조
-----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7fa771ee-15c1-4367-a6da-602e3d839cbe">
</div>

-----
### BoardWriteForm
-----
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Board Write Form</title>

	<style>
		* {
			box-sizing:border-box;
		}
		
		h2 {
			text-align:center;
			font-size:20px;
			font-weight:600;
		}

		.wrapper {
			width:100%;
			display:flex;
			flex-direction:row;
			justify-content:center;
			align-items:center;
						
		}
				
		.container {
			width:600px;
			display:flex;
			flex-direction:column;
			justify-content:center;
			align-items:center;
			
			border:3px solid black;
		}
		
		.form {
			width:100%;		
			height:50px;
			
			display:flex;
			flex-direction:row;
			justify-content:flex-start;
			align-items:center;
			
			border:1px solid black;
		}
		
		.writer_name, .password_name, .email_name, .title_name, .content_name {
			padding:10px;
			width:100px;
			display:flex;
			flex-direction:row;
			justify-content:center;
			align-items:center;
		}
		
		.content_form {
			height:200px;
		}
		
		.writer, .password, .email, .title, .content {
			width:100%;
			text-area:center;
			
			display:flex;
			flex-direction:row;
			justify-content:center;
			align-items:center;
		}
		
		input {
			width:50%;
			border:none;
			border-bottom:1px solid black;
		}
		
		textarea {
			width:75%;
			height:50%;
			resize:none;
			border:1px solid black;
		}
		
		.button_zip {
			display:flex;
			flex-direction:row;
			justify-content:center;
			align-items:center;
		}
		
		.button {
			margin:10px;
			display:inline-block;
			width:100px;
			height:30px;
			border:2px solid black;
		}
	</style>
</head>

<body>
	<h2> Board </h2>
	
	<div class = "wrapper">
	<form action = "BoardWriteProc.jsp" method = "post">
		<div class = "container">
			<div class = "writer_form form">
				<div class = "writer_name">Writer</div>
				<div class = "writer">
				<input type = "text" name = "writer" required = "required"/>
				</div>
			</div>
			
			<div class = "password_form form">
				<div class = "password_name">Password</div>
				<div class = "password">
				<input type = "password" name = "password" required = "required"/>
				</div>
			</div>
			
			<div class = "title_form form">
				<div class = "title_name">Title</div>
				<div class = "title">
				<input type = "text" name = "subject" required = "required"/>
				</div>
			</div>
			
			<div class = "email_form form">
				<div class = "email_name">Email</div>
				<div class = "email">
				<input type = "email" name = "email"/>
				</div>
			</div>
			
			<div class = "content_form form">
				<div class = "content_name">Content</div>
				<div class = "content">
				<textarea name = "content" rows = "10"></textarea>
				</div>
			</div>
		</div>
		<div class="button_zip">
			<input type="submit" class="button" value="Write">
			<input type="reset" class="button" value="Reset"></form>
			<button class="button" onclick="location.href='BoardList.jsp'">Board List</button>
		</div>
	</div>
</body>
</html>
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/afc1d7d7-d3d0-4235-b8eb-f91cc085fc22">

</div>

-----
### BoardWriteProcessing JSP Page (DB 전송만 구현)
-----
```jsp
<%@page import="Board.BoardDAO"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Board Write Processing</title>
</head>

<body>

<!-- 게시글에 작성한 데이터를 불러옴 -->
<jsp:useBean id="board" class="Board.Board">
	<jsp:setProperty name="board" property="*"/>
</jsp:useBean>

<%
	// DB쪽으로 데이터 전송
	BoardDAO boardDAO = new BoardDAO();

	// DB에 데이터 삽입
	boardDAO.insertBoard(board);
%>
</body>
</html>
```

-----
### BoardDAO (insertBoard만 구현)
-----
```java
package Board;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.sql.DataSource;

public class BoardDAO {
	Connection conn = null;
	PreparedStatement pstmt = null;
	ResultSet rs = null;
	
	public void getConnection() {
		try {
			Context initcnx = new InitialContext();
			Context envcnx = (Context)initcnx.lookup("java:comp/env");
			
			DataSource ds = (DataSource)envcnx.lookup("jdbc/pool");
			
			conn = ds.getConnection();
			
		} catch(Exception e) {
			e.printStackTrace();
		}
	}
	
	/*
	 * 새로운 게시글 하나 추가하는 메서드
	 */
	public void insertBoard(Board board) {
		int ref = 0; // 글 그룹 의미 (Query를 실해시켜 가장 큰 REF 값을 가져온 후 1 증가)
		int re_step = 1; // 새로운 글의 re_step은 1
		int re_level = 1; // 새로운 글이므로 re_level은 1
		
		try {
			getConnection();
			
			// 가장 큰 REF를 읽어오는 Query
			String refsql = "SELECT MAX(REF) FROM BOARD";
			
			pstmt = conn.prepareStatement(refsql);
			
			rs = pstmt.executeQuery();
			
			if(rs.next()) {
				//최댓값에 1을 더해서 글 그룹 설정
				ref = rs.getInt(1) + 1;
			}
			
			// 게시글 전체 데이터를 DB에 전송
			String sql = "INSERT INTO BOARD VALUES(BOARD_SEQ.NEXTVAL, ?, ?, ?, ?, SYSDATE, ?, ?, ?, 0, ?)";
			pstmt = conn.prepareStatement(sql);
			
			pstmt.setString(1, board.getWriter());
			pstmt.setString(2, board.getEmail());
			pstmt.setString(3, board.getSubject());
			pstmt.setString(4, board.getContent_password());
			pstmt.setInt(5, ref);
			pstmt.setInt(6, re_step);
			pstmt.setInt(7, re_level);
			pstmt.setString(8, board.getContent());
			
			pstmt.executeUpdate();
			
			conn.close();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

```
