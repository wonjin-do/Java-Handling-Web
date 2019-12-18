# 자바 웹을 다루는 기술

[톰캣](#톰캣)
[DataBase](#DataBase)
[웹어플리케이션_폴더_구조](#웹어플리케이션_폴더_구조)
[개발환경_폴더구조](#개발환경_폴더구조)
[수동배포와 컨택스트의 의미](#수동배포)

## 개발을 하고 싶어요
## Coding을 잘하고 싶어요

# JDK 10 설치

# 톰캣
## tomcat 9 

Core > Windows Service Installer > 기본설정으로 next버튼 누르며 설치<br>
tomcat 8(이전버전)을 삭제하고 싶을 땐 cmd창에 
~~~
sc delete Tomcat8
~~~
## 톰캣서버 기본구조
내용이 너무 많아서 다음 블로그 참고 https://jang8584.tistory.com/72 <br>

가상의 WAS를 통하여 개발이 진행됨. 이클립스는 실제 설치된 톰캣을 Server 설정을 통해 연동한 경우 런타임 환경만 실제 톰캣의 것을 사용하며 배포 경로는 가상의 경로를 이용합니다.<br>
tmp0은 이클립스 servers 뷰에서 보이는 서버의 index같은 것입니다.
이클립스에 server를 여러개 만드는 경우 tmp0, tmp1 식으로 여러개의 서버가 생성됩니다.

```
workspace\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps

```


# DataBase
## 사용자 생성 / 권한부여
1. sqlplus -> system/1234 로 접속
2. create user scott identified by tiger;
3. grant resource , connect to scott;

## DBMS 수동 설정하기
1. 내컴퓨터>우클릭_관리>서비스및응용프로그램>서비스> OracleServiceXE, OracleXTNSListner를 수동으로 설정.

# exERD 를 이클립스에 설치하기
Help > install New software > add > Name : exERD , Location : http://exerd.com/update <br>
설치를 마치고 나면 File > New > others 이후 eXERD 폴더가 보이면 정상

## 웹어플리케이션_폴더_구조
~~~
webApplication Name(줄여서 app으로 표기)
              ┗ WEB-INF            // 외부에서 접근 불가능
                     ┗ classes     // 서블릿, 클래스
                     ┗ lib         // 라이브러리 압축파일(jar), DB연동 드라이버, 프레임워크 기능 관련jar 파일
                                      lib의 jar는 클래스 패스가 자동으로 설정된다.
                     ┗ bin         // 각종 실행 파일이 위치한 곳
                     ┗ conf        // 프레임워크에서 사용하는 각종 설정 파일이 저장된 곳
                     ┗ web.xml     // 배치 지시자(deployment decriptor)로서 일종의 환경설정파일
~~~

## 개발환경_폴더구조
### JSP_개발환경에서의_구조
~~~
project Name
       ┗ java Resources
       ┃      ┗ src
       ┃      ┗ Libraies
       ┃            ┗ JRE System Library[JavaSE-1.8]
       ┃            ┗ Web App Libraries
       ┃                    ┗ commons-dbcp.jar
       ┃                    ┗ commons-logging.jar
       ┃                    ┗ commons-pool.jar
       ┃                    ┗ mysql-connector.jar
       ┗ javaScript Resources
       ┗ build
       ┗ WebContent
              ┗ META-INF
              ┗ WEB-INF
                  ┗ lib
              ┗ web.xml
~~~

### 스프링 프레임워크_개발환경에서의_구조
~~~
project Name
       ┗ src
       ┃  ┗ main  
       ┃  ┃   ┗ java
       ┃  ┃   ┗ resource
       ┃  ┃   ┗ WEB-INF            // 외부에서 접근 불가능
       ┃  ┃         ┗ classes     // 서블릿, 클래스
       ┃  ┃         ┗ config
       ┃  ┃         ┃    ┗ presentation-layer.xml
       ┃  ┃         ┗ web.xml     // 배치 지시자(deployment decriptor)로서 일종의 환경설정파일
       ┃  ┗ test
       ┃      ┗ java
       ┃      ┗ resource
       ┃             ┗ applicationContext.xml
       ┗ Maven Dependencies
       ┗ pom.xml
~~~

## 수동배포
### CATALINA_HOME 이란?
JDK의 루트디렉토리를 JAVA_HOME이라고 부른것 처럼 <br>
톰캣의 루트디렉토리 C:/tomcat9/ 을 뜻함.
~~~
C:/tomcat9/             // CATALINA_HOME
          ┗ webapps     // 웹어플리케이션 폴더 webShop(위 웹어플리케이션 기본구조를 갖춘 폴더)를 복붙하면 배포가 이루어짐.
            ┗ app1
            ┗ app2
            ┗ app3
            ┗ 보이지 않지만 server.xml에서 컨텍스트를 추가할 수 있다. <Host> 자식태그 <Context path=" ">     
            ┗....
          ┗ bin
          ┗ conf
          ┗ lib
          ┗ log
          ┗ temp
          ┗ work
~~~
### 컨텍스트란 : server.xml에 등록하는 웹 어플리케이션을 뜻함.
특징1. 웹어플리케이션당 하나의 컨텍스트가 등록된다.
특징2. 웹어플리케이션이름과 다른 별도의 별칭을 부여할 수 있다.
톰캣 컨테이너에 컨텍스트 등록하기.tomcat/conf/server.xml
~~~
<Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">
          <Context path="/webMal"           //요청URL의 형태가 /webMal일때
                    docBase="c:\webShop"    //컨텍스트를 C:\webShop으로 잡아라
                    reloadable="true"/>
        ...............             
      </Host>
~~~
~~~
<Context path="/컨텍스트 이름 명명" docBase="웹 어플리케이션 실제경로" reloadable="true"/>
~~~
를 달아준다.




          
