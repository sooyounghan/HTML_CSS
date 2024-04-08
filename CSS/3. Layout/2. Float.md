-----
### Float
-----
1. Float : '띄우다'
   - 요소가 Normal Flow로부터 벗어나서 특정 Container의 좌/우측을 감싸는 형태가 되도록 강제배치 하는 속성
   
          Normal Flow : 기본적인 요소의 흐름

2. float : none (기본값)
<div align = "cetner">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/2d02736a-6103-47b7-b79b-433f061aef07">
</div>

3. float : left
   - 두 개의 Block Level 요소를 왼쪽으로 강제 배치 시키는 요소
<div align = "cetner">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/8dbebda9-a8c6-40b9-bd03-87b724a3ffdd">
</div>

3. flaot : right
   - 두 개의 Block Level 요소를 오른쪽으로 강제 배치 시키는 요소
<div align = "cetner">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/a22d0ee9-be2a-4090-a886-fcd0c44df9ff">
</div>

-----
### Clear
-----
1. float가 적용된 요소 혹은 float가 적용된 요소에게 영향을 받고 있는 요소에게 추가로 줄 수 있는 속성
2. float의 영향력을 clear가 적용된 요소에 한해 그 영향력을 해제한다고 보면 됨
3. clear : none (기본값)
   - float : left가 적용된 왼쪽 div
   - float : right가 적용된 오른쪽 div
   - 이 둘에 영향을 받는 p 태그 (clear 속성에 영향을 받을 태그)
<div align = "cetner">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/96080612-f030-49cd-af2b-964e167116ce">
</div>

4. clear : right
   - clear의 값은 float와 관계를 받음
   - 따라서, float : right의 값은 clear : right가 적용된 요소와 관련
<div align = "cetner">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/c335211d-cbe2-461b-b43f-a507933bfe0f">
</div>

   - 현재 파란 박스에 float : right가 적용되어 있으므로, 이 요소에 영향을 받는 p 태그가 파란 박스 아래 쪽으로 적용

5. clear : left
   - float : left의 값은 clear : left가 적용된 요소와 관련
<div align = "cetner">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/9b5e6e79-21ef-4bb2-af96-fb9460e14b02">
</div>

  - 현재 빨간 박스에 float : left가 적용되어 있으므로, 이 요소에 영향을 받는 p 태그가 빨간 박스 아래 쪽으로 적용

6. claar : both (주로 사용)
   - float : left, float : right의 모두 영향력을 받는 요소의 영향력 모두 해제 가능


-----
### 예제
-----
1. float : right 적용
```html
<!DOCTYPE html>
<html lang="kr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02-01-float</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="float-box">
        안녕!<br>
        박스1 입니다.
    </div>    
    <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris risus sapien, facilisis vitae feugiat ut, semper at ligula. Vivamus cursus lectus tincidunt tellus tincidunt pharetra. Donec pharetra dictum malesuada. Fusce non sapien egestas, maximus urna vel, pulvinar magna. Aenean ut dapibus lacus, in blandit ligula. Vestibulum sit amet efficitur tortor. Phasellus id viverra felis. Mauris magna est, luctus sit amet neque et, sagittis ultrices elit. Morbi odio eros, finibus non justo eget, sollicitudin dapibus ante. Nunc maximus eu nunc et finibus. Vivamus viverra feugiat pretium. Sed at tempus enim, et dignissim ante. Mauris vel nisi leo. Nullam vel nibh suscipit, lobortis ex eu, mollis nunc. Fusce in eros blandit, vehicula libero et, euismod enim.
    </p>
</body>
</html>
```

2. clear : right 적용
```css
.float-box {
    width:200px;
    height:200px;
    background-color:blue;
    color:#ffffff;
    padding:30px;
    box-sizing:border-box;
    float:right;
}

p {
    font-size:20px;
    clear:right;
}
```

3. 결과 : float : right 영향을 받는 p가 clear : right로 인해 다음과 같아짐
<div align = "cetner">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/f0453058-6a4b-448e-9ddf-ce9d32623d4b">
</div>

-----
### clearfix
-----
1. float : left, float : right 속성의 박스 2개 존재
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02-02-clear</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="box1 box">
        첫 번째 박스입니다.<br>
        float:left가 적용되어 있음.
    </div>
    <div class="box2 box">
        두 번째 박스입니다.<br>
        float:right가 적용되어 있음.
    </div>
    <div class="clearfix"></div>
    <div class="box3">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris risus sapien, facilisis vitae feugiat ut, semper at ligula. Vivamus cursus lectus tincidunt tellus tincidunt pharetra. Donec pharetra dictum malesuada. Fusce non sapien egestas, maximus urna vel, pulvinar magna. Aenean ut dapibus lacus, in blandit ligula. Vestibulum sit amet efficitur tortor. Phasellus id viverra felis. Mauris magna est, luctus sit amet neque et, sagittis ultrices elit. Morbi odio eros, finibus non justo eget, sollicitudin dapibus ante. Nunc maximus eu nunc et finibus. Vivamus viverra feugiat pretium. Sed at tempus enim, et dignissim ante. Mauris vel nisi leo. Nullam vel nibh suscipit, lobortis ex eu, mollis nunc. Fusce in eros blandit, vehicula libero et, euismod enim.
    </div>  
</body>
</html>
```
  - 중복 클래스 생성 방법

        <div class = "box1 box">
        <div class = "box2 box">
        - 위 두 div는 box라는 공통 클래스를 또 하나 가짐

2. box3 속성에 clear:both를 적용하면 결과적으로 영향을 받지 않음
   - 하지만, float와 연결된 모든 요소에 clear:both를 적용하는것은 힘듬
   - 따라서, 빈 div에 clearfix라는 클래스 생성
```css
.box {
    width:300px;
    box-sizing:border-box;
    padding:20px;
}

.box1 {
    height:400px;
    background-color:red;
    float:left;
}

.box2 {
    height:200px;
    background-color:blue;
    float:right;
}

.clearfix {
    clear:both;
}
```
  - clearset의 설정 때문에 float가 적용된 요소를 clear 시킬 수 있음
  - 따라서, float 요소 속성에 대해 영향을 받는 요소에 대해 clearfix 속성이라는 빈 div를 먼저 생성
  - clearset 클래스로 설정해 항상 영향을 받지 않도록 설정 가능

<div align = "center">
<img src = "https://github.com/sooyounghan/DataBase/assets/34672301/cb526eff-2986-48dc-a922-4988a17c6308">
</div>
