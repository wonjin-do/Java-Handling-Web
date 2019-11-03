# 서블릿API 계층구조
~~~
Servlet  ServletConfig   // 인터페이스
    \     /
     \   /  (구현)
      \ /
 GenericServlet         // 클래스
       |
       | (상속) ~ 프로토콜에 따라 메소드 service()를 오버라이딩해서 구현함.
       |
  HttpServlet           // 자식클래스 : http프로토콜을 채택하여 웹브라우저 기반 서블릿을 만들 때 상속받아 사용한다.
~~~

# 이클립스에서 서블릿 클래스를 사용하려면?
서블릿API들(클래스들)은 톰캣의 servlet-api.jar 라이브러리로 제공됨.
~~~
tomcat
  ┗ lib
    ┗ servlet-api.jar
~~~
이클립스 프로젝트 이름 우클릭 > Build Path > Libraries탭 > Add External JARs.. > 위 파일 선택하여 추가한다.
이 과정은 프로젝트에 종속되므로 다른 프로젝트를 생성하면 다시 과정을 밟아나간다.



    
## 서블릿 요청데이터 인코딩 설정 / 응답데이터 contentType 설정
요청데이터 : request.setCharacterEncoding("utf-8"); //인코딩 설정
응답데이터 : response.setContentType("text/html;charset=utf-8"); //응답데이터의 데이터타입(MIME-TYPE)

응답데이터의 데이터 타입을 설정해주는 이유
