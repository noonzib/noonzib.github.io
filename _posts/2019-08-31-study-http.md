---
layout: post
title:  "http 정리"
date:   2019-08-31
excerpt: "웹 어플리케이션 기술"
tag:
- web application
- http
comments: true
---

# HTTP protocol
    * 메시지 기반 모델로서 클라이언트가 요청을 보내고 서버가 그에 대한 응답 메시지를 보내는 방식이다.
    * 비연결지향적 프로토콜

* HTTP 요청
    * 헤더를 통해 다양한 정보를 포함하고 있으며, 각 헤더마다 특정 정보를 갖고 있다.

## HTTP 요청 첫번째 줄
## GET /auth/488/xxx.ashx?uid=129 HTTP/1.1
    1. HTTP 전송방법
    2. 요청된 URL
    3. HTTP 버전

* HTTP 응답

## HTTP 응답 첫번째 줄
## HTTP 1.1 200 ok
    1. HTTP 버전
    2. 요청에 대한 결과 코드
    3. 응답에 대한 상황을 설명해 주는 문자열

* HTTP 메소드
    * GET 메소드 - 웹 서버에 있는 자원을 얻을때 사용, 요청된 자원의 URL 쿼리 문자열에 인자 값을 보내는 용도로도 사용
    * POST 메소드 - 특정 행동을 시작할 때 사용한다, 인자를 메시지의 바디에 보냄
    * HEAD 메소드 - GET과 비슷함, 응답할 때 메시지 바디를 보내지 않음
    * TRACE 메소드 - 프록시서버가 요청을 조정하는지 여부 판단
    * OPTIONS 메소드 - 특정 자원에 맞는 HTTP 방식을 알려달라고 서버특에 요청
    * PUT 메소드 - 서버에 임의의 스크립트를 서버에 올료 실행할 수도 있음

* URL 형식
    > 프로토콜://호스트명[:포트번호]/[경로/]파일명[?param=값]

* REST
    * 분산 시스템에서 사용하는 아키텍처의 한종류
    * 요청, 응답 내용에 시스템 자원의 현재 상태가 나타나있다.

* HTTP 헤더
    1. 일반적인 헤더
        * Connection - HTTP 전송 완료후 TCP 연결 차단 여부확인
        * Content-Encoding - 메시지 바디 내용에 어떤 종류의 인코딩을 사용할지 정할 때 쓰임
        * Content-Length - 메시지 바디 길이
        * Content-Type - 메시지 바디에 들어있는 콘텐츠 종류
    2. 요청헤더
        * Accept - Client가 그림 파일이나 문서 형식등 어떤 종류의 내용을 수락 할 것인지 서버에 알리는 역할을 한다.
        * Accept-Encoding - Client가 어떤 종류의 인코딩된 문서를 받아들일지 서버에게 알리는 역할을 한다.
        * Authorization - 사용자의 식별 정보를 서버에게 보낼때
        * Cookie - 서버로부터 받은 쿠키를 다시 서버에게 보내주는 역할
        * Host - 요청된 URL에 나타난 호스트명
        * If-Modified-Since - 브라우저가 마지막으로 요청 자료를 받은 시간을 나타낸다.
        * If-None-Match - 엔티티 태그를 지정하기 위해 사용한다.
        * Origin - 크로스 도메인 Ajax 요청에서 요청이 시작된 도메인을 나타내기 위해 사용 
        * Referer - 현재 요청이 처음시작된 곳의 URL
        * User-Agent - 요청하는 브라우저의 정보
    3. 응답헤더
        * Access-Control-Allow-Origin - 크로스 도메인 Ajax 요청으로 리소스를 가져올 수 있는지 여부
        * Cache-Control - 캐시에 대한 지시를 브라우저에게 전달하는 역할을 한다
        * Etag - 엔티티 태그를 나타낼 때 사용한다
        * Expires - 브라우저는 요청한 자원에 대해 Expires 시간까지 클라이언트의 하드에 저장된 복사본 내용을 사용한다.
        * Location - 재전송하는 응답에서 목적지를 나타내는데 쓰임
        * Pragma - 브라우저에게 캐싱 지시를 보내기 위해 사용
        * Server - 사용하는 웹 서버의 소프트웨어에 대한 정보제공
        * Set-Cookie - 쿠키를 생성하고 브라우저에 보낼때 사용

* 쿠키
    * Server가 클라이언트에게 데이터를 보낼 수 있게하고, Client가 쿠키를 저장해 뒀다가 다시 서버에게 보냄

* Set-Cookie 헤더의 추가 속성
    * Expires - 쿠키 유효시간을 나타낸다
    * domain - 쿠키를 사용할 수 있는 도메인
    * path - 쿠키가 사용할 수 있는 URL 경로를 나타낸다
    * secure - 쿠키를 HTTPS 요청으로만 전송
    * Http Only - 쿠키는 Client 쪽의 JS로 직접 접근할 수 없다

* 상태코드
    1. 1XX - 정보제공
    2. 2XX - 요청이 성공적으로 이뤄짐
    3. 3XX - 요청한 해당 자원이 다른 곳에 있음
    4. 4XX - 요청에 문제가 있음
    5. 5XX - 서버에 문제가 있음

* HTTPS
    * HTTP와 같이 애플리케이션 계층 프로토콜로 SSL을 이용해 클라이언트와 서버 사이에 주고받는 정보를 보호

* HTTP 프록시
    * 클라이언트 브라우저와 목적지 웹서버 간에 중개 역할
    * 캐싱, 인증, 접근 통제 같은 서비스를 제공함

* HTTP 인증
    * Basic - 메시지 요청 헤더에 Base64로 암호화한 문자열을 사용자 자격 증명으로 보낸다.
    * NTLM - 시도/응답 방법, 윈도우 NTLM 프로토콜 사용
    * Digest - 시도/응답 방법, MD5 체크섬을 사용        