-----
### Member TABLE
-----
1. 기존 MEMBER TABLE 이용
```sql
CREATE TABLE MEMBER (
ID VARCHAR2(10) CONSTARINT MEMBER_ID_PK PRIMARY KEY,
PASS1 VARCHAR2(20) NOT NULL,
EMAIL VARCHAR2(50),
TEL VARCHAR2(20),
HOBBY VARCHAR2(60), 
JOB VARCHAR2(15),
AGE VARCHAR2(10), 
INFO VARCHAR(500)
);
```
  - 테이블 구성도 (테이블, 제약조건, ERD)
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/410843ba-a97e-452a-828e-4c6873b073af">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f9d7a9a2-3b5b-42af-bbc7-5a8653eb8346">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9e1b9584-3055-499e-a214-498a8e480463">
</div>

2. 기존 MEMBER 정보
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/3b9ada04-bdd8-45c1-ae10-849269564730">
</div>

-----
### MemberLogin JSP Page
-----
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Member Login Page</title>
	<style>
	* {
    box-sizing:border-box;
    padding:0;
    margin:0;
	}
	
	.login_div {
	    display:flex;
	    flex-direction:rpw;
	    justify-content:center;
	    align-items:center;
	}
	
	.login_form {
	    width:300px;
	    height:300px;
	    border:3px solid gray;
	    border-radius:10%;
		text-align:center;
	    display:flex;
	    flex-direction:column;
	    justify-content:space-around;
	    align-items:center;
	}
	
	.login_menu {
	    width:20%;
	    font-size:20px;
	    font-weight:600;
	}
	
	.login_select {
	    width:80%;
	    height:100px;
	
	    display:flex;
	    flex-direction:row;
	    flex-wrap:wrap;
	    justify-content:center;
	    align-content:space-around;
	}
	
	.login_id, .login_pwd {
	    width:100%;
	
	    display:flex;
	    flex-direction:row;
	    justify-content:flex-start;
	    align-content:center;
	}
	
	.login_id_menu, .login_pwd_menu {
	    font-size:13px;
	    font-weight:600;
	    padding:0 15px;
	    width:50px;
	}
	
	.login_id_input, .login_pwd_input {
	    padding-left:30px;
	}
	
	.login_button {
	    width:100%;
	    height:50px;
	
	    display:flex;
	    flex-direction:row;
	    flex-wrap:wrap;
	    justify-content:center;
	    align-content:center;
	}
	
	.id, .pwd {
	    width:calc(100%);
	}
	
	.login_button_input {
	    border:2px solid black;
	    width:50px;
	    height:30px;
	}
	</style>
</head>

<body>
	<form action="MemberLoginProc.jsp" method="post">
	<div class="login_div">
    <div class="login_form">
        <div class="login_menu">Login</div>
        <div class="login_select">
            <div class="login_id">
                <div class="login_id_menu">ID</div>
                <div class="login_id_input">
                    <input type="text" class="id" name="id" placeholder="ID 입력">
                </div>
            </div>
            <div class="login_pwd">
                <div class="login_pwd_menu">PassWord</div>
                <div class="login_pwd_input">
                    <input type="password" class="pwd" name="pwd" placeholder="PassWord 입력"></div>
            </div>
        </div>
        <div class="login_button">
            <input type="submit" class="login_button_input" value="Login">
        </div>
    </div>
    </div>
    </form>
</body>
</html>
```

-----
### MemberLoginProc JSP Page
-----
```jsp
<%@page import="RentCar.RentCarDAO"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Member Login Processing</title>
</head>

<body>
	<%
		String id = request.getParameter("id");
		String password = request.getParameter("pwd");
		
		RentCarDAO rentCarDAO = new RentCarDAO();
		
		// 해당 회원의 여부를 숫자로 확인
		int result = rentCarDAO.getMember(id, password);
		
		if(result == 0) {
	%>			
			<script>
				alert("Not Match ID or Password");
				location.href="RentCarMain.jsp?center=MemberLogin.jsp"
			</script>
	<%
		} else {
			session.setAttribute("id", id);
			response.sendRedirect("RentCarMain.jsp");
		}
	%>
	
</body>
</html>
```

-----
### RentCarDAO Class - getMember 구현
-----
```java
package RentCar;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.*;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.sql.DataSource;

public class RentCarDAO {
	
	Connection conn = null;
	PreparedStatement pstmt = null;
	ResultSet rs = null;
	
	public void getConnection() {
		try {
			Context initcnx = new InitialContext();
			Context envcnx = (Context)initcnx.lookup("java:comp/env");
			DataSource ds = (DataSource)envcnx.lookup("jdbc/pool");
			
			conn = ds.getConnection();
		} catch(NamingException e) {
			e.printStackTrace();
		} catch(SQLException e) {
			e.printStackTrace();
		}
	}
	
	/*
	 * 상위 3개의 Car List 추출
	 */
	public List<CarList> getSelectCar() {
		List<CarList> carList = new ArrayList<CarList>();
		
		try {
			getConnection();
			
			String sql = "SELECT * FROM RENTCAR ORDER BY NO DESC";
			pstmt = conn.prepareStatement(sql);
			
			rs = pstmt.executeQuery();

			int count = 0; // 상위 3개 상품 출력을 위해 설정
			while(rs.next()) {	
				CarList car = new CarList();
				
				car.setNo(rs.getInt(1));
				car.setName(rs.getString(2));
				car.setCategory(rs.getInt(3));
				car.setPrice(rs.getInt(4));
				car.setUsepeople(rs.getInt(5));
				car.setCompany(rs.getString(6));
				car.setImg(rs.getString(7));
				car.setInfo(rs.getString(8));
				
				carList.add(car);
				
				count++;
				if(count >= 3) break;
			}
			
			conn.close();
		} catch(SQLException e) {
			e.printStackTrace();
		}
		return carList;
	}
	
	/*
	 * Category별 CarList 추출
	 */
	public List<CarList> getCategoryCar(int category) {
		List<CarList> carList = new ArrayList<CarList>();
		
			try {
				getConnection();
				
				String sql = "SELECT * FROM RENTCAR WHERE CATEGORY = ?";
				pstmt = conn.prepareStatement(sql);
				pstmt.setInt(1, category);
				rs = pstmt.executeQuery();
				
				while(rs.next()) {
					CarList car = new CarList();
					
					car.setNo(rs.getInt(1));
					car.setName(rs.getString(2));
					car.setCategory(rs.getInt(3));
					car.setPrice(rs.getInt(4));
					car.setUsepeople(rs.getInt(5));
					car.setCompany(rs.getString(6));
					car.setImg(rs.getString(7));
					car.setInfo(rs.getString(8));
					
					carList.add(car);
				}
				
				conn.close();
			} catch(SQLException e) {
				e.printStackTrace();
			}
		return carList;
	}
	
	/*
	 * 모든 CarList 추출
	 */
	public List<CarList> getAllListCar() {
		List<CarList> carList = new ArrayList<CarList>();
		
			try {
				getConnection();
				
				String sql = "SELECT * FROM RENTCAR";
				pstmt = conn.prepareStatement(sql);
				rs = pstmt.executeQuery();
				
				while(rs.next()) {
					CarList car = new CarList();
					
					car.setNo(rs.getInt(1));
					car.setName(rs.getString(2));
					car.setCategory(rs.getInt(3));
					car.setPrice(rs.getInt(4));
					car.setUsepeople(rs.getInt(5));
					car.setCompany(rs.getString(6));
					car.setImg(rs.getString(7));
					car.setInfo(rs.getString(8));
					
					carList.add(car);
				}
				
				conn.close();
			} catch(SQLException e) {
				e.printStackTrace();
			}
		return carList;
	}
	
	/*
	 * 하나의 Car 정보 추출
	 */
	public CarList getOneCarList(int no) {
		CarList car = new CarList();
		
		try {
			getConnection();
			
			String sql = "SELECT * FROM RENTCAR WHERE NO = ?";
			pstmt = conn.prepareStatement(sql);
			
			pstmt.setInt(1, no);
			
			rs = pstmt.executeQuery();
			
			if(rs.next()) {
				car.setNo(rs.getInt(1));
				car.setName(rs.getString(2));
				car.setCategory(rs.getInt(3));
				car.setPrice(rs.getInt(4));
				car.setUsepeople(rs.getInt(5));
				car.setCompany(rs.getString(6));
				car.setImg(rs.getString(7));
				car.setInfo(rs.getString(8));
			}
			
			conn.close();
		} catch(SQLException e) {
			e.printStackTrace();
		}
		return car;
	}
	
	/*
	 * 로그인 처리를 위한 회원 ID와 PassWord를 추출
	 */
	public int getMember(String id, String password) {
		int result = 0;
		
		try {
			getConnection();
			
			// 일치하면 1, 불일치하면 0 
			String sql = "SELECT COUNT(*) FROM MEMBER WHERE ID = ? AND PASS1 = ?";
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, id);
			pstmt.setString(2, password);
			
			rs = pstmt.executeQuery();
			
			if(rs.next()) {
				result = rs.getInt(1);
			}
			
			conn.close();
		} catch(SQLException e) {
			e.printStackTrace();
		}
		
		return result;
	}
}
```

<로그인 정보 일치>
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/afea2306-9f88-4d54-825d-b2535b7a6eff">
</div>
