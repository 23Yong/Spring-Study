# URI와 웹 브라우저 요청 흐름

>## URI (Uniform Resource Identifier)
>
>- Uniform: 리소스를 식별하는 통일된 방식
>
>- Resource: 자원, URI로 식별할 수 있는 모든 것
>
>- Identifier: 다른 항목과 구분하는데 필요한 정보
>
><img src="https://t1.daumcdn.net/cfile/tistory/2416C94158D62B9E11" alt="URI vs URL vs URN :: 마이구미 :: 마이구미의 HelloWorld" style="zoom:50%;" />
>
>### URL, URN
>
>- URL - Locator: 리소스가 있는 위치를 지정
>
>- URN - Name: 리소스에 이름을 부여
>
>- 위치(Locate)는 변할 수 있지만, 이름(Name)은 변하지 않는다.
>
>#### URL
>
>- URI의 가장 흔한 형태
>
>- 특정 서버의 한 리소스에 다한 구체적인 위치를 서술
>
>- 리소스가 정확히 어디에 있고 어떻게 접근할 수 있는지 서술
>
>
>
>#### URN
>
>- 리소스의 위치에 영향을 받지 않는 유일한 이름 역할을 수행
>
>- 이미 널리 상용화된 URL 주소 체계를 완전히 바꾸는 것은 무리..
>
>---
>
>#### URL 분석
>
>https://www.google.com:443/search?q=hello&hl=ko
>
>scheme://[userinfo@]host [port] [/path] [?query] [#fragment]
>
>- 프로토콜(https)
>
>- 호트스명(www.google.com)
>
>- 포트번호(443)
>
>- 패스(/search)
>
>- 쿼리 파라미터(q=hello&hl=ko)
>
>##### scheme (https)
>
>- 리소스에 접근하기 위해 사용되는 프로토콜
>  - ex. http, https, ftp, smtp..
>
>##### userinfo
>
>- URL에 사용자 정보를 포함해서 인증할 때 사용
>
>- 거의 사용하지 않음
>
>##### host(www.google.com)
>
>- 호스트명
>
>- 도메인명 또는 IP 주소를 직접 사용가능
>
>##### port(443)
>
>- 접속 포트
>
>- 일반적으로 생략, 생략시 http = 80, https = 443
>
>###### path(/search)
>
>- 리소스 경로(path)
>
>##### query(?q=hello&hl=ko)
>
>- key=value 형태
>
>- ?로 시작, &로 추가 가능
>
>##### fragment
>
>- html 내부 북마크에 사용
>
>- 서버에 전송하는 정보가 아님
>
>- 리소스 자체의 다른 부분을 가리키는 앵커
>
>  ---
>
>  
>
>## 웹 브라우저 요청 흐름
>
>웹 브라우저와 서버의 통신
>
>(https://www.google.com:443/search?q=hello?hl=ko)
>
>> 1. 브라우저는 HTTP 요청메시지 생성
>>    - GET /search?q=hello&hl=ko HTTP/1.1 Host:www.google.com
>> 2. HTTP 메시지 전송
>>    - 브라우저가 SOCKET 라이브러리를 통해 전달
>>    - TCP/IP 패킷 생성, HTTP 메시지 포함
>>      - HTTP메시지를 TCP/IP 패킷이 감싸는 이미지
>>    - NIC를 거쳐 인터넷을 통해 서버로 전달
>> 3. 브라우저가 요청 패킷을 서버로 전달 후 서버로 요청 패킷 도착
>> 4. 서버는 HTTP 응답 메시지 생성후 위와 같은 방식으로 브라우저에게 응답 패킷 전달
>>    - HTTP/1.1 200 OK ...
>> 5. 브라우저는 도착한 응답 패킷을 화면에 HTML 렌더링