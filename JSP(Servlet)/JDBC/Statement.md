-----
### Statement 객체
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/72e792a5-3032-4724-b064-c711a4c491b0">
</div>
1. 정적 쿼리에 사용 : Connection 객체를 생성한 후에는 Connection 객체로부터 Statment를 생성하고 쿼리를 실행
  
       Statment createStatement() throws SQLException
       Statment stmt = conn.createStatement();

       ResultSet executeQuery(String query) : SELECT 쿼리 실행
       int executeUpdate(String query) : UPDATE, INSERT, DELETE 쿼리 실행

2. 하나의 쿼리를 사용하고나면, 더 이상 사용 불가
   
3. 하나의 쿼리를 끝내고 나면, close()를 사용해 객체를 즉시 해제


-----
### executeQuery()
-----
: 데이터를 조회하는 메서드

       ResultSet executeQuery(String sql) throws SQLException

< 사용 예 >
```jsp
<%
String memberID = request.getParameter("memeberID");
String name = request.getParameter("name");

Class.forName("com.mysql.jdbc.Driver");

Connection conn = null;
Statment stmt = null;

try {
  String jdbcDriver = "jdbc.mysql://localhost:3306/chap14?" + "useUnicode=true&characterEncoding=UTF8";
  String dbUser = "jspexam";
  String dbPass = "jsppw";

  String sql = "SELECT * FROM Member WHERE id = '1'";

  conn = DriverManager.getConnection(jdbcDriver, dbUser, dpPass);
  stmt = conn.createStatement();
  ResultSet rs = stmt.executeQuery(sql);
} catch (SQLException ex) {
} finally {
  if(stmt != null) try { stmt.close(); } catch(SQLException ex) { }
  if(conn != null) try { conn.close(); } catch(SQLException ex) { }
}
%>
```

-----
### executeUpdate()
-----
- 데이터를 삽입, 삭제, 수정하는 메서드

      int executeUpdate(String sql) throws SQLException
    
< 사용 예 >
```jsp
<%
int updateCount = 0;
String memberID = request.getParameter("memeberID");
String name = request.getParameter("name");

Class.forName("com.mysql.jdbc.Driver");

Connection conn = null;
Statment stmt = null;

try {
  String jdbcDriver = "jdbc.mysql://localhost:3306/chap14?" + "useUnicode=true&characterEncoding=UTF8";
  String dbUser = "jspexam";
  String dbPass = "jsppw";

  String sql = "UPDATE MEMBER set NAME = " + name + " " + "WHERE MEMBERID = " + memberID + "";

  conn = DriverManager.getConnection(jdbcDriver, dbUser, dpPass);
  stmt = conn.createStatement();
  updateCount = stmt.executeUpdate(sql);
} catch (SQLException ex) {
} finally {
  if(stmt != null) try { stmt.close(); } catch(SQLException ex) { }
  if(conn != null) try { conn.close(); } catch(SQLException ex) { }
}
%>
```

- 변경된 레코드의 개수를 Return
- 지정한 아이디가 존재하지 않으면 0을 리턴 = 즉, 레코드의 개수를 사용해 지정한 아이디가 존재하는지 여부 판단
