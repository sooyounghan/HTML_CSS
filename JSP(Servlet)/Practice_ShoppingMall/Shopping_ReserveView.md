-----
### CarReserveView JSP Page
-----
1. 예약에 대한 정보를 확인하는 페이지
2. 오늘 날자 이후에 대한 예약에 대해서 확인
3. 웹 페이지에 로그인된 유저에 대해서 예약 내역을 확인
4. Top.jsp에서 Reserve Check 메뉴 변경
```jsp
        <div class="top_menu">
            <div class="menu1 menu"><a href = "RentCarMain.jsp?center=CarReserveMain.jsp">Reservation</a></div>
            <div class="menu2 menu"><a href = "RentCarMain.jsp?center=CarReserveView.jsp">Reserved Check</a></div>
            <div class="menu3 menu"><a href = "#">Board</a></div>
            <div class="menu4 menu"><a href = "#">Event</a></div>
            <div class="menu5 menu"><a href = "#">Q&A</a></div>
        </div>
```

5. 보여줄 항목
   - 예약 차량의 이미지
   - 예약 차량의 이름
   - 예약 차량의 대여 가격
   - 예약 차량 수량
   - 예약 차량의 대여 기간
   - 예약 차량의 대여 일자
   - 예약 차량의 보험료 유무
   - 예약 차량의 Wi-fi 이용 유무
   - 예약 차량의 Navigation 이용 유무
   - 예약 차량의 BabySheet 유무
  
-----
### Car(Reserve)View Class
-----
1. 보여줄 항목에 대해 새로운 Bean Class 생성
```java
package RentCar;

/*
 * 차량 예약에 대한 정보를 담을 Class
 */
public class CarView {
	private String name; // 차 이름
	private int price; // 대여 가격
	private String img; // 차 이미지
	private int car_num; // 차 수량
	private int duration_day; // 대여기간
	private String reserve_day; // 대여일
	private int insurance; // 보험료
	private int use_wifi; // Wi-fi 이용
	private int navigation; // Navigation 이용
	private int baby_sheet; // BabySheet 이용
	
	public String getName() {
		return name;
	}
	
	public void setName(String name) {
		this.name = name;
	}
	
	public int getPrice() {
		return price;
	}
	
	public void setPrice(int price) {
		this.price = price;
	}
	
	public String getImg() {
		return img;
	}
	
	public void setImg(String img) {
		this.img = img;
	}
	
	public int getCar_num() {
		return car_num;
	}
	
	public void setCar_num(int car_num) {
		this.car_num = car_num;
	}
	
	public int getDuration_day() {
		return duration_day;
	}
	
	public void setDuration_day(int duration_day) {
		this.duration_day = duration_day;
	}
	
	public String getReserve_day() {
		return reserve_day;
	}
	
	public void setReserve_day(String reserve_day) {
		this.reserve_day = reserve_day;
	}
	
	public int getInsurance() {
		return insurance;
	}
	
	public void setInsurance(int insurance) {
		this.insurance = insurance;
	}
	
	public int getUse_wifi() {
		return use_wifi;
	}
	
	public void setUse_wifi(int use_wifi) {
		this.use_wifi = use_wifi;
	}
	
	public int getNavigation() {
		return navigation;
	}
	
	public void setNavigation(int navigation) {
		this.navigation = navigation;
	}
	
	public int getBaby_sheet() {
		return baby_sheet;
	}
	
	public void setBaby_sheet(int baby_sheet) {
		this.baby_sheet = baby_sheet;
	}
}
```
2. 이 정보를 얻기 위한 JOIN 방법
```sql
SELECT *
FROM RENTCAR R INNER JOIN CAR_RESERVE C ON (R.NO = C.NO)
WHERE C.ID = ?  AND SYSDATE < TO_DATE(C.RESERVE_DAY, 'YYYY-MM-DD');
```

