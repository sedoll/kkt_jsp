# 웹 프로젝트 생성
1. [File] - [New] - [Project]
2. Project name, Location을 입력 및 지정 -> [OK]
3. 해당 프로젝트 디렉토리에서 마우스 오른쪽 버튼 -> [Add Framework Support...]
4. Java EE 항목의 Web Application 만 체크 -> Version : 4.0, Create web.xml 체크 [OK]

# apache Tomcat 설치
Web Server : apache, nginX	-> jsp, php, asp 를 실행

Web Application Server : Tomcat -> .jsp, .xml, .java로 만들어진 .class 를 실행 -> war, jar, ear -> Web Container

1. tomcat9을 검색하여 https://tomcat.apache.org/download-90.cgi 를 방문하여 원하는 타입의 프로그램을 다운로드 한다.

2. 여기서는 64-bit Windows.zip 를 선택하여 다운로드 받은 후

3. d:\name\server 에 복사하여 붙여 넣고, 압축을 해제한다.
-----------------------------------------------------------------------
4. d:\kim\server\apache-tomcat-9.0.78-windows-x64\apache-tomcat-9.0.78\conf 의 server.xml의 포트번호 8080을 8081로 모두 변경하고, 저장
### 변경 전
```xml
<Connector port="8080" protocol="HTTP/1.1"
       connectionTimeout="20000"
       redirectPort="8443"
       maxParameterCount="1000"
       />	
<Connector executor="tomcatThreadPool"
     port="8080" protocol="HTTP/1.1"
     connectionTimeout="20000"
     redirectPort="8443"
     maxParameterCount="1000"
     />
```

### 변경후
```xml
<Connector port="8081" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443"
               maxParameterCount="1000"
               />	
<Connector executor="tomcatThreadPool"
   port="8081" protocol="HTTP/1.1"
   connectionTimeout="20000"
   redirectPort="8443"
   maxParameterCount="1000"
   />
```

# apache Tomcat 설정
1. 상단 configurer (Current File) 을 클릭 -> [Edit Configurations...]
2. [+] Add New Configuration -> Tomcat Server : Local 선택
3. Name : tomcat9, 

## Server 탭 -> 
1) Application server : 의 오른쪽 끝의 [Configure...]버튼 클릭하여 [+]를 눌러 Tomcat 설치했던 디렉토리를 지정 -> [OK]
2) Open browser 를 Default -> Chrome으로 변경
3) Tomcat Server Settings 항목의 HTTP Port를 8080에서 8081로 변경
## Deployment 탭 ->
1) [+] 을 눌러 Artifacts를 선택하면, ch01.war exploded 를 생성
2) Application context : / 로 변경		
3) [OK] 버튼
4) 해당 프로젝트 선택 후, Run 'tomcat9' 또는 [Shift+F10]을 누르면, 자동으로 브라우저 실행되고, 메인(index.jsp) 페이지를 실행시켜줌
	1. 해당 프로젝트의  src 디렉토리에서 마우스 오른쪽 버튼 -> [Open Module Settings...] 클릭
	2. 왼쪽 메뉴의 Project Settings 에서 Libraries 선택 -> [+] New Project Libraries] 클릭
	-> From Maven.. 클릭
	3. 입력란에 javax.servlet 를 입력하고, Search(돋보기) 를 눌러 검색하여 목록이 나오면,
	javax.servlet:javax.servlet-api:4.0.1 를 선택 -> [OK] -> [Apply] -> [OK]
	4. [File] > [Settings] > Editor > File and Code Templates
	> Other 탭 > 좌측 Web > Java code templates > Servlet Class.java 를 선택하여 그 안의 템플릿 내용을 복사하기 
	> Files 탭 > [+] > Name : Servlet > 내용에 붙여넣기 한 후 저장

	인텔리제이에서 tomcat9 에서 해당 프로젝트 디렉토리를 선택하여 실행하면,
	http://localhost:8081/  로 열리면서 index.jsp 로 띄움
