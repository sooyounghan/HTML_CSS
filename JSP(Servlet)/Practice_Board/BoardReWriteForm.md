----
### BoardReWrite 구조도
----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ba2f9515-d306-4ffe-b95a-a9c336b3a45a">
</div>

----
### BoardReWrite Form
----
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Board Reply Write Form</title>
	<style>
	
	* {
	    box-sizing:border-box;
	}
	
	h2 {
	    text-align:center;
	    font-size:20px;
	    font-weight:600;
	}
	
	.wrapper {
	    width:100%;
	    display:flex;
	    flex-direction:row;
	    justify-content:center;
	    align-items:center;
	                
	}
	        
	.container {
	    width:600px;
	    display:flex;
	    flex-direction:column;
	    justify-content:center;
	    align-items:center;
	    
	    border:3px solid black;
	}
	
	.form {
	    width:100%;		
	    height:50px;
	    
	    display:flex;
	    flex-direction:row;
	    justify-content:flex-start;
	    align-items:center;
	    
	    border:1px solid black;
	}
	
	.writer_name, .password_name, .email_name, .title_name, .content_name {
	    padding:10px;
	    width:100px;
	    display:flex;
	    flex-direction:row;
	    justify-content:center;
	    align-items:center;
	}
	
	.content_form {
	    height:200px;
	}
	
	.writer, .password, .email, .title, .content {
	    width:100%;
	    text-area:center;
	    
	    display:flex;
	    flex-direction:row;
	    justify-content:center;
	    align-items:center;
	}
	
	input {
	    width:50%;
	    border:none;
	    border-bottom:1px solid black;
	}
	
	textarea {
	    width:75%;
	    height:50%;
	    resize:none;
	    border:1px solid black;
	}
	
	.button_zip {
	    display:flex;
	    flex-direction:row;
	    justify-content:center;
	    align-items:center;
	}
	
	.button {
	    margin:10px;
	    display:inline-block;
	    width:100px;
	    height:30px;
	    border:2px solid black;
	}

	</style>
</head>

<body>
	<%
		// QueryString 정보 
		int board_num = Integer.parseInt(request.getParameter("board_num").trim());
		int ref = Integer.parseInt(request.getParameter("ref").trim());
		int re_step = Integer.parseInt(request.getParameter("re_step").trim());
		int re_level = Integer.parseInt(request.getParameter("re_level").trim());
 	%>
	
    <h2>Reply Write</h2>
	<div class = "wrapper">
       <form action = "BoardReWriteProc.jsp" method = "post">
           <div class = "container">
               <div class = "writer_form form">
                   <div class = "writer_name">Writer</div>
                   <div class = "writer">
                   <input type = "text" name = "writer" required = "required"/>
                   </div>
               </div>
               
               <div class = "password_form form">
                   <div class = "password_name">Password</div>
                   <div class = "password">
                   <input type = "password" name = "content_password" required = "required"/>
                   </div>
               </div>
               
               <div class = "title_form form">
                   <div class = "title_name">Title</div>
                   <div class = "title">
                   <input type = "text" name = "subject" required = "required" value = "[Reply]"/>
                   </div>
               </div>
               
               <div class = "email_form form">
                   <div class = "email_name">Email</div>
                   <div class = "email">
                   <input type = "email" name = "email"/>
                   </div>
               </div>
               
               <div class = "content_form form">
                   <div class = "content_name">Content</div>
                   <div class = "content">
                   <textarea name = "content" rows = "10"></textarea>
                   </div>
               </div>
           </div>
           
           <div class="button_zip">
           	   <input type="hidden" name="<%=ref%>">
           	   <input type="hidden" name="<%=re_step%>">
           	   <input type="hidden" name="<%=re_level%>">
               <input type="submit" class="button" value="Reply Write">
               <input type="reset" class="button" value="Reset"></form>
               <button class="button" onclick="location.href='BoardList.jsp'">Board List</button>
           </div>
       </div>
   </div>
</body>
</html>
```

1. 해당 페이지가 어느 특정 글에 답변 페이지 이므로 title 부분에 [reply] 초기값 입력

2. 답변에 대해서는 ref / re_step / re_level 정보가 중요
   - 어떤 부모 글에 대한 답변인지?
   - 부모 글의 몇 번째 답변인지?
   - 최신순으로 되어있는지?
   - 이러한 정보가 중요하므로 정보가 중요한데, 이를 사용자로부터 입력받지 않고, hidden 속성을 통해 DB가 받을 수 있도록 처리

<div align = "center">
<img  src="https://github.com/sooyounghan/Web/assets/34672301/a0ea4b0e-f3b9-471e-95a4-8a0479be404c">
</div>
