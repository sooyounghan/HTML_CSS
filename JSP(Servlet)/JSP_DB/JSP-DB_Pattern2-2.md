-----
### Member Update
-----
1. Member Information JSP Page에 다음과 같은 기능 추가
   - Member Update
       + Email, H.P., Hobby, Job, 정보 수정 가능
       + Password를 일치 여부를 통해 정보를 수정하도록 설정
   - Member Delete
   - Member List
   - Member Join

-----
### Member Update 구현
-----

      Button onclick = "location.href='이동할 페이지명'"
      Update Page에서 기본 회원 정보 유지 : 결국 value 값에 저장된 값 선언
    
1. MemberUpdate JSP Page 생성
```jsp
<%@ page import="Model.Member, Model.MemberDAO"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<meta charset="UTF-8">
	<title>Member Update</title>
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
		
		.menu input {
			display:inline-block;
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
	
	<h2>Member Update</h2>
	
	<div>
	<table>
	<form action = "MemberUpdateProc.jsp" method = "post">
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
			<td><input type="email" name="email" value="<%=member.getEmail()%>" size="40" placeholder="Ex) abc@naver.com"></td>
		</tr>
		<tr>
			<td>H.P.</td>
			<td><input type="tel" name="tel" size="40" value="<%=member.getTel()%>" placeholder="Ex) 010-1234-5678"></td>
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
			<td><textarea rows="2" cols="40" name="info" placeholder = "Write Your Information."><%=member.getInfo()%></textarea></td>
		</tr>
		
		<tr class = "menu">
			<td colspan="2">
				<input type="submit" value="Member Update"></form>
			</td>
		</tr>	
	</table>
	</div>
</body>
</html>
```

2. MemberInfo JSP Page에 위 4가지 기능 추가
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
		
		.menu input {
			display:inline-block;
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
		
		<tr>
			<td colspan = "2">
				<button name = "update" onclick = "location.href='MemberUpdateForm.jsp?id=<%=member.getId()%>'">Update</button>
				<button name="memberDelete" onclick="location.href='MemberDeleteForm.jsp?id=<%=member.getId()%>'">Member Delete</button>
				<button name="memberList" onclick="location.href='MemberList.jsp'">Member List</button>
				<button name="memberJoin" onclick="location.href='MemberJoin.jsp'">Member Join</button>
			</td>
		</tr>
	</table>
	</div>
	
</body>
</html>
```
