-----
### Flex
-----
1. CSS 레이아웃 배치에 중점을 두고 고안
2. 기존의 Float 방식보다 훨씬 수월하고 간단하게 레이아웃을 잡을 수 있음

----
### Flex 적용
-----
1. 요소의 속성을 flex로 변경 (display : 요소의 기본 속성 값을 변경할 때 사용)
```css

display:flex
```

2. flex-container : display:flex를 적용시킨 요소 (부모 요소)
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/01383c00-2a33-46e0-8449-9ce040e883de">
</div>

3. flex-item : flex-container의 자식 요소

----
### flex-direction
-----
1. flex 정렬의 기준
2. flex-direction : row(기본값) | column (행 | 열)
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/68ddd08f-6d38-49f5-a1ec-72f73bf573d1">
</div>

<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/951a48c1-2950-430c-bb58-88943a7a96e6">
</div>

      flex-direction : row-reverse | column-reverse
      - row와 동일하지만, item의 순서을 역으로 배치
      - column와 동일하지만, item의 순서를 역으로 배치
      
3. flex 방식의 중심축 : 요소가 flex가 되면 중심축이 형성되며, flex-container를 가로지르는 축으로, 정렬의 기준이 됨
<div align = "center">
<img width="1000" alt="dd726086-f1bf-45a5-85fd-39d1f9c86422" src="https://github.com/sooyounghan/Web/assets/34672301/fd0a3453-4744-4da3-b013-0ce8a9bf0896">
</div>

----
### flex-justify
-----
1. 중심축 방향 정렬 결정
  - flex-direction : row이면, 중심축이 가로이므로 가로 방향에 대한 정렬
  - flex-direction : column이면, 중심축이 세로이면 세로 방향에 대한 정렬

2. justify-content : flex-start (기본값)
  - container의 시작점을 기준으로, item이 정렬
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/8b0dad68-74d0-43ec-ae8d-a3d4856b4a20">
</div>   

3. justify-content : flex-end
  - container의 끝 부분을 기준으로, item이 정렬
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/c0c5f56f-31c1-4636-a62b-a693d11f82c2">
</div>   

4. justify-content : center
   - 중앙 정렬, 해당 중심축을 기준으로 container의 가운데 지점, 즉 center지점을 기준으로 정렬
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/4fff3aca-4a03-449a-a0ec-8ddd04e63910">
</div>   

5. justify-content : space-between
   - container 안의 item들이 균일한 여백을 두고 배치
   - 처음과 마지막 item은 start-line과 end-line에는 여백이 미존재
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/f35cbc4e-fc55-4bcd-a1eb-6945ab4e9d07">
</div>   

6. justify-content : space-around
   - 처음과 마지막 item에도 균일한 좌우 여백이 존재 (양 끝과 각 요소 사이 여백이 다름, 일반적으로 2배 차이)
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/cbab5428-dbca-4503-be14-8fa718c337b5">
</div>   

7. justify-content : space-evenly
   - space-around와 유사하나, space-around와 여백 차이 존재 
   - 모든 여백이 균일하게 정렬되어 있음
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/71cbf776-7ba7-45be-bf9c-3b2223c78378">
</div>   

----
### align-items
-----
1. 중심축 반대 방향 정렬
2. align-items : stretch (기본값)
   - item의 세로 길이를 늘려서, container의 세로 영역을 늘림
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/2bddf527-26a8-4231-902d-f48cfe2fead6">
</div>  

3. align-items : flex-start
   - container의 시작 지점을 기준으로 정렬
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/8d71c499-c75b-488c-bab3-56a350fa0aeb">
</div>

4. align-items : flex-end
   - container의 끝 지점을 기준으로 정렬
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/ac1d30c2-3c46-4704-bb09-5adcbed030a8">
</div>

5. align-items : center
   - container의 중심축의 반대 방향의 중앙 지점을 기준으로 정렬
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/ba199b0d-9ec1-4345-9c31-d7d4d44acf8f">
</div>

6. align-items은 flex-item이 한 줄 일때 우선 적용되며, 두 줄 이상일 때는 align-content라는 다른 속성을 써야함
7. flex-direction이 바뀌면, 중심축의 방향도 바뀌므로, justify-content와 align-items의 정렬 방향도 함께 바뀜
<div align = "center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/8298b51d-9787-47c0-bfac-be7842a5e4e8">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/4b1a467d-a6c1-4455-b7e5-d9118d07f0e0">
</div>

      추가적으로, flex-direction:row-reverse | column-reverse의 경우라면,
      - flex-start, flex-end의 방향이 변경될 수 있음

