---
layout: archive
title: "스프링 특징"
date: 2018-11-09
excerpt: ""
tags: [language, java, framework, spring, 스프링 특징]
category: [language/java/framework/spring]
#read_time: true
#share: true

sidebar:
  nav: "java"
---

# 정리

* * *

## 프레임워크란

* 뼈대나 근간을 이루는 코드들의 묶음
* 프레임워크(Framework) 사용이유?
  * 개발 속도 단축 (틀을 이미 만들어 놓았기 때문)
  * 일정한 품질이 보장됨

### 스프링 선택 이유

* 경량 컨테이너
  * EJB 등의 기존 프레임워크에서 만들어진 코드에 비해 코드량이 적고 단순
  * 크기와 부하의 측면에서 경량
* 다른 프레임워크와의 결합이 쉽다.
  * Hibernate, Mybatis
* 많은 부분을 프레임워크에서 처리
  * Servlet 처리와 같은 부분들
* 개발 생산성 향상
  * 비즈니스로직에 집중할 수 있게 함
  * POJO 기반 구성
    * 특정한 라이브러리/컨테이너 기술에 종속적이지 않기 때문에 생산성/테스트 수월
  * AOP
    * 공통 관심요소를 단일 기능으로 뽑아내어 코드의 중복을 줄이고 관리의 효율성을 높임
    * ex) 트랜젝션/로깅/예외 처리
  * DI
    * 의존성 제거로 인한 변경의 유연성을 가짐

## 참고

* <https://blog.naver.com/93kwiyoung/221390879199>