---
layout: archive
title: "[JAVA LABRARY] Jackson VS Gson"
date: 2018-12-12
excerpt: ""
tags: [language, java, library, Jackson VS Gson]
category: [language/java/library]
#read_time: true
#share: true

sidebar:
  nav: "language"
---

# 정리

* * *

## jackson

* public field 일 때 - serializable, deserializable
* private field 일 때
  * getter - serializable, deserializable
  * setter - deserializable
* null 표시
* 대용량 json 파일 처리에 유리

## gson

* getter, setter 없이 serializable, deserializable
* reflection 으로 값 설정 및 조회
* serialized 시 값이 null 인 키는 생략 됨
* 저용량 json 파일 처리에 유리

## 참고

* jackson
  * <https://www.novixys.com/blog/jackson-json-serialization/>
  * <https://www.baeldung.com/jackson-field-serializable-deserializable-or-not>

* gson
  * <http://www.javacreed.com/simple-gson-example/>

* 속도비교
  * <http://www.yunsobi.com/blog/entry/java-json-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-%EB%B3%84-parser-%EC%86%8D%EB%8F%84-%EB%B9%84%EA%B5%90>