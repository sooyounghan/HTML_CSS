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


