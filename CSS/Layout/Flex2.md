-----
### flex-wrap
-----
1. wrap : 줄바꿈과 개행과 관련
2. flex-item이 여러개 일 떄, item들의 줄바꿈을 허용할 것인지, 말 것인지를 결정
 
3. flex-wrap : nowrap(기본값)
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/dcf43fb1-c990-46a0-9f05-6af46744bd72">
</div>

  - flex-items의 가로 사이즈가 커져도, 무조건 한 줄에 들어가도록 강제성을 부여
  - flex-items들의 찌그러짐이 발생

4. flex-wrap : wrap
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/746e347c-1d49-4512-8333-122ec0925c9c">
</div>

  - flex-items가 가로 사이즈의 이상으로 커지면, 자연스럽게 다음줄로 넘어감
  - 규격이 강제로 변경되지 않고, 자연스럽게 넘어감

-----
### align-content
-----
1. align-items는 flex-item이 한 줄 일때 우선 적용
2. flex-item이 두 줄 이상이면 align-content라는 다른 속성을 써야함
3. 즉, 여러 줄이 된 flex-item의 중심 반대 축 정렬을 어떻게 할 것인지 결정

4. align-content : stretch (기본값)
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9ca52d46-61f7-4011-ac18-3cff0514df81">
</div>

  - item의 실제 규격과 상관 없이, 길이가 늘어나 꽉 채우게 됨

5. align-content : flex-start
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cda9ce2d-f1e6-4dee-b14d-61cf344f78f7">
</div>

  - Container의 Start-Line을 기준으로 정렬

6. align-content : flex-end
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/39915ec2-6eed-4aee-9a06-2d3668987f86">
</div>

  - Container의 End-Line을 기준으로 정렬

7. align-content : center
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2fc72490-dd31-4593-ac22-5e3ad96dc353">
</div>

  - Container의 중심 Line을 기준으로 정렬

8. align-content : space-between
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2ec4aa9b-e357-40e7-9c2c-4a756049022a">
</div>

  - Container의 축을 따라 균일하게 배치
  - 첫 item과 마지막 item은 여백이 없음

9. align-content : space-around
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0d21b1fc-84ee-4a88-990d-8d72abad63e4">
</div>

  - Container의 축을 따라 균일하게 배치
  - 양 끝의 여백도 존재하나, 양 끝의 여백과 item 사이의 여백의 차이가 존재

10. align-content: space-evenly
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2bb16d6d-33f4-4cc6-8ca2-730a41bc8d73">
</div>

  - Container의 축을 따라 균일하게 배치
  - 모든 여백을 균일하게 적용

-----
### flex-flow
-----
1. flex-direction과 flex-wrap을 합쳐놓은 단축 속성

       단축 속성 : 유사한 성질을 가진 여러 공통 속성을 한 번에 입력할 수 있도록 묶은 것
           예) border:1px solid red;

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/fe8a6f9c-e8ea-4875-9856-e0d8125ec4e4">
</div>

2. 순서 주의 : flex-diection flex-wrap

-----
### flex-item 속성
-----
1. flex-order : item의 순서를 지정 (HTML에 작성한 요소의 순서를 무시하고, 원하는 순서대로 배치 가능)
2. flex-basis : item의 기본 사이즈를 지정
3. flex-shrink : 설정된 숫자값에 따라 flex-container 요소 내부에서 flex-item요소의 크기가 축소
4. flex-grow : flex-container 요소 내부에서 flex-item 요소가 할당 가능한 공간의 정도를 선언
5. 그 외 여러가지 존재

-----
### MDN : CSS 속성 참조
-----
