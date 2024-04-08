-----
### Position
-----
1. HTML 요소가 배치되는 방식을 결정하는 속성
2. 속성값
   - static (기본값)
   - relative
   - absolute
   - fixed
   - sticky

-----
### Top / Left / Right / Bottom
-----
: 해당 방향 기준으로 요소의 좌표값을 변경

-----
### position:static(기본값)
-----
1. 요소를 문서상 원래 있어야 하는 위치에 배치 (즉, 위치 조정이 불가)
2. top/right/bottom/left 적용 불가
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cb46dd4e-6adb-4365-b273-16792c9a4fd5">
</div>

-----
### position:relative
-----
1. 원래 있던 자리를 기준으로 요소의 위치를 조정 가능
2. top/right/bottom/left 적용 가능
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a3386bdf-4783-4fd2-b8f7-fa0867487504">
</div>

-----
### position:absolute
-----
1. 절대 좌표(부모 요소 중 relative가 적용된 요소를 기준으로 삼음)를 기준으로 요소의 위치를 조정 가능
2. top/right/bottom/left 적용 가능
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6cb9eae0-8499-42cc-a133-8acbd9ad5e8b">
</div>

3. relative가 적용된 부모 요소가 없다면, HTML의 body 전체를 절대 좌표로 삼음

-----
### 예제
-----
1. 부모 요소 중에 relative가 없는 경우
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>06-03-absolute</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        여기는 Container입니다.

        <div class="wrapper">
            여기는 Container 안 입니다.

            <div class="item">
                여기는 Container 가장 안 쪽의 item 박스입니다.
            </div>
        </div>
    </div>
</body>
</html>
```
```css
* {
    box-sizing:border-box;
}

.container {
    border:3px solid red;
    padding:10px;
}

.wrapper {
    border:3px solid blue;
    padding:10px;
}

.item {
    background-color:orange;
    width:200px;
    height:100px;
    position:absolute;
    top:0;
    left:0;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b6a05f16-ad03-471a-b9a3-4696e41c17d4">
</div>

  - 현재 부모 요소 중 relative를 가진 부모 요소가 없으므로 HTML BODY를 절대 좌표로 지정

2. 부모 요소 중 container에 relative를 부여한 경우
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>06-03-absolute</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        여기는 Container입니다.

        <div class="wrapper">
            여기는 Container 안 입니다.

            <div class="item">
                여기는 Container 가장 안 쪽의 item 박스입니다.
            </div>
        </div>
    </div>
</body>
</html>
```
```css
* {
    box-sizing:border-box;
}

.container {
    border:3px solid red;
    padding:10px;
    position:relative;
}

.wrapper {
    border:3px solid blue;
    padding:10px;
}

.item {
    background-color:orange;
    width:200px;
    height:100px;
    position:absolute;
    top:0;
    left:0;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2d426e7f-24be-4607-ba0c-fa1a24f29587">
</div>

  - 현재 부모 요소 중 relative를 가진 부모 요소인 container를 기준으로 절대 좌표로 지정

3. 부모 요소 중 container와 wrapper에 relative를 부여한 경우
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>06-03-absolute</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        여기는 Container입니다.

        <div class="wrapper">
            여기는 Container 안 입니다.

            <div class="item">
                여기는 Container 가장 안 쪽의 item 박스입니다.
            </div>
        </div>
    </div>
</body>
</html>
```
```css
* {
    box-sizing:border-box;
}

.container {
    border:3px solid red;
    padding:10px;
    position:relative;
}

.wrapper {
    border:3px solid blue;
    padding:10px;
    position:relative;
}

.item {
    background-color:orange;
    width:200px;
    height:100px;
    position:absolute;
    top:0;
    left:0;
}
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/93866d38-ceb3-4498-ab04-43c98a5c815b">
</div>

  - 현재 부모 요소 중 relative를 가진 부모 요소 중 가장 가까운 부모 요소인 wrapper를 기준으로 절대 좌표로 지정

-----
### position:fixed
-----
1. Scroll과 무관하게 ViewPort를 기준으로 요소의 위치 설정
2. 기준 : viewport
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a64bfd45-0303-41f7-be3d-285b11d70665">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1c0052ff-fa93-4f5b-9691-4bfcdabd7be0">
</div>

3. Scorll과 무관하게 그 위치에 지속적으로 유지됨을 보임

-----
### position:sticky
-----
1. 요소의 원래 위치에 있다가 스크롤이 내려가면 지정한 좌표에 고정
2. 기준 : 부모 요소의 좌표
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1a0ab8d5-b444-408c-80b3-9fce78b43091">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e1b2c1d2-4f89-4c27-ab19-ae526518c138">
</div>

3. 최초에는 static과 동일, Scroll이 내려가면 원하는 위치에 지정

-----
### z-index
-----
1. 여러개의 요소가 겹쳐져 있을 때, 무엇이 앞으로 나올지 결정하는 속성
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/87584c24-712e-4f03-97b0-fa42e72d6178">
</div>

2. 3차원 공간 시, z축이 존재하는데, z-index란 z축의 방향에서 몇 번째에 위치할 것인지 결정
3. z-index:auto (기본값)
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7dd469dc-af91-49cd-95e3-bfdcf2a407b9">
</div>

4. z-index의 수가 커질수록, 가장 앞으로 나오도록 설정 가능
5. position이 static이면, z-index는 미적용

-----
### 예제
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>06-04-z-index</title>
    <link rel="stylesheet" href="./index.css">
</head>

<body>
    <div class="container">
        <div class="item item1">
            z-index : 4
        </div>
        <div class="item item2">
            z-index : 2
        </div>
        <div class="item item3">
            z-index : 1
        </div>
        <div class="item item4">
            z-index : auto
        </div>
    </div>
</body>
</html>
```

```css
* {
    box-sizing:border-box;
}

.container {
    width:100%;
    height:400px;
    border:2px solid blue;
    padding:30px;
}

.item {
    width:160px;
    height:140px;
    border:2px solid black;
    background-color:#dddddd;
}

.item1 {
    position:relative;
    z-index:4;
}

.item2 {
    position:absolute;
    top:70px;
    left:70px;
    z-index:2;
}

.item3 {
    position:absolute;
    top:100px;
    left:100px;
    z-index:1;
}

.item4 {
    position:absolute;
    top:130px;
    left:130px;
}
```

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/168ebf06-d57e-4cc8-aeeb-585ad9bbb1ec">
</div>
