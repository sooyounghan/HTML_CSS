-----
### JDBC (Java DataBase Connectivity)
-----
1. Java / JSP 프로그램 내 데이터베이스와 관련된 작업을 처리할 수 있도록 도와주는 자바 표준 인터페이스
2. RDBMS에 접근해, SQL문을 실행하기 위한 자바 API 또는 라이브러리
3. JDBC API를 이용해 DBMS 종류에 상관없이 데이터베이스 작업 처리 가능

-----
### JDBC (Java DataBase Connectivity)의 구조
-----
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/e7bed988-355e-4d5c-8bc6-b85792b767a4">
</div>

1. 데이터베이스 종류에 상관 없이 JDBC API를 이용해 데이터베이스에 접근
2. 각 DBMS는 자신에게 알맞은 JDBC 드라이버 제공

-----
### JDBC를 통한 JSP와 데이터베이스 연동
-----
1. java.sql.* 패키지를 import
2. JDBC 드라이버 로딩
3. 데이터베이스 접속을 위한 Connection 객체 생성
4. Query 실행을 위한 Statement / PreparedStatement / CallableStatment 객체 생성
5. 쿼리 실행
6. 쿼리 실행의 결과 값(int, ResultSet) 사용
7. 사용된 ResultSet / Statement / PreparedStatement / CallableStatment 객체 종료
8. Connection 객체 종료

-----
### JDBC Driver Loading
-----
1. 드라이브 인터페이스를 구현하는 작업
2. Class.forName(String ClassName)을 이용해 JDBC 드라이버 로딩
```jsp
<%
try {
  Class.forName("com.mysql.jdbc.Driver"); // 지정한 클래스 정보를 담고 있는 Class Instance를 구해주는 기능
 } catch(SQLException ex) {
  // 예외 발생 처리
}
%>
```

3. JDBC 드라이버가 로딩되면 자동으로 Connection 객체를 생성
     - JDBC 드라이버에서 데이터베이스와 연결된 Connection을 가져오기 위해 DriverManager 클래스의 getConnection() 이용
     - DriverManager 클래스로 Connection 객체를 생성할 때, 드라이버를 검색
     - 검색한 드라이버를 이용해 Connection 객체를 생성 후 반환

           static Connection getConnection(String url)
           static Connection getConnection(String url, String user, String password)
           static Connection getConnection(String url, Properties prop)

           MySQL : com.mysql.jdbc.Driver
           Oracle : oracle.jdbc.driver.OracleDriver
           MSSQL 서버 : com.microsoft.sqlserver.jdbc.SQLServerDriver
           jdbc:[DBMS]:[데이터베이스 식별자] = jdbc:[DBMS]://HOST[:PORT]/DBNAME[?param=value&param1=value2&...]
       
< 매개변수 url : 데이터베이스 경로 >
 - URL 표현방식 : jdbc.dbms이름:주소::포트번호[데이터베이스 식별자]

```jsp
<%
Connection conn = null;

try {
  Class.forName("com.mysql.jdbc.Driver");
  conn = DriverManager.getConntion("jdbc.mysql://localhost:3306/chap14?" + "user=jspeaxm&password=jsppw");
 } catch(SQLException ex) {
  // 예외 발생 처리
}
%>
```

< 매개변수 url, user, password : 데이터베이스 경로, 데이터베이스 사용자 이름, 비밀번호>

```jsp
<%
Connection conn = null;

try {
  Class.forName("com.mysql.jdbc.Driver");
  conn = DriverManager.getConntion("jdbc.mysql://localhost:3306/chap14","jspeaxm","jsppw") ;
 } catch(SQLException ex) {
  // 예외 발생 처리
}
%>
```

<매개변수 prop : 사용자 및 비밀번호 등 추가정보를 포함한 Properties 객체 사용>
```jsp
<%
Connection conn = null;

try {
  Class.forName("com.mysql.jdbc.Driver");
  Propertires prop = new Properties();
  prop.put("user", "jspexam");
  prop.put("password", "jsppw");

  conn = DriverManager.getConntion("jdbc.mysql://localhost:3306/chap14", prop) ;
 } catch(SQLException ex) {
  // 예외 발생 처리
}
%>
```

5. Connection 객체를 DriverManager 클래스에 등록
   * JDBC 드라이버 로딩은 프로그램 수행 시 한 번만 필요
  
-----
### DataBase Connection
-----
1. JDBC를 이용해서 데이터베이스를 사용하려면 데이터베이스와 연결된 Connection을 구해야함
2. java.sql.Connection 타입이 데이터베이스 커넥션을 의미
3. java.sql.DriverManager 클래스가 제공하는 getConnection()을 사용해 Connection 객체 생성
  - 객체를 생성하지 못하면 SQLException 발생하므로 try ~ catch 블록을 사용해 예외 처리 필요
    
        DriverManager.getConnection(String jdbcURL)
        DriverManager.getConnection(String jdbcURL, String user, String password)

4. DataBase 연결(Connection) 닫기
   - 데이터베이스의 연결이 더 이상 필요하지 않으면 close() 메서드로 실행한 Connection 객체를 해제
   - 데이터베이스 리소스를 사용하지 않기 위해 사용을 끝내마자 리소스 해제

         void close() throws SQLException
```jsp
<%
Connection conn = null;

try {
  Class.forName("com.mysql.jdbc.Driver");
  conn = DriverManager.getConntion("jdbc.mysql://localhost:3306/chap14","jspeaxm","jsppw") ;
 } catch(SQLException ex) {
  // 예외 발생 처리
} finally {
  if(conn != null) try { conn.close(); } catch(SQLException ex) { }
}
%>
```
  - DriverManager.getConnection() 메서드가 예외를 발생시킬 경우 conn은 Connection 객체가 생성되지 않음
  - 유효성 검사 필요 (null 여부 확인) 후, close() 메서드 호출

-----
### Statement 객체
-----
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
