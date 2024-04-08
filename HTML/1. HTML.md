-----
### HTML
-----

1. HyperText Markup Language
   - HyperText : 하이퍼링크를 통해 어떤 문서에서 다른 문서로 접근할 수 있는 텍스트
   - Markup : (콘텐츠) 표시
   - Language : 언어

         내용(Content) + 구조(Structrue) 담당 언어
     
2. 웹 브라우저를 통해 표시되는 웹 페이지의 콘텐츠를 정의하기 위해 사용되는 언어

        - 태그 : HTML 코드에 정보(콘텐츠)를 정의하는 형식 (태그 안에 또 다른 태그 삽입 가능)
        - 태그는 <>와 </>를 사용해 콘텐츠의 시작과 끝을 표시
        - 각 태그는 콘텐츠를 감싸며, 태그명은 콘텐츠의 성격과 의미를 나타냄
3. Rendering : HTML 코드가 웹 브라우저를 통해 해석되고 표현되는 과정
4. 확장자 : *.html / *.htm

-----
### 단일 태그
-----
- 시작과 끝을 구분할 필요가 없는 태그
- <태그명 /> 또는 <태그명>

-----
### 속성
-----
- 태그의 부가적인 기능을 정의
- 시작 태그 내부에 주로 정의, 개수에는 특별한 제한이 없음
- <태그명 속성값 = "속성값"> 내용 </태그명> 또는 <태그명 속성값 = "속성값"/>
- 태그명과 속성 정의는 공백으로 구분, 큰 따옴표를 사용

-----
### 주석
-----
- 코드에 대한 메모를 남기기 위한 용도
- 주로 개발자에게 코드를 설명하기 위해 사용되며 브라우저에 미표시
- 사용 : < !-- 주석 처리 -- >
  
        예) <!--Comment-->

-----
### 기본 구조
-----
```html
<!DOCTYPE html> // HTML5는 <!DOCTYPE html>으로 시작해 문서 형식을 HTML5로 지정

<html> // 실질적인 HTML Document 시작(<html> ~ </html>

     <head> // Document Tile, 외부 파일 참조, 메타데이터 설정 등 위치 (단, 브라우저 표시 X)
        <meta charset = "UTF-8">
        <title> 문서의 제목을 쓰는 곳 </title> // 문서의 제목을 나타냄. 콘텐츠는 브라우저 탭에 나타남
     </head>

     <body> // 웹브라우저에 출력되는 모든 요소가 위치
 
     </body>

</html>
```
  - DOCTYPE : 선언된 페이지의 HTML 버전이 무엇인지 웹 브라우저에 알려주는 선언문
  - html : HTML의 루트 요소 정의 (다른 HTML 요소 포함을 위한 컨테이너이며, HTML 문서임을 알려줌)

        - 문서 유형을 지정한 후 실제 문서가 시작되고 끝나는 것을 나타냄
    		- lang 속성 : 문서에서 사용할 언어를 지정
    		- 예) <html lang = "ko">
    
  - head : 해당 문서에 대한 정보인 메타데이터의 집합 정의

        
    		<meta> 태그 : 문자 세트 지정 등 사용 (<meta charset = "UTF-8"> : 문자 인코딩 및 문서 키워드 등에 대한 요약 정보 기입)
        * <title>, <style>, <base>, <link>, <meta>, <script>, <noscript>(<body>요소에도 포함 가능)
  - body : HTML의 모든 콘텐츠를 포함하는 영역을 정의 (텍스트 / 이미지 / 사용자 인터페이스를 나타내는 태그)


-----
### 상대경로와 절대경로
-----
1. 절대 경로 (모든 주소 작성)

        현재 문서 URL : http://172.30.1.33:8081/webPro/cf/LoginForm.jsp 
        이동 문서 URL : http://172.30.1.33:8081/webPro/cf/Map_Login.jsp 

2. 상대 경로

        . : 현재 Directory
        .. : 상위 Directory
         * 현재 문서 URL : http://172.30.1.33:8081/webPro/cf/LoginForm.jsp 
         * 이동 문서 URL : Map_Login.jsp
              A. ./Map_Login.jsp (.은 현재 디렉토리 = 여기서는 cf Directory)
              B. ../cf/Map_Login.jsp (..은 상위 디렉토리 = 여기서는 webPro)
