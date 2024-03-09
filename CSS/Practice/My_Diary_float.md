-----
### HTML
-----
1. 상단바 작업 : header 태그
2. 총 3개의 div 생성 : logo / menu / user
3. menu div 내에는 총 3개의 메뉴 생성 : ul 태그 및 li 태그 사용
   - 각 li는 a 태그를 통해 추후 메뉴 이동
4. user 태그는 이미지 삽입
5. float의 left / right 속성을 제거하기 위한 clearset div 생성

```html
    <header class="header">
        <div class="header-inner">
            <div class="logo">
                <h1><a href="#none">HAGD</a></h1>
            </div>
            <div class="menu">
                <ul class="menu__ul">
                    <li>
                        <a href="#none">어제의 일기</a>
                    </li>
                    <li>
                        <a href="#none">오늘의 일기</a>
                    </li>
                    <li>
                        <a href="#none">내일의 일기</a>
                    </li>
                    <div class="clearfix"></div>
                </ul>
            </div>
            <div class="user">
                <img src="../img/portrait.png" alt="유저 정보", width = "32", height = "32">
            </div>
            <div class="clearfix"></div>
        </div>
    </header>
```

-----
### CSS
-----

```css
* {
    box-sizing:border-box;
    margin:0;
    padding:0;
}

.header {
    border-bottom:1px solid gray;
}

.header-inner {
    width:900px;
    height:100%;
    margin:0 auto;
}

.logo {
    float:left;
    width:100px;
    height:80px;
    padding-top:18px;
    padding-left:10px;
}

.logo h1 a {
    text-decoration:none;
    color:orange;
}
.menu {
    float:left;
    width:calc(100% - 200px);
    height:80px;
    text-align:center;
}

.menu__ul {
    display:inline-block;
}
.menu__ul li {
    float:left;
    list-style:none;
}

.menu__ul li a {
    display:block;
    color:black;
    text-decoration:none;
    padding :29px 20px;
}

.menu__ul li a:hover{
    color:orange;
}

.user {
    float:left;
    width:100px;
    height:80px;
    padding-top:23px;
}

.clearfix {
    clear:both;
}
```

1. margin:0 auto
   - 위와 같이 설정하면 자연스럽게 가운데 정렬 가능

2. float 설정이 적용된 logo / menu / user로 인해 전체 header가 left까지 영향을 받음
   - clearfix div 설정을 통해 이후 영역에 영향을 받지 않도록 clear:both 설정

3. menu는 logo과 user의 width를 뺀 값
   - cacl() 이용 : calc(100% - 200px) [전체 해당 div 크기에서 각각 차지하는 픽셀 제거 / 공백 항상 필요]

4. ul과 li는 Block 요소이므로 float를 적용하게 되면, 또 이 영향을 받는 것도 left 영향
   - 따라서, clearfix를 선언하여 이후 영역이 영향을 받지 않도록 설정
   - list-style : li의 Boolet 설정 (none : 없음)

5. display:inline-block
   - Block 요소에 대해 Inline 요소를 적용
   - 그러나, Block 요소처럼 크기 설정이 가능하도록, 즉 두 개의 요소가 중첩되도록 설정
