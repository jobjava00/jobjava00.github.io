---
layout: archive
title: "[xUnit 테스트 패턴] 소개"
date: 2018-10-28
excerpt: ""
tags: [book, xunit, xUnit 테스트 패턴, introduce]
category: [book/xunit]
#read_time: true
#share: true

sidebar:
  nav: "book"
---

# 정리

* * *

## 깨지기 쉬운 테스트

* 동작에 민감함
  * 시스템의 동작이 변경될 경우 테스트를 다시 돌리면 실패 함.
* 인터페이스에 민감함
  * 사용자 인터페이스가 약간만 바뀌어도 테스트가 실패
* 데이터에 민감함
  * 데이터 자체가 변경되는 경우 테스트가 실패
* 문맥에 민감함
  * 시스템 동작은 시스템 외부 상태에 따라 영향을 받는다.
    * ex) 장비의 상태, 시스템 시간, 다른 프로그램들..

## 명세로서의 테스트

* 테스트 주도 개발에서의 자동 테스트
  * 작성해야 하는 소프트웨어 기능을 명세로 쓴다.

## 용어

* SUT(System Under Test) - 테스트 대상 시스템
  * 테스트하려는 대상 모두
  * ex) 클래스, 메소드, 애플리케이션 등등
* DOC(Depended-On Component) - 의존 컴포넌트
  * SUT에서 호출하거나 실행할 때 필요한 데이터를 미리 설정하는데 필요한 부분