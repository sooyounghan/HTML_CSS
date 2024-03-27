-----
### 파일 업로드를 위한 Servlet 설정
-----
1. web.xml에 설정 예시
```jsp
<multipart-config>
  <location>/tmp</location>
  <max-file-size>20848820</max-file-size>
  <max-request-size>418018841</max-request-size>
  <file-size-threshold>1048576</file-size-threshold>
</multipart-config>
```

2. annotation으로 설정 예시
```java
@MultipartConfing(
  location="/tmp",
  fileSizeThreshold=1024*1024,
  maxFileSize=1024*1024*5,
  maxRequestSize=1024*1024*5*5)
```

3. location : 절대경로로 지정
   - 절대경로는 서비스를 실행하는 리눅스/윈도우즈에 차이가 있으므로, 차라리 설정을 안하고 자바에 지정된 임시 디렉토리 사용

4. fileSizeThreshold : 전송한 크기보다 큰 파일이 들어오면 location 위치에 저장
5. maxFileSize : 한 파일의 최대 크기 지정
6. maxRequestSize : 한 번에 전체 받을 수 있는 최대 크기 (한 파일이 아닌 한 번에 전체임을 주의)
   
-----
### 파일 업로드
-----
1. form 태그 내 enctype 속성 추가 : multipart/form-data
```jsp
<form action="/Project/admin/board/notice/reg" method="post" enctype="multipart/form-data">
    <div class="margin-top first">
        <h3 class="hidden">공지사항 입력</h3>
        <table class="table">
            <tbody>
                <tr>
                    <th>제목</th>
                    <td class="text-align-left text-indent text-strong text-orange" colspan="3">
                        <input type="text" name="title" />
                    </td>
                </tr>
                <tr>
                    <th>첨부파일</th>
                    <td colspan="3" class="text-align-left text-indent"><input type="file"
                            name="file" /> </td>
                </tr>
                <tr class="content">
                    <td colspan="4"><textarea class="content" name="content"></textarea></td>
                </tr>
                <tr>
                    <td colspan="4" class="text-align-right"><input class="vertical-align" type="checkbox" id="open" name="open" value="true"><label for="open" class="margin-left">바로공개</label> </td>
                </tr>
            </tbody>
        </table>
    </div>
    <div class="margin-top text-align-center">
        <input class="btn-text btn-default" type="submit" value="등록" />
        <a class="btn-text btn-cancel" href="/Project/admin/board/notice/list">취소</a>
    </div>
</form>
```

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/bc96b729-a536-4736-b0e6-ec66d021f91b">
</div>

2. RegController
```java
package com.newlecture.web.controller.admin.notice;

import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.MultipartConfig;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import com.newlectrue.web.service.NoticeService;
import com.newlecture.web.entity.Notice;

@MultipartConfig(
	  fileSizeThreshold=1024*1024,
	  maxFileSize=1024*1024*5,
	  maxRequestSize=1024*1024*5*5
)

@WebServlet("/admin/board/notice/reg")
public class RegController extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		RequestDispatcher rd = request.getRequestDispatcher("/WEB-INF/view/admin/board/notice/reg.jsp");
		rd.forward(request, response);
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		String title = request.getParameter("title");
		String content = request.getParameter("content");
		String isOpen = request.getParameter("open");
		
		boolean pub = false;
		if(isOpen != null) pub = true; 
		
		Notice notice = new Notice();
		notice.setTitle(title);
		notice.setContent(content);
		notice.setPub(pub);
		notice.setWriterId("newlec");

		NoticeService service = new NoticeService();
		service.insertNotice(notice);
		
		response.sendRedirect("list");
	}
}
```
