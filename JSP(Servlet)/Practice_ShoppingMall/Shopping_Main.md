-----
### Top 부분 구현
-----
```jsp 
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
	<meta charset="UTF-8">
	<title>RentCar Main Top</title>
	<style>
	
	* {
	    box-sizing:border-box;
	    margin:0;
	    padding:0;
	}
	
	header {
	    height:170px;
	
	    display:flex;
	    flex-direction:column;
	    justify-content:flex-start;
	    align-items:space-around;
	}
	
	.top_logo_user {
	    height:50%;
	    display:flex;
	    flex-direction:row;
	    justify-content:space-between;
	    align-items:center;
	}
	
	.top_logo {
	    width:20%;
	    height:100%;
	    position:relative;
	}
	
	.top_user  {
		padding:20px;
	    width:30%;
	    text-align:right;
	}
	
	.top_menu {
	    padding:10px;
	    height:40%;
	    
	    display:flex;
	    flex-direction:row;
	    justify-content:space-between;
	    align-items:center;
	}
	
	.menu1, .menu2, .menu3, .menu4, .menu5 {
	    width:calc(20% - 15px);
	    height:100%;
	
	    display:flex;
	    flex-direction:row;
	    justify-content:center;
	    align-items:center;
	}
	
	.menu a {
	    display:inline-block;
	    font-size:15px;
	    font-weight:600;
	    text-decoration:none;
	    color:black;
	}
	
	.top_logo img {
		position:absolute;
		over-fit:cover;
	}
	</style>
</head>

<body>
    <header class="top">
        <div class="top_logo_user">
            <div class="top_logo"><img src = "./img/logo.png"></div>
            <div class="top_user"><p>님 어서오세요!</p></div>
        </div>
        <div class="top_menu">
            <div class="menu1 menu"><a href = "#">Reservation</a></div>
            <div class="menu2 menu"><a href = "#">Reserved Check</a></div>
            <div class="menu3 menu"><a href = "#">Board</a></div>
            <div class="menu4 menu"><a href = "#">Event</a></div>
            <div class="menu5 menu"><a href = "#">Q&A</a></div>
        </div>
    </header>
</body>

</html>
```
<div align="center">
<img width="952" alt="20240317_200526" src="https://github.com/sooyounghan/Web/assets/34672301/1672f6e0-5013-4e75-b357-70a930c0e9ec">
</div>

-----
### Bottom 부분 구현
-----
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
	
	<style>
	* {
	    box-sizing:border-box;
	    padding:0;
	    margin:0;
	}
	
	footer {
	    height:100px;
	    display:flex;
	    flex-wrap:wrap;
	    justify-content:center;
	    align-items:center;
	}
	
	.description p {
	    font-size:14px;
	    font-weight:600;
	    font-style: italic;
	}
	
	hr {
	    width:100%;
	}

	</style>
</head>

<body>
    <footer>
        <hr>
        <div class="description">
            <p>RentCar에 오신걸 환영합니다!</p>
        </div>
    </footer>
</body>
</html>
```
<div align="center">
<img width="943" alt="20240317_200535" src="https://github.com/sooyounghan/Web/assets/34672301/d730e558-9671-4137-a5c7-0450342d9d32">
</div>
