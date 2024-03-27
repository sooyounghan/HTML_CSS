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
		
		Part filePart = request.getPart("file");
		String fileName =filePart.getSubmittedFileName();
		
		InputStream fis = filePart.getInputStream();
		String realPath = request.getServletContext().getRealPath("/upload");
		String filePath = realPath + File.separator + fileName;
		FileOutputStream fos = new FileOutputStream(filePath);
		
		byte[] buff = new byte[1024];
		int size = 0;
		while((size = fis.read(buff)) != -1) {
			fos.write(buff, 0, size);
		}
		
		fos.close();
		fis.close();
		
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

-----
### File Upload Logic 
-----
1. 일반적인 Form Data로 전송되는 데이터는 단순한 문자열
   - application/x-www-form-urlencoded라는 형식으로 전송
   - 예시
```
POST http://localhost:8080/jspServletStudy/login HTTP/1.1
Host: localhost:8080
Content-Length: 24
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like  Gecko) Chrome/75.0.3770.142 Safari/537.36
Accept:  text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
Accept-Encoding: gzip, deflate, br
 
id=dololak&password=1234
출처: https://dololak.tistory.com/726 [코끼리를 냉장고에 넣는 방법:티스토리]
```

3. 첨부파일은 단순한 문자열이 아닌 0과 1로 이루어진 Binary Data이므로 전송시에 'multipart/form-data'형식으로 전송
   - 따라서, 이를 받을 수 있는 InputStream이 필요한데, request에는 이를 지원 : InputStream request.getInputStream()
   - 이 스트림을 얻어서, 데이터를 가공해 추출하는 작업 필요
```
POST http://localhost:8080/jspServletStudy/fileUpload HTTP/1.1
Host: localhost:8080
Connection: keep-alive
Content-Length: 2049708
Upgrade-Insecure-Requests: 1
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryg3IbmadDo87Bmh2R
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like  Gecko) Chrome/75.0.3770.142 Safari/537.36
 
------WebKitFormBoundaryg3IbmadDo87Bmh2R
Content-Disposition: form-data; name="file1"; filename="메이븐.pptx"
Content-Type: application/vnd.openxmlformats-officedocument.presentationml.presentation
 
ppt 파일에 대한바이너리 데이터...
출처: https://dololak.tistory.com/726 [코끼리를 냉장고에 넣는 방법:티스토리]
```

-----
### Part API 
-----
1. 쉽게 생각하면, miltipart/form-data POST 요청으로 수신받은 from 아이템이나 하나의 Part를 의미
2. HttpServletRequest에서 Part를 받아오는 메서드 (import javax.servlet.http.Part)
   - Part request.getPart(String filName) : 웹 서버로 전송되어진 fileName에 대해 Part 자료형으로 받음 (즉, Binary Content를 얻어옴)
   - Collection< Part > request.getParts(String fileName) : Part형을 담은 Colleciton으로 반환

3. 주요 메서드
  - String getName(): Part의 이름을 반환
  - String getContentType(): 업로드된 파일의 콘텐츠 유형을 반환
  - long getSize(): 업로드된 파일의 크기를 반환
  - void write(String fileName): 업로드된 파일을 지정된 파일로 저장
  - InputStream getInputStream(): 업로드된 파일의 내용을 읽기 위한 InputStream을 반환
  - String getSubmittedFileName(): 클라이언트가 업로드한 파일의 이름을 반환
  - void delete(): 업로드된 파일을 삭제
  - String getHeader(String name): 특정 HTTP 헤더의 값을 반환
    
```java
Part filePart = request.getPart("file");
String fileName = filePart.getSubmittedFileName();

InputStream fis = filePart.getInputStream();
String realPath = request.getServletContext().getRealPath("/upload");
String filePath = realPath + File.separator + fileName;
FileOutputStream fos = new FileOutputStream(filePath);

byte[] buff = new byte[1024];
int size = 0;
while((size = fis.read(buff)) != -1) {
	fos.write(buff, 0, size);
}

fos.close();
fis.close();
```
1. ServletContext request.getServletContext() : 현재 웹 서버 루트 기준으로 상대 경로 반환
2. String ServletContext.getRealPath(String path) : path에 대한 웹 서버 루트 기준 주소에 대해 절대 경로 반환 
3. File.separator : 현재 운영체제 대한 파일경로 구분자
