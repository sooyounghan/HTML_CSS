-----
### JSP-DB 연동 Pattern
-----
1. Data에 대해 JSP 내에서 DB 연동
2. JSP로 Data를 입력 받아 DAO(Data Access Object)를 이용해 DB 연동
3. Connection Pool 개념을 적용하여 DB와 연동

-----
### 순서
-----
1. 회원가입 JSP 페이지 생성
2. 회원가입 관련 DB TABLE 생성
3. 처리해주는 DAO 클래스 생성 - DB와 연동 후 저장
4. response.sendRedirect()를 통한 회원 전체 보기 구성
5. 회원 수정 및 삭제

-----
### Pattern 1 : JSP 내에서 DB 연동
-----
    * DB TABLE 구성 : 아이디(id) / 비밀번호 (pwd) [비밀번호 확인(repwd)은 중복되므로 제외] / 이메일(email) / 전화번호(tel) / 관심분야 (hobby) / 직업 (job) / 연령(age) / 하고싶은 말 (info)
    * 여기서 관심 분야 (hobby)는 다중 선택이 가능하므로, 해당 값을 배열로 받을 것

1. MemberJoin.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title> Member Join</title>
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
		<h2>회원 가입</h2>
		<form action="MemberJoinProc.jsp" method = "post">
			<table border="1">
				<tr height="50">
					<td width="150" align="center">아이디 </td>
					<td width="350" align="center">
						<input type="text" name="id" size="40" placeholder="id를 넣으세요">						
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">패스워드</td>
					<td width="350" align="center">
						<input type="password" name="pass1" size="40"
						placeholder="비밀번호는 숫자와 영어만 넣어주세요">						
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">패스워드 확인</td>
					<td width="350" align="center">
						<input type="password" name="pass2" size="40"
						placeholder="비밀번호는 숫자와 영어만 넣어주세요">						
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">이메일</td>
					<td width="350" align="center">
						<input type="email" name="email" size="40">						
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">전화 번호 </td>
					<td width="350" align="center">
						<input type="tel" name="tel" size="40">				
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">당신의 관심 분야</td>
					<td width="350" align="center">
						<input type="checkbox" name="hobby" value="캠핑">캠핑&nbsp;
						<input type="checkbox" name="hobby" value="등산">등산&nbsp;
						<input type="checkbox" name="hobby" value="독서">독서&nbsp;
						<input type="checkbox" name="hobby" value="음악">음악&nbsp;				
					</td>
				</tr>
				
			   <tr height="50">
					<td width="150" align="center">당신의 직업은</td>
					<td width="350" align="center">
						<select name="job">
						<option value="교사">교사</option>
						<option value="의사">의사</option>
						<option value="변호사">변호사</option>
						<option value="기술사">기술사</option>
						</select>				
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">당신의 연령은</td>
					<td width="350" align="center">
						<input type="radio" name="age" value="10">10대&nbsp;
						<input type="radio" name="age" value="20">20대&nbsp;
						<input type="radio" name="age" value="30">30대&nbsp;
						<input type="radio" name="age" value="40">40대&nbsp;			
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">하고 싶은말</td>
					<td width="350" align="center">
							<textarea rows="5" cols="40" name="info"></textarea>	
					</td>
				</tr>
					
				<tr height="50">
					<td width="150" colspan="2">
						<input type="submit" value="회원 가입">	
						<input type="reset" value="취소">			
					</td>
				</tr>	
			</table>
		</form>	
</body>
</html>
```

2. MemberBean Class 생성
```java
package Model;

public class MemberBean {
	private String id;
	private String pass1;
	private String repwd;
	private String email;
	private String tel;
	private String hobby;
	private String job;
	private String age;
	private String info;
	
	public String getId() {
		return id;
	}
	public void setId(String id) {
		this.id = id;
	}
	
	public String getPass1() {
		return pwd;
	}
	
	public void setPass1(String pass1) {
		this.pwd = pwd;
	}
	
	public String getRepwd() {
		return repwd;
	}
	
	public void setRepwd(String repwd) {
		this.repwd = repwd;
	}
	
	public String getEmail() {
		return email;
	}
	
	public void setEmail(String email) {
		this.email = email;
	}
	
	public String getTel() {
		return tel;
	}
	
	public void setTel(String tel) {
		this.tel = tel;
	}
	
	public String getHobby() {
		return hobby;
	}
	
	public void setHobby(String hobby) {
		this.hobby = hobby;
	}
	
	public String getJob() {
		return job;
	}
	
	public void setJob(String job) {
		this.job = job;
	}
	
	public String getAge() {
		return age;
	}
	
	public void setAge(String age) {
		this.age = age;
	}
	
	public String getInfo() {
		return info;
	}
	
	public void setInfo(String info) {
		this.info = info;
	}
}
```

3. MemberJoin 관련 Table 생성
```sql
CREATE TABLE MEMBER (
ID VARCHAR2(10) CONSTARINT MEMBER_ID_PK PRIMARY KEY(ID),
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

   
