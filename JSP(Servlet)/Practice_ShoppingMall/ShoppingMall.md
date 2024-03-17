-----
### 요구사항 정의
-----
1. 개인 렌터카 예약 서비스 Shopping Mall
2. 구성 : Top (Logo, Menu, 회원정보) / Center (Top의 메뉴를 선택하면 변경) / Bottom
3. Top의 주요 기능 구현 예정 부분 : 예약 / 예약 확인 / [이벤트 / 고객 센터]
  
4. 주요 기능 (예약하기)
   - 렌터카 카테고리 구성 : 카테고리에 따라 전체 또는 일부 리스트 선택 가능 
   - 특정 렌터카를 선택하면, 예약할 수 있는 기능
   - 수량이 부족하면, 예약이 힘든 메세지 까지 출력
   - 결제 시스템 전까지 구현 예정
     
5. 예약 확인 : 본인의 아이디와 비밀번호를 입력하면 예약 정보 확인을 제공하는 서비스

6. DB TABLE 구성
   - 렌터카 사이트에 등록된 자동차에 대한 정보를 담을 TABLE
   - 주문 유저 TABLE
   - 예약 확인 TABLE
  
-----
### DBCP 연동
-----
1. RentCar Project 생성 후, DBCP 연동

  - WAS의 Server.xml 설정 변경 (Pool에 Connection 객체 준비)
```jsp
      <Context docBase="RentCar" path="/RentCar" reloadable="true" source="org.eclipse.jst.jee.server:RentCar">
      	<Resource auth="Container" driverClassName="oracle.jdbc.driver.OracleDriver" loginTimeout="10" maxWaits="5000" name="jdbc/pool" password="1234" type="javax.sql.DataSource" url="jdbc:oracle:thin:@localhost:1521:xe" username="dbPractice"/>
      </Context>
```

2. RentCarDAO 생성 (DBCP 연동)
```java
package RentCar;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

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
}
```
