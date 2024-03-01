-----
### 태그의 구분
-----
1. 블록 레벨 요소 : 자기가 속한 영역의 너비가 모두 차지하여 블록 형성
2. 인라인 요소 : 자기에게 필요한 만큼의 공간만 차지

-----
### 블록 레벨 요소
-----

-----
### 문단(Paragraph) 태그 (p)
-----
1. p 태그 : 문단 요소를 나타내는 태그
2. 하나의 p 태그는 하나의 문단을 표현
3. 문단과 문단 사이에는 공백 존재
   
```html
<!DOCTYPE html>

	<html>
		<body>
			<p> 문단 태그 </p>
			<!-- <p>~</p> 후 자동 개행 -->
			<p> 문단과 문단 사이에는 공백 </p>
		</body>
	</html>
```

-----
### 제목(Headline) 태그 (h)
-----
1. 제목을 나타내는 태그
2. h1 ~ h6까지의 태그 존재 (h1이 가장 중요한 제목 의미)
   
```html
<!DOCTYPE HTML>

<html>

  <body>

    <h1> Heading 1 </h1>
    <h2> Heading 2 </h2>
    <h3> Heading 3 </h3> 
    <h4> Heading 4 </h4>
    <h5> Heading 5 </h5>
    <h6> Heading 6 </h6>

</body>

</html>
```

-----
### 수평선 태그 (hr)
----
1. 수평줄을 표시하는 태그 (단일 태그)
2. 주제 변경 또는 내용 구분을 위해 주로 사용
   
```html
<!DOCTYPE html>
	<html>	
		<body>        
		<p> Paragraph 1 </p>
        
		<hr/>
                
		<p> Paragraph 2</p>
		</body>
</html>
```

-----
### HTML 텍스트의 특징
-----
1. 일반적인 'Enter'는 줄바꿈이지만, HTML에서는 이를 무시
2. 스페이스를 통한 공백도 한 번씩만 저장

<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/75935ac9-a913-423e-995f-501f8b83d87a">
</div>

-----
### 줄바꿈 태그 : br
-----
1. 강제 개행(link break)로, 단일 태그
2. 공백을 두 번 이상 표현하고자 할 때는 &nbsp(;) 사용

```html
<!DOCTYPE html>
<html>
  <body>
     <p>개행<br/>공백 &nbsp;&nbsp; 두 칸 표현</p>
   </body>
</html>
```

-----
### 형식화 태그 : pre
-----
  - 형식화(Preformatted)된 텍스트를 출력
  - pre 태그 내 content는 작성된 그대로 브라우저에 표시

```html
<!DOCTYPE html>
	<html>
	<body>
		<pre>
		var myArray = [];
		console.log(myArray.length); // 0

		myArray[1000] = true; // [ , , ... , , true ]
		console.log(myArray.length); // 1001
		console.log(myArray[0]); // undefined
		</pre>
	</body>
	</html>
```
-----
### 인라인 요소
-----
-----
### 굵게 표시하는 태그 : b와 strong
-----
: 감싸고 있는 콘텐츠를 굵게 표시하고 싶을 때 사용하는 태그

```html
<!DOCTYPE html>
	<html>
	<body>
		<b>강조1</b>
    <strong>강조2</strong>
	</body>
	</html>
```

-----
### 기울임 표시 태그 : em, i
-----
: 감싸고 있는 콘텐츠를 기울여 이탤릭체로 표시하고 싶을 때 사용하는 태그

```html
<!DOCTYPE html>
	<html>
	<body>
		<em>이탤릭체 표기1</em>
    <i>이탤릭체 표기2</i>
	</body>
	</html>
```
-----
### 강조 태그 : mark
-----
: 감싸고 있는 콘텐츠에 형광펜으로 그어 놓은 듯한 효과를 주는 태그

```html
<!DOCTYPE html>
	<html>
	<body>
		<mark>이 부분</mark>이 중요합니다.
	</body>
	</html>
```

-----
### 블록 레벨 요소와 인라인 요소
-----
-----
### 인용 태그 : blockquote, q
-----
1. blockquote : 한 문단이나 내용 전체가 인용문일 때 사용
2. q :  문장 내 들어가는 인용문에 대해 사용 (속성 : cite = "주소")


```html
<!DOCTYPE html>
	<html>
	<body>
		<blockquote>이 곳은 인용하는 태그를 사용하는 곳입니다.</blockquote>
    나는 <q cite = "www.naver.com">이 부분</q>을 인용합니다.
	</body>
	</html>
```

-----
### 영역을 묶는 태그 : span (+ div)
-----
: 단순 텍스트나 텍스트에 관련된 마크업 등 구문 콘텐츠 스타일이나 속성의 범위를 적용하기 위해 감싸주는 태그

   		div 태그 : 레이아웃을 만들거나 콘텐츠를 나누는(Division) 컨테이너로 사용
     
```html
<!DOCTYPE html>
	<html>
	<body>
		<span style = "color:blue;">이 부분</span>은 파란색으로 표시합니다.
	</body>
	</html>
```

