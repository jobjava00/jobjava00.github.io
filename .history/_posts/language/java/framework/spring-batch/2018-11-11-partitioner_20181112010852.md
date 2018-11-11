---
layout: archive
title: "[Spring Batch] partitioner"
date: 2018-11-11
excerpt: ""
tags: [language, java, framework, spring-batch, Spring Batch 소개]
category: [language/java/framework/spring-batch]
#read_time: true
#share: true

sidebar:
  nav: "java-framework"
---

# 정리

* * *

## 파티셔닝 (Partitioning)의 개념

![partitioner01](/assets/image/language/java/framework/spring-batch/partitioner01.png)

![partitioner02](/assets/image/language/java/framework/spring-batch/partitioner02.png)

* 파티셔닝이란, 병렬로 chunk 단위(각 slave들)을 동시에 수행하는 것
* partitioner는 paging 역할을 하여 데이터를 병렬적으로 읽게 해줌
* master도 한 스텝이고, slave도 별도의 스텝

## 참고

* <http://marobiana.tistory.com/131>