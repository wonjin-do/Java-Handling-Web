




# DataBase
## 사용자 생성 / 권한부여
1. sqlplus -> system/1234 로 접속
2. create user scott identified by tiger;
3. grant resource , connect to scott;

## DBMS 수동 설정하기
1. 내컴퓨터>우클릭_관리>서비스및응용프로그램>서비스> OracleServiceXE, OracleXTNSListner를 수동으로 설정.

# 톰캣서버에 배포하기
## 수동배포
### 컨텍스트란 : server.xml에 등록하는 웹 어플리케이션을 뜻함.
톰캣 컨테이너에 컨텍스트 등록하기.tomcat/conf/server.xml
~~~
<Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">
          <Context path="/webMal"
                    docBase="c:\webShop"
                    reloadable="true"/>
        ...............             
      </Host>
~~~
~~~
<Context path="/컨텍스트 이름 명명" docBase="웹 어플리케이션 실제경로" reloadable="true"/>
~~~
를 달아준다.




          
