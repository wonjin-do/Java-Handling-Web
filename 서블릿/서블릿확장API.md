
# 포워드 기능
## redirect / Refresh / location
새로운 요청흐름이 발생함. 브라우저에게 강제함.<br>

redirect : response.sendRedirect("***.jsp");
refresh : response.addHeader("Refresh",경과시간(초);url=***.jsp");
location : location.href = '***.jsp';

## dispatch
기존 요청흐름을 유지함. 이전의 request 객체가 계속 유지됨.
RequestDispatcher dis = request.getRequestDispatcher("***.jsp");
dis.forward(req, res);

# ServletContext & ServletConfig 사용법

## ServletContext클래스
### 톰캣컨테이너 실행시 각 컨텍스트(웹어플리케이션)마다 한 개의 컨택스트객체를 생성.
### 톰캣컨테이너 종료시 컨텍스트객체 소멸
### 어플리케이션 내에서 공통 자원이나 정보를 서블릿들끼리 공유
1) 서블릿에서 파일 접근가능하게 함.
2) 자원바인딩 setAttribute, getAttribute
3) 로그파일기능
4) 컨텍스트에서 제공하는 설정 정보 제공 기능
~~~
톰캣컨테이너
    ┗ app1(컨텍스트)
          ┗ ServletContext    // 컨택스트마다 1개
          ┗ A Servlet
              ┗ A ServletConfig // 서블릿마다 1개
          ┗ B Servlet
              ┗ B ServletConfig // 서블릿마다 1개
    ┗ app2(컨텍스트)
    ┗ app3(컨텍스트)
    ┗ ...
~~~
따라서, 단일 웹어플리케이션내에서 모든 사용자가 공통으로 사용하는 데이터는 ServletContext에 바인딩해서 사용할것.
~~~
//A.java
ServletContext context = getServletContext();
context.setAttribute("name", object);
~~~
~~~
//B.java
ServletContext context = getServletContext();
Object obj = (형변환)getAttribute("name");
~~~




