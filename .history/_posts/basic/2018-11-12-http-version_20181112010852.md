---
layout: archive
title: "[Basic] HTTP 버전별 특징"
date: 2018-11-11
excerpt: ""
tags: [basic, HTTP 버전별 특징]
category: [basic]
#read_time: true
#share: true

sidebar:
  nav: "main"
---

# 정리

* * *

## HTTP 1.0

* 단기 커넥션(Short-lived connections)
* Request를 날릴 때마다 Connection을 새로 생성
* 데이터 전송
  * 플레인텍스트
  * Data를 압축해서 전달이 가능하도록 하여 전달하는 Data 양이 감소

## HTTP 1.1

* 지속 커넥션(Persistent connection)
* 커넥션 재사용 가능
* HTTP 파이프라이닝(Pipelining)
  * Request를 미리 여러개 서버에 날릴 수도 있게 되었다
* 한 Reuqest 당, 한 개의 리소스를 받아옴
* 헤더 압축으로 인한 성능 향상
* 단점(Head Of Line Blocking)
  * 요청한 Request에 문제가 있어서, 응답이 늦어지면 2번째, 3번째에 요청한 Request의 응답도 같이 늦어짐

## HTTP 2.0

* Multiplexing
  * 프레임 단위로 나눠서 전송,관리 가능하게 됨.   * 다수의 요청과 응답이 가능한 구조
* 데이터 전송
  * 바이너리로 인코딩하여 전송
* ServerPush 사용
  * 브라우저에서 필요한 리소스들을 서버가 알아서 찾아다가 내려주는걸 의미한다
  * 필요한 경우
    * 캐싱되지 않은 리소스를 받아올 때
    * 페이지에서 필요한 리소스가 페이지를 내려주는 서버에 있을 때

## 참고

* <http://americanopeople.tistory.com/115>