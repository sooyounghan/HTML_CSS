-----
### 차량 예약
-----
1. 상위 최신 상품 3개를 인위적으로 화면에 출력할 예정
2. 차량 종류에 대한 선택(소형, 중형, 대형)하여 검색하게 되면, 해당 차량에 대해서만 출력
   - RentCar의 Category에 설정한 부분에 맞게 출력 설정  
3. 전체 검색을 하게 되면, 전체 차량에 대한 정보 출력

-----
### Top 부분 예약하기 부분 링크 변경
-----
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
...

    <header class="top">
        <div class="top_logo_user">
            <div class="top_logo"><img src = "./img/logo.png"></div>
            <div class="top_user"><p><%=id%>님 어서오세요!</p></div>
        </div>
        <div class="top_menu">
            <div class="menu1 menu"><a href = "CarReserveMain.jsp">Reservation</a></div>
...

        </div>
    </header>
</body>

</html>
```
