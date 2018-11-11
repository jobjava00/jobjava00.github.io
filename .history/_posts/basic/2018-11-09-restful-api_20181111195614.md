---
layout: archive
title: "[Basic] RESTful API"
date: 2018-11-09
excerpt: ""
tags: [language, java, basic, RESTful API]
category: [language/java/basic]
#read_time: true
#share: true

sidebar:
  nav: "main"
---

# 정리

* * *

## REST

* `Re`presentational `S`tate `T`ransfer - 대표적인 상태 전달
  * 자원을 정의하고 자원에 대한 주소를 지정하는 방법론
  * 어떤 자원에 대해 CRUD 연산을 수행하기 위해 URI로 요청을 보내는 것

## REST 구성

* 자원(Resource) - URI
  * 문서, 이미지, 동영상 파일 같은 Resource 요청
* 행위(Verb) - HTTP Method
  * GET, POST, PUT, DELETE, PATCH
* 표현(Representations)
  * JSON, XML, TEXT, RSS

## REST API 특징

* Uniform Interface (일관된 인터페이스)
  * 리소스에 상관없이 동일한 API 메소드를 갖는다.
    * 이미지 리소스에 대한 처리와 문서 리소스에 대한 처리가 일관된 형태로 요청된다.
  * 플랫폼에 무관, 특정 언어나 기술에 종속받지 않는 특징을 의미
* Stateless (무상태성)
  * 세션정보나 쿠키정보를 활용하여 작업을 위한 상태정보를 저장 및 관리하지 않는다.
    * 서버에서 불필요한 정보를 관리하지 않음
* Cacheable (캐시 가능)
  * HTTP 프로토콜 표준에서 사용하는 Last-Modified Tag 또는 E-Tag를 이용하여 캐싱을 구현
* Client-Server Architecture (서버-클라이언트 구조)
  * 서버는 API를 제공, 클라이언트는 사용자 인증, Context(세션, 로그인 정보) 등을 관리하는 등 역할을 구분시킴으로서 서로 간의 의존성을 줄인다.
* Self-Descriptiveness (자체 표현)
  * 요청 메세지만 보고도 이를 쉽게 이해할 수 있는 자체 표현 구조로 되어있다.
* Layered System (계층 구조)
  * 다중 계층으로 구성될 수 있으며 보안, 로드 밸런싱, 암호화 등을 위한 계층을 추가하여 구조를 변경할 수 있다. 또한 Proxy, Gateway와 같은 네트워크 기반의 중간매채를 사용할 수 있게 해준다.

## RESTful 하다

* URI는 자원을 정확하게 인식하기 편하게 표현하는데 집중
* 자원에 대한 행위는 Uniform 하게 HTTP 메소드를 통해 정의
* 나머지 페이로드는 JSON, XML 같은 언어를 이용하여 별도로 정의

## REST의 장점

* 사용이 쉽다.
  * 메시지 자체를 그냥 읽기만 하는 것으로도 메시지의 본래 의도를 파악할 수 있다.
  * 기존 HTTP 인프라를 그대로 이용하기 때문에 REST를 사용하기 위해 별도의 인프라를 요구할 필요가 없다.
* Client-Server가 명확히 분리된다.
  * 클라이언트와 서버의 역할을 명확하게 분리해서 REST API의 제공과 사용으로 분리하여 개발할 수 있다.
* 원하는 데이터 표현을 사용할 수 있다.
  * REST API는 헤더부분에 URI에 대한 처리 메소드를 명시하고, 필요한 실제 데이터는 body부분에 표현하도록 분리시켰다. 페이로드부분을 JSON, XML, YAML 등 원하는 표현 언어로 사용할 수 있다는 장점이 있다.

## REST의 단점

* HTTP 메소드의 한계에 묶인다.
  * 간단한 수준의 메소드만 지원할 수 있다. 예를 들어 '메일을 보낸다.'라는 행위는 단일 메소드로 구현하기 쉽지 않다.
* 표준이 없어서 관리하기 어렵다.
  * REST API는 API설계 가이드일 뿐이지 명시적인 표준이 아니다.
* RDBMS와 어색한 관계
  * REST API를 RDBMS에 적극적으로 사용하기 위해서는 RESTful 한 테이블 구조가 필요하게 되는데, 이것보다는 NoSQL쪽이 더 잘 맞는 추세다.

## 참고

* <https://blog.naver.com/jh_p0415/221361060953>
* <http://it.plusblog.co.kr/220986337770>