-----
### BoardUpdateController : Update 버튼을 누를 때 처리할 Controller
-----
```java
package Controller;

import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import Model.Board;
import Model.BoardDAO;

/*
 * 게시물 수정 페이지 이동 처리 Servlet
 */
@WebServlet("/BoardUpdateController.do")
public class BoardUpdateController extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doService(request, response);
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doService(request, response);
	}

	protected void doService(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		int board_num = Integer.parseInt(request.getParameter("board_num"));
		
		BoardDAO boardDAO = new BoardDAO();
		Board board = boardDAO.getOneUpdateBoard(board_num);
		request.setAttribute("board", board);
		
		RequestDispatcher rd = request.getRequestDispatcher("BoardUpdateForm.jsp");
		rd.forward(request, response);
	}
}
```

-----
### BoardUpdate Form View Page
-----
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Board Update Form</title>
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
		
		.writer_form {
		    display:flex;
		    justify-content:space-between;
		    align-content:center;
		}
		
		.writer_name, .reg_date_name {
		    padding:10px;
		    width:100px;
		    text-align:center;
		}
		
		.writer_content, .reg_date_content {
		    padding:10px;
		    text-align:center;
		    width:calc(100% - 350px);
		}
		
		.password_name, .email_name, .title_name, .content_name {
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
		
		.password, .email, .title, .content {
		    width:100%;
		    text-align:center;
		    
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
		
		.update, .button {
		    margin:10px;
		    display:inline-block;
		    width:100px;
		    height:30px;
		    border:2px solid black;
		}
		</style>
</head>

<body>
	<c:set var="board" value="${board}"/>
	<h2>${board.subject}</h2>
	
	<form action="BoardUpdateFormProcController.do" method="post">
	<div class = "wrapper">
        <div class = "container">
            <div class = "writer_form form">
                <div class = "writer_name">Writer</div>
                <div class = "writer_content">${board.writer}</div>
                <div class = "reg_date_name">작성일</div>
                <div class = "reg_date_content">${board.reg_date}</div>
            </div>
                       
            <div class = "title_form form">
                <div class = "title_name">Title</div>
                <div class = "title">
                	<input type = "text" name = "subject" value="${board.subject}" required = "required"/>
                </div>
            </div>
            
            <div class = "password_form form">
                <div class = "password_name">PassWord</div>
                <div class = "password">
                	<input type = "password" name = "content_password" required = "required"/>
                </div>
            </div>
            
            <div class = "content_form form">
                <div class = "content_name">Content</div>
                <div class = "content">
               	 	<textarea name = "content" rows = "10">${board.content}</textarea>
                </div>
            </div>
        
	       <div class="button_zip">
	       	   <input type="hidden" name="board_num" value="${board.board_num}">
	       	   <input type="hidden" name="pwd" value="${board.content_password}">	       	   
	           <input type="submit" class="update" value="Update">
	           <button class="button" onclick="location.href='BoardListController.do'">BoardList</button>
	       </div>
        </div>
     </div>
	</form>
</body>
</html>
```

-----
### BoardUpdateFormProcController
-----
```java
package Controller;

import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import Model.BoardDAO;

/*
 * 게시물 수정 처리 Servlet
 */
@WebServlet("/BoardUpdateFormProcController.do")
public class BoardUpdateFormProcController extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doService(request, response);
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doService(request, response);
	}

	protected void doService(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		BoardDAO boardDAO = new BoardDAO();
				
		String content_password = request.getParameter("content_password");
		String password = request.getParameter("pwd");
	
		int board_num = Integer.parseInt(request.getParameter("board_num"));
		String subject = request.getParameter("subject");
		String content = request.getParameter("content");
		
		if(password.equals(content_password)) {
			boardDAO.updateBoard(board_num, subject, content);
			
			
			RequestDispatcher rd = request.getRequestDispatcher("BoardListController.do");
			rd.forward(request, response);
			
		} else {
			
			RequestDispatcher rd = request.getRequestDispatcher("BoardListController.do");
			rd.forward(request, response);
		}
	}
}
```
