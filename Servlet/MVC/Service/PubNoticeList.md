-----
### 1단계 : 관리자 공지사항에서 일괄 공지 등록 확인을 위한 설정
-----
```jsp
  <c:forEach var="notice" items="${noticeList}">
  <tr> 
    <td>${notice.id}</td>
    <td class="title indent text-align-left"><a href="/Project/admin/board/notice/detail?id=${notice.id}">${notice.title}<span>[${notice.comment_count}]</span></a></td>
    <td>${notice.writerId}</td>
    <td>
      <fmt:formatDate pattern="yyyy년 MM월 dd일" value="${notice.regdate}"/>	
    </td>
    <td>${notice.hit}</td>
    
    <c:set var="open" value=""/>
    <c:if test = "${notice.pub}">
      <c:set var="open" value="checked"/>
    </c:if>
    <td><input type="checkbox" name="open-id" value="${notice.id}" ${open}></td>
    <td><input type="checkbox" name="del-id" value="${notice.id}"></td>
    
  </tr>
  </c:forEach>
```
: < c:if >문을 통해 pub의 값이 ture(1)이면 등록된 공지임을 확인

-----
### 2단계 : 관리자 공지와 유저의 공지를 구분하기 위한 service Class 및 DAO 함수 구현
-----
1. Service Class
```java
public class NoticeService {
	NoticeDAO noticeDAO = new NoticeDAO();

...

	public List<NoticeView> pubNoticeAllList(String field, String query, int page) {
		return noticeDAO.getPubNoticeList(field, query, page);
	}
}
```

2. NoticeDAO에서 getPubNoticeList 구현
```java
	public List<NoticeView> getPubNoticeList(String field, String query, int page) {
		List<NoticeView> noticeList = new ArrayList<NoticeView>();
		
		try {
			getConnection();
			
			String sql = "SELECT B.* FROM (SELECT A.*, ROWNUM NUM FROM (SELECT * FROM NOTICE_VIEW WHERE " + field + " LIKE ? ORDER BY REGDATE DESC) A) B WHERE PUB = 1";

			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, "%"+query+"%");
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				NoticeView notice = new NoticeView();
				
				notice.setId(rs.getInt(1));
				notice.setTitle(rs.getString(2));
				notice.setWriterId(rs.getString(3));
				notice.setRegdate(rs.getDate(4));
				notice.setHit(rs.getInt(5));
				notice.setFiles(rs.getString(6));
				notice.setPub(rs.getBoolean(7));
				noticeList.add(notice);
			}
			conn.close();
  		} catch(SQLException se) {
			se.printStackTrace();
		}
		
		return noticeList;
	}
```

3. 이에 따른 Controller 변경 (유저의 ListController)
```java
package com.newlecture.web.notice;

import java.io.IOException;
import java.util.List;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import com.newlectrue.web.service.NoticeService;
import com.newlecture.web.entity.NoticeView;

@WebServlet("/notice/list.do")
public class ListController extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		service(request, response);

	}
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		service(request, response);
	}

	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		NoticeService service = new NoticeService();

		// list.do?field=title(or writerId)&query=검색어
		String page_ = request.getParameter("page");
		String field = request.getParameter("field");
		String query = request.getParameter("query");
		int page = 1;
		
		if(page_ == null || page_.equals("")) {
			page = 1;
		} else {
			page = Integer.parseInt(page_);
		}
		
		if(field == null || field.equals("")) {
			field = "title";
		}

		if(query == null || query.equals("")) {
			query = "";
		}
		
		List<NoticeView> noticeList = service.pubNoticeAllList(field, query, page);
		int count = service.getNoticeCount(field, query);
		request.setAttribute("noticeList", noticeList);
		request.setAttribute("count", count);
		RequestDispatcher rd = request.getRequestDispatcher("/WEB-INF/view/notice/list.jsp");
		rd.forward(request, response);
	}
}
```

-----
### 3단계 : 해당 조건에 따라 공지사항(pub = 1)이 등록된 경우만 유저에게 출력
-----
