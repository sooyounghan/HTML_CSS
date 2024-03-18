-----
### 예약 관련 TABLE
-----
1. CarReserve Class에 대한 CAR_RESERVE TABLE 생성
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/3869ef5a-cd7b-41ab-9610-dc1a4af7e733">
</div>

```sql
CREATE TABLE CAR_RESERVE (
RESERVE_NO NUMBER CONSTRAINT CAR_RESERVE_RESERVE_NO_PK PRIMARY KEY,
NO NUMBER CONSTRAINT CAR_RESERVE_NO_NN NOT NULL,
ID VARCHAR2(10) CONSTRAINT CAR_RESERVE_ID_NN NOT NULL,
DURATION_DAY NUMBER CONSTRAINT CAR_RESERVE_DURATION_DAY_NN NOT NULL,
RESERVE_DAY NUMBER CONSTRAINT CAR_RESERVE_RESERVE_DAY_NN NOT NULL,
USE_INSURANCE NUMBER CONSTRAINT CAR_RESERVE_USE_INSURANCE_NN NOT NULL,
USE_WIFI NUMBER CONSTRAINT CAR_RESERVE_USE_WIFI_NN NOT NULL,
USE_NAVIGATION NUMBER CONSTRAINT CAR_RESERVE_USE_NAVGATION_NN NOT NULL,
USE_BABY_SHEET NUMBER CONSTRAINT CAR_RESERVE_USE_BABY_SHEET_NN NOT NULL,

CONSTRAINT CAR_RESERVE_NO_FK FOREIGN KEY(NO) REFERENCES RENTCAR(NO),
CONSTRAINT CAR_RESERVE_FK_FK FOREIGN KEY(ID) REFERENCES MEMBER(ID)
);
```
- RESERVE_NO는 PK
- NO, ID는 FK로서 각각 RENTCAR의 PK, ID는 MEMBER의 PK를 참조
- 모든 COLUMN에 대해서 NOT NULL

- 테이블 구조 및 제약조건
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/ba827e12-3b99-456e-b42d-6139e021b00e">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/a9a4cce4-9b7c-496e-9ce2-5822e8653855">
</div>


- 총 3개의 테이블의 ERD
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/2d8fd3f6-1bac-47fa-9a5a-de07aac2db77">
</div>


2. 기존 CarReserve Class

```java
package RentCar;


/*
 * 차량에 대한 예약 정보 클래스
 */
public class CarReserve {
	private int reserve_no; // 예약번호
	private String id; // 예약 회원 ID
	private int no; // 차 식별자
	private int car_num; // 차 수량
	private int duration_day; // 대여 기간
	private String reserve_day; // 대여일
	private int insurance; // 보험료
	private int use_wifi; // Wi-fi 이용
	private int navigation; // Navigation 이용
	private int baby_sheet; // BabySheet 이용
	
	public int getReserve_no() {
		return reserve_no;
	}

	public void setReserve_no(int reserve_no) {
		this.reserve_no = reserve_no;
	}

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public int getNo() {
		return no;
	}
	
	public void setNo(int no) {
		this.no = no;
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

3. 
