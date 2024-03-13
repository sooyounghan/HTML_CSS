-----
### Animation
-----
1. 여러 이미지를 연결해서 자연스럽게 움직이는 것 처럼 보이게 하는 기법
2. CSS를 이용해서 애니메이션을 만드는 방법
   - transition 속성 활용
   - animation 속성과 keyframe 활용
3. @keyframe으로 애니메이션을 정의하고, 정의한 애니메이션을 불러와서 제어해야함
   - 애니메이션 속성을 이용해 불러온 애니메이션을 제어해야함
   - 최소 keyframe 하나, 애니메이션 속성 하나 필요

-----
### Transition VS Animation
-----
1. Transition
   - 특정 이벤트를 기점으로 작동 (예) hover)
   - 전후 관계가 명백(trigger 존재)해야하며, 이벤트 발생 시점이 명확하게 있어야함
2. Animation
   - 시작하기 위한 이벤트가 필요 없음
   - 시작, 정지, 반복까지 제어 가능
3. traisition으로 제작 가능한 것은 transition으로 해결하되,
   trigger로 해결할 수 없는 부분 (transition으로 제작 불가)은 animation과 keyfrmae을 이용해 제작

-----
### @keyframes
-----
1. CSS 애니메이션의 시작, 중간, 끝 등의 중간 상태를 정의
2. 작성 방법 예시
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/890802ea-0d2d-4d57-b950-44528f834dee">
<img src="https://github.com/sooyounghan/Web/assets/34672301/101d8892-1ee7-4952-9eae-8edae38e7f32">
</div>

  - from, to를 통해 시작 시점 / 종료 시점 CSS 정의 가능
  - 진행도(%)를 이용해 0 / 1~50~99 / 100 %로 시작 / 중간 / 종료 시점의 CSS 정의 가능

-----
### animation 속성
-----
-----
### animation-name
-----
1. 어떠한 keyframes를 요소에 적용할 것인지 지정
2. 예시
```css
animation-name:moveRight;
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9cffa2b7-f84b-4d64-ab37-9a8e26f08f49">
</div>

-----
### animation-duration
-----
1. 애니메이션을 한 번 재생(from ~ to로 재생) 하는데 걸리는 시간 설정
2. 예시
```css
animation-duration:2s;
```

-----
### animation-direction
-----
1. 애니메이션 재생 방향 정의 (정방향[from~to]/역방향[to~from])
2. 예시
```css
animation-direction:alternate;
```

3. 속성
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/63c6d5ff-3e46-4d12-ad30-b6cf5c696f5c">
</div>

  - normal : 정방향으로 지정된 방향(from~to 방향)으로만 계속 Animation
  - alternate : 정방향에서 역방향으로 이동 후, 역방향으로 이동 하는 작업을 반복하는 Animation
  - reverse : 역방향으로 지정된 방향(to~from 방향)으로만 계속 Animation
  - reverse-alternate : 역방향에서 정방향으로 이동 후, 다시 정방향에서 역방향으로 이동하는 작업을 반복하는 Animation

-----
### animation-iteration-count
-----
1. 애니메이션의 재생 횟수를 정의 (animation-direction과 연관)
2. 예시
```css
animation-iteration-count:infinite;
```

3. 기본값은 0 (애니메이션은 1번 재생), 구체적 숫자 가능, infinite는 무한 반복

-----
### animation-timing-function
-----
1. 애니메이션 재생 패턴을 정의
2. transition-timing-function과 유사
3. 예시
```css
animation-timing-fuction:ease-in-out;
```

4. 참조 링크 : https://codepen.io/Joogumi/full/eYMgrKO
   
-----
### animation-delay
-----
1. 애니메이션 시작을 얼마나 지연할지 설정
2. 예시
```css
animation-delay:2s;
```
-----
### animation 단축 속성
-----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e9c821f1-ad17-41d0-a9a0-64303c8f2079">
</div>
