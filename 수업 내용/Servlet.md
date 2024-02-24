-----
### MVC 패턴 (Model-View-Controller)
-----
1. 클라이언트 요청에 따라 Contorller에서 데이터가 필요하면 Model을 통해 DB에 접근해 데이터를 가져옴
2. View에서 보여줄 화면을 데이터와 함께 만들어서 클라이언트 측에 제공 (데이터가 필요 없으면 바로 View로 제공)
3. MVC에 대한 표준이 없어서 등장한 것 : MVC FrameWork(Spring, SpringBoot)

-----
### Servlet
-----
참고 자료 : https://github.com/sksrpf1126/study/blob/main/Spring(Spring%20Boot)/Servlet.md

1. 동적 웹 페이지를 만들기 위해 사용되는 자바 기반의 웹 어플리케이션 기술
2. 웹 기반 요청에 대한 동적 처리가 가능한 하나의 클래스
3. 서블릿 구조 (인터페이스)
```jsp
public interface Servlet {

    public void init(ServletConfig config) throws ServletException;


    public ServletConfig getServletConfig();

    public void service(ServletRequest req, ServletResponse res)
            throws ServletException, IOException;

    public String getServletInfo();

    public void destroy();
}
```
4. 서블릿이 만들어지면, init이 호출되어 단 하나의 서블릿 객체만 만들어짐(Singleton Pattern)
5. service 메서드를 통해 서블릿 객체를 통해 실행할 코드 작성 (Servlet을 구현하는 HttpServlet 클래스를 통해 실행)
6 destory 메서드는 보통 서블릿 컨테이너가 종료될 때 실행되며, 해당 Servlet 인스턴스 제거
