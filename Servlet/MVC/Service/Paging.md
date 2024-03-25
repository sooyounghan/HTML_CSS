-----
### 기본 Paging
-----
```jsp
	<c:set var="page" value="${(param.page == null) ? 1 : param.page}"/>
	<c:set var="startNum" value="${page - (page - 1) % 5}"/>
	<c:set var="endNum" value="${23}"/>

	<div>		
		<c:if test="${startNum - 1 > 1}">
			<a href="?page=${startNum - 1}&field=&query=" class="btn btn-next">이전</a>
		</c:if>
		<c:if test="${startNum - 1 <= 1}">
			<span class="btn btn-prev" onclick="alert('이전 페이지가 없습니다.');">이전</span>
		</c:if>
	</div>
	<ul class="-list- center">
		<c:forEach var="i" begin="0" end="4">
		<li><a class="-text- orange bold" href="?page=${startNum + i}&field=&query=" >${startNum + i}</a></li>
		</c:forEach>		
	</ul>
	<div>
		<c:if test="${startNum + 5 < endNum}">
			<a href="?page=${startNum + 5}&field=&query=" class="btn btn-next">다음</a>
		</c:if>
		<c:if test="${startNum + 5 >= endNum}">
			<span class="btn btn-next" onclick="alert('다음 페이지가 없습니다.');">다음</span>
		</c:if>
	</div>
```
