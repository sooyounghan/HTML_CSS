-----
### meta 
-----
1. HTML 문서에 대한 메타데이터 정의

         메타데이터란 데이터에 대한 데이터, 즉 '정보'

2. 항상 head 태그 안에 들어감
3. 일반적으로 charset, 페이지 설명, 키워드, 문서의 작성자 및 뷰포트 설정을 지정
4. 웹페이지에 대한 정보를 제공하므로, 검색 최적화 및 검색 결과 반영 가능

-----
### meta 태그의 유형 및 속성
-----
1. charset : 문자 세트
2. http-equiv : 콘텐츠 속성 정보에 대한 http Header
3. name : 문서 정보
4. content : 메타데이터 내용

-----
### charset
-----
1. 문자 인코딩에 대한 요약 정보 기입 속성

       - 문자 인코딩이란 한글을 표시하기 위해 문자 세트를 지정하는 작업
       - 한글과 영어 모두 사용을 위해 UTF-8

2. 인코딩을 명확히 하지 않으면, 웹브라우저 설정 상황에 따라 자동으로 인코딩 추정해서 처리 (문자가 깨질 가능성 존재)
   
```html
<head>
<meta charset = "UTF-8">
</head>
```

-----
### http-equiv
-----
: 콘텐츠 속성의 정보 / 값에 대한 HTTP 헤더를 제공

       HTTP : 인터넷에서 데이터를 주고 받을 수 있는 프로토콜

```html
<head>
<!-- IE 브라우저의 최신 버전의 엔진을 사용하라는 뜻 -->
<meta http-equiv = "x-ua-compatible" content = "IE=edge">
<!-- 10초마다 페이지 새로고침 하라는 뜻 -->
<meta http-equiv = "refresh" content = "10">
</head>
```

-----
### name, content
-----
: name 속성을 이름으로, content 속성을 값으로 문서 정보를 이름 + 값 쌍의 형태로 제공해 사용 가능

```html
<head>
<!-- 문서 제작자-->
<meta name = "author" content = "김터넷"
<!-- 페이지에 대한 요약, 브라우저 즐겨찾기 페이지의 기본 설명 값 -->
<meta name = "description" content = "요약">
<!-- 페이지의 콘텐츠와 관련된, 쉼표로 구분한 키워드 목록 -->
<meta name = "keywords" content = "강아지, 고양이, 반려동물, 등등">
</head>
```
