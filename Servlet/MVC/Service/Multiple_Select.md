-----
### list.jsp 내 다중 선택 값을 POST 하기
-----
```jsp
			<form action="list" method="post">
				<div class="notice margin-top">
					<h3 class="hidden">공지사항 목록</h3>
					<table class="table">
						<thead>
							<tr>
								<th class="w60">번호</th>
								<th class="expand">제목</th>
								<th class="w100">작성자</th>
								<th class="w100">작성일</th>
								<th class="w60">조회수</th>
								<th class="w40">공개</th>
								<th class="w40">삭제</th>
							</tr>
						</thead>
						<tbody>

					<c:forEach var="notice" items="${noticeList}">
					<tr> 
						<td>${notice.id}</td>
						<td class="title indent text-align-left"><a href="/Project/notice/detail.do?id=${notice.id}">${notice.title}<span>[${notice.comment_count}]</span></a></td>
						<td>${notice.writerId}</td>
						<td>
							<fmt:formatDate pattern="yyyy년 MM월 dd일" value="${notice.regdate}"/>	
						</td>
						<td>${notice.hit}</td>
						<td><input type="checkbox" name="open-id" value="${notice.id}"></td>
						<td><input type="checkbox" name="del-id" value="${notice.id}"></td>
					</tr>
					</c:forEach>
						</tbody>
					</table>
				</div>

				<c:set var="page" value="${(empty param.page) ? 1 : param.page}"/>
				<c:set var="startNum" value="${page - (page - 1) % 5}"/>
				<fmt:parseNumber var="result" value="${count/10}" integerOnly="true"/>
				<c:set var="endNum" value="${result + ((count % 10 == 0) ? 0 : 1)}"/>
				
	
				<div class="indexer margin-top align-right">
					<h3 class="hidden">현재 페이지</h3>
					<div><span class="text-orange text-strong">${(empty param.page) ? 1 : param.page}</span> / ${endNum} pages</div>
				</div>

				<div class="text-align-right margin-top">
					<input type="submit" class="btn-text btn-default" name="cmd" value="일괄공개">
					<input type="submit" class="btn-text btn-default" name="cmd" value="일괄삭제">
					<a class="btn-text btn-default" href="reg.jsp">글쓰기</a>				
				</div>
			</form>
```
  - 일괄공개와 일괄삭제에 대해 다중 값을 전달 가능
  - form태그에서 POST 방식으로 전달

-----
### NOTICE 테이블에 공개여부에 대한 PUB 컬럼 추가
-----
1. PUB 컬럼을 통해 해당 글의 공개 / 미공개 여부 확인
  - 공개 : 1
  - 비공개 : 0
   
