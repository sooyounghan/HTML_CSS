-----
### grid VS flex
-----
1. flex : 1차원적 구조 (row 혹은 column 방향 중 하나를 택해야 함)
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9e56a839-c5d9-4bb1-9f96-b8943769d6c9">
</div>

  - 다음과 같은 Layout이 구성되어 있다면, 두 개의 flex로 구성
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/babc39ac-e5cd-44b4-beb3-9bd5ae95f872">
</div>

  - flex는 row 혹은 column 방향으로만 하나를 선택해서 구성할 수 있으므로 2개의 레이아웃으로 구성

2. grid : 2차원적 구조 (즉, row와 column 레이아웃을 동시에 설정 가능)
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/87b7c5f2-33c7-4e38-8685-5c10ed6b1dc7">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0941e9db-890e-420d-ab14-7ea036e6cc8c">
</div>

  - 다음과 같은 Layout이 구성되어 있다면, 한 개의 grid로도 구성
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8e19d230-d5cb-441f-85a6-ebbbd42a4051">
</div>

-----
### grid 속성
-----
-----
### display:grid
-----
1. 요소의 속성을 grid로 변경
2. 형식
```css
display:grid;
```

3. grid 구조
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d238eaab-7107-4a99-8ef0-32dc56fd2765">
<img src="https://github.com/sooyounghan/Web/assets/34672301/54bcd6ac-ae9d-4581-ac3b-e34076520284">
<img src="https://github.com/sooyounghan/Web/assets/34672301/828bff1a-9d18-4b25-9027-d33d5b463d77">
</div>

  - grid-container : grid가 적용된 요소 (부모 요소)
  - grid-item : grid가 적용된 요소의 자식 요소
  - grid-line : grid-item 사이의 경계 (열과 행의 grid-item을 나누는 경계)
  - grid-number : grid-line이 몇 번째 line인지 의미하는 요소

-----
### fr
-----
1. Fraction(분수)의 약자
2. grid-template에서 사용할 수 있는 비율 단위
3. grid의 해당 영역을 지정한 비율로 나눌 수 있음
4. 예시
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ba8ecd6f-5c73-49b9-8b90-44463289ea1a">
</div>

- 해당 grid의 열을 1 : 2 : 1 : 1의 비율로 나눔
- grid-container의 크기가 변경되더라도 비율로 설정했으므로 비율로 유지

-----
### grid-template-rows
-----
    - Template : 어떠한 요소를 만들 때 가이드의 역할을 하는 기본 틀

1. grid의 행의 개수 및 크기를 지정
2. 형식
```css
grid-template-rows:1fr 2fr 200px;
```

  - 총 grid의 행은 3개를 의미
  - 각 행의 규격 : 1fr 2fr 200px

-----
### grid-template-columns
-----
1. grid의 열의 개수 및 크기 지정
2. 형식
```css
grid-template-columns:1fr 2fr 200px;
```

  - 총 grid의 열은 3개를 의미
  - 각 열의 규격 : 1fr 2fr 200px

-----
### repeat(a, b)
-----
1. grid-template에서 사용할 수 있는 반복 함수
2. b 규격의 grid-template을 a개 생성
3. 예시
```css
grid-template-columns:repeat(4, 1fr);
=
grid-template-columns:1fr 1fr 1fr 1fr
```
  - 1fr 규격을 4개 생성

```css
grid-template-rows:repeat(2, 1fr 200px);
=
grid-template-rows:1fr 200px 1fr 200px
```

  - 1fr 200px 즉, 두 개의 template이 2번 반복

```css
grid-template-rows:3fr repeat(2, 1fr 200px);
=
grid-template-rows:3fr 1fr 200px 1fr 200px
```

  - 정적 설정 + repeat 함수 적용 가능
  - 첫 grid-item은 3fr 규격
  - 나머지는 1fr 200px 즉, 두 개의 template이 2번 반복

-----
### grid-template 예시
-----
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/96ccaede-d9ee-4569-b0c5-63b5138eb049">
</div>

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6240bcd5-8620-4e5f-835b-d55c7512cc08">
</div>

  - 행 : 1 : 2 비율을 가진 총 2개의 열
  - 열 : 200px, 1 : 1 : 1비율을 가진 총 4개의 열

-----
### grid-gap
-----
1. grid-shell : grid-item이 차지하는 공간
2. grid-shell 가장자리에 공백(buffer)을 주는 것
3. 주의사항
  - 인터넷 익스플로러의 경우에는 아예 기능 불가하므로 주의
 4. 예시
```css
grid-gap:5px;
```

-----
### grid-column / grid-row
-----
1. grid-item이 얼마만큼의 영역을 차지할 지 정의
2. 예시
```css
grid-column:1 / 3;
```

3. grid-column : grid-line의 번호를 기준으로 할당
4. grid-row : grid-number의 번호를 기준으로 할당

<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/96ccaede-d9ee-4569-b0c5-63b5138eb049">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6240bcd5-8620-4e5f-835b-d55c7512cc08">
</div>

  - 이 위에 다음 속성을 가진 item을 얹으면?
```css
grid-column : 1 / 4;
grid-row : 2 / 3;
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/84dd15fc-1b19-446c-a04a-da2b785d76dd">
</div>

  - column은 grid-line 1번에서부터 4번까지를 의미
  - row는 grid-number 2번에서부터 3번까지를 의미


-----
### grid-template 예제
-----
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>09-01-grid</title>
    <link rel="stylesheet" href="./index.css">
</head>
<body>
    <div class="container">
        <div class="item item1">
            item1
        </div>
        <div class="item item2">
            item2
        </div>
        <div class="item item3">
            item3
        </div>
        <div class="item item4">
            item4
        </div>
        <div class="item item5">
            item5
        </div>
        <div class="item item6">
            item6
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
    border:2px solid red;

    display:grid;
    grid-template-columns:repeat(2, 1fr 2fr);
    grid-template-rows:repeat(4, 100px);
    grid-gap:5px;
}

.item {
    border:2px solid blue;
}

.item1 {
    background-color:green;
    
    grid-column : 1 / span 2;
    /* grid-column:1/4; */
    grid-row:1/2;
}
```

1. grid-row(column) : 1 / span n
   - 1번 grid number(혹은 grid line)에서부터 1번 라인을 포함하여 n칸을 차지

2. grid-column : 1 / span 2
   - 1번 grid line에서부터 1번 라인을 포함하여 2칸 차지

3. grid-row : 1 / span 4
   - 1번 grid number에서부터 1번을 포함하여 4칸 차지
  
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9d5a9bd0-34d7-4b75-bcfa-de6f2c0ab715">
</div>
