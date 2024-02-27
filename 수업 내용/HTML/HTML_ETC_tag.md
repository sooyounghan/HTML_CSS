-----
### table
-----    
```html
<table>
  <tr>
    <th></th>
    <td></td>
    <td></td>
  </tr>

  <tr>
    <td></td>
    <td></td>  
  </tr>
</table>
```

1. table 태그를 이용해 표 전체 윤곽을 잡은 후 행(row)을 먼저 만들고 행마다 몇 개의 셀(cell)을 들어갈지 결정
     - table 태그로 표 자리를 먼저 설정
     - tr 태그로 행 제작
     - td 태그로 행마다 열을 제작
     - 각 셀에 들어갈 내용은 td 태그 사이에 설정

2. th 태그 : 표에 제목 셀 만들기
   - th 태그도 td 태그와 마찬가지로 셀을 만드는 태그로 해당 셀에 들어가는 내용을 셀의 중앙에 배치하고 굵게 표시

3. 표는 테두리 없이 표시됨

4. colspan(가로) / rowspan(세로)
   - < th >나 < td > 태그에서 이루어짐
   - 몇 개의 셀을 가로로 합칠지 정함
  ```html
<table>
  <tr>
    <th></th>
    <td colspan = "합칠 셀의 개수"></td>
    <td></td>
  </tr>

  <tr>
    <td></td>
    <td rowspan = "합칠 셀의 개수"></td>  
  </tr>
</table>
```

5. caption, figcaption 태그
   - 표에 제목을 붙일 때 사용
   - caption 태그 : table 태그 바로 밑에 사용, 표의 위쪽 중앙에 표시되며 제목을 여러 줄 표시 또는 텍스트 꾸미기 가능
```html
<table>
  <caption>
    <strong>제목</strong>
    <p>내용</p>
  </caption>
  <tr>
    <th></th>
    <td colspan = "합칠 셀의 개수"></td>
    <td></td>
  </tr>

  <tr>
    <td></td>
    <td rowspan = "합칠 셀의 개수"></td>  
  </tr>
</table>
```
   - figcaption 태그 : figure 태그를 감싼 후 figcaption 태그를 이용해 제목이나 설명 글을 입력 (중앙에 정렬되지 않음)

           + table 태그보다 앞에 사용하면 표 위에 제목 표시
           + /table 태그 다음에 추가하면 표 아래 제목 표시
```html
<figure>
<figcaption>
  <p> 제목 </p>
</figcaption>
<table>
  <caption>
    <strong>제목</strong>
    <p>내용</p>
  </caption>
  <tr>
    <th></th>
    <td colspan = "합칠 셀의 개수"></td>
    <td></td>
  </tr>

  <tr>
    <td></td>
    <td rowspan = "합칠 셀의 개수"></td>  
  </tr>
</table>
<figcaption>
  <p> 제목 </p>
</figcaption>
</figure>
```

  - aria-describedby 속성 : 표에 대한 설명 제공
```html
<p id = "summary">요약</p>
<table aria-describedby = "summary">
  <caption>
    <strong>제목</strong>
    <p>내용</p>
  </caption>
  <tr>
    <th></th>
    <td colspan = "합칠 셀의 개수"></td>
    <td></td>
  </tr>

  <tr>
    <td></td>
    <td rowspan = "합칠 셀의 개수"></td>  
  </tr>
</table>
```

-----
### 표 구조 정의 태그
-----    

-----
### 이미지 맵 설정 태그
-----    
