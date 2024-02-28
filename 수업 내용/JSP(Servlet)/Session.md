-----
### Session
-----

1. 클라이언트와 웹 서버 간 상태를 지속적 유지
2. 웹 서버만에서만 접근 가능하므로 보안 유지에 유리, 데이터 저장에 한계가 없음
3. 오직 웹 서버에만 존재하는 객체
4. 웹 브라우저마다 하나씩 존재하므로 웹 서버의 서비스를 제공받는 사용자를 구분하는 단위가 됨
5. 웹 브라우저를 닫기 전까지 웹 페이지를 이동하더라도 사용자의 정보가 웹 서버에 보관되어 있어 정보를 잃지 않음

<div align = "center" >
<img src = "https://github.com/sooyounghan/Web/assets/34672301/f63dbea0-3390-4f28-90e0-3bb05c65189b">
</div>

<div align = "center" >
<img src = "https://github.com/sooyounghan/Web/assets/34672301/41115fb1-6975-4bb6-a365-ffcd525ce680">
</div>

-----
### Session 생성
-----

< setAttribute >

      void setAttribute(String name, Object value)
      
1. session 내장 객체의 setAttribute() 메서드 사용 [MVC에서 Model 역할]
2. 세션의 속성을 설정하면 계속 세션 상태 유지 가능
3. 동일한 세션 속성 이름으로 세션을 생성하면, 마지막에 설정한 것이 세션 속성 값
    - name : 세션에서 사용할 세션 속성의 이름, 세션에 저장된 특정한 값 찾아오기 위한 키로 사용
    - value : 세션의 속성값 (Object 타입으로, 형변환 필요)

          session.setAttribute("memberId", "admin");

< getAttribute >

1. 세션에 저장된 하나의 세션 속성 이름에 대한 속성 값 가져오기
2. 반환 타입은 Object형이므로 형변환 필요

          Object getAttribute(String name)
   
3. name은 속성 이름 / 해당 속성에 이름이 없는 경우 null 반환

5. 다중 세션 정보 얻기
   - 세션에 저장된 여러 개 세션 속성 이름에 대한 속성 값을 얻기 위해 getAttributeNames()
   - 반환 타입 : Enumeration 객체 타입

  
-----
### Session 유효 시간 설정
-----
1. 세션 유지를 위한 세션의 일정 시간
2. 웹 브라우저에 마지막 접근 시간부터 일정 시간 이내 다시 웹 브라우저에 접근하지 않으면 자동 세션 종료
3. 세션 유효 시간 설정

         void setMaxInactiveInterval(int interval)
         - interval : 세션 유효 시간
         - 세션 유효 시간 기본값 : 1,800초 (초 단위 설정)
         - 예) session.setMaxInactiveInterval(60 * 60)

4. 세션 유효 시간이 음수이면, 세션 유효 시간이 없는 상태
   (세션 삭제했을 때, session.invalidate()를 호출하지 않으면, 세션 속성이 웹 서버에서 제거 되지 않고 유지)
5. session.invaildate() 메서드를 명시적으로 실행하지 않으면, 이 세션 떄문에 메모리 부족현상 발생 가능
