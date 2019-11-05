
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
