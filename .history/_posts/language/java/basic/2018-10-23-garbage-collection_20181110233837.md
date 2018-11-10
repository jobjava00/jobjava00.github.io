---
layout: archive
title: "GC - Garbage Collection"
date: 2018-10-23
excerpt: ""
tags: [language, java, basic, Garbage Collection]
category: [language/java/basic]
#read_time: true
#share: true

sidebar:
  nav: "language"
---

# 정리

* * *

## GC 란

* 프로그램이 동적으로 할당했던 메모리 영역 중에서 필요없게 된 영역을 해제하는 기능
* JVM에서는 Heap영역의 메모리를 자동으로 관리

## GC 기본 개념

![garbage-collection01](/assets/image/language/java/basic/garbage-collection01.jpg)

* GC 과정
  1. 객체 생성 -> Eden 영역에 생성
  2. Eden 영역 꽉 차면 minor GC 발생 -> 살아남은 객체 Survivor 영역(2개중 하나)으로 이동
  3. Survivor 영역 꽉 차면 minor GC 발생 -> 살아남은 객체들 나머지 Survivor 영역으로 이동(GC가 일어난 Survivor영역은 비어있어야 함)
  4. Survivor1 영역과 2영역을 왔다 갔다하는 과정을 반복하다가 계속 살아있는 객체는 Old 영역으로 이동
  5. Old영역에 있는 모든 객체들을 검사하여 참조되지 않은 객체들을 한꺼번에 삭제 major GC 발생

## GC 영역 설명

* Young Area
  * 새로 생긴 객체의 대부분이 여기에 위치합니다.
  * Eden Area, Survivor Area (2개)로 구성됩니다.
  * Minor GC가 발생
* Old Area
  * Young Area에서 살아남은 객체가 여기에 위치
  * Major GC 또는 Full GC가 발생

## stop-the-world

* 모든 GC방식에서 발생
* GC을 실행하기 위해 JVM이 모든 애플리케이션 실행을 멈추는 것

## GC 방식

* 시리얼 콜렉터 (Serial Collector)
  * Old 영역의 객체들은 Mark-sweep-compact 알고리즘을 따른다.
  * 살아있는 객체를 식별하고(Mark), Old영역의 가장 앞부분 부터 살아 있는 것만 남기고 삭제하며(Sweep), 마지막으로 살아있는 객체들을 가장 앞쪽으로 모아준다.(Compact)
  * 굉장히 느리다.
    * 그렇지만 그만큼 시스템 자원을 덜 사용
  * 속도와 별 상관이 없고, 시스템 자원이 부족할 때 사용하는 GC 방식
* 병렬 콜렉터 (Parallel Collector)
  * 시리얼 콜렉터 방식과 GC 알고리즘은 같다.
  * GC를 처리하는 스레드가 여러개
  * 시스템 자원이 넉넉할 때 유리한 방식
* 병렬 압축 콜렉터 (Parallel Compacting Collector)
  * 병렬 콜렉터 방식과 비슷
  * Old 영역의 GC에서 Mark-Summary-Compaction 알고리즘을 채택
  * Sweep과 Summary의 차이
    * Sweep은 단일 스레드가 Old 영역 전체를 훑어 살아있는 객체만 찾아내는 방식이지만, Summary는 여러 스레드가 Old 영역을 분리하여 훑는다.
  * 효율을 위해 앞선 GC에서 Compaction된 영역을 별도로 훑는다.
* CMS 콜렉터 (Concurrent Mark Sweep Collector)
  * Young 영역 GC 방식은 병렬 콜렉터와 같다.
  * Old 영역에서는 다음과 같은 단계를 거친다.
    * Initial Mark
      * 클래스 로더에서 가장 가까운 객체 중에서만 살아있는 객체를 찾는다.
    * Concurrent Mark
      * Initial Mark 단계에서 살아남은 객체의 참조를 따라가며 살아있는 객체를 찾는다.(이 때 여러개의 스레드가 동작한다.)
    * Remark
      * Concurrent Mark를 수행하는 동안 객체의 참조가 끊기거나, 새롭게 생긴 객체가 없는지 다시한번 확인
    * Concurrent Sweep
      * 쓰레기를 정리한다. 별도의 Compaction이 없음에 유의
  * stop-the-world 시간이 매우 짧다
  * 시스템 자원(메모리, CPU)를 더 많이 사용하고, Compaction 단계가 없어 Old영역의 크기가 충분하지 않거나 크기에 비해 조각난 메모리가 많을 경우 오히려 stop-the-world 시간이 늘어날 수 있다.
* G1 콜렉터 (Garbage First Collector)
  * JAVA7에서 새롭게 소개된 GC방식
  * G1 콜렉터 방식에서는 바둑판 모양의 영역이 각각 Eden, Survivor, Old영역의 역할을 동적으로 바꿔가며 GC가 일어난다.
  * Young 영역의 GC와 Old 영역의 GC는 모두 CMS콜렉터 방식과 유사
  * Memory가 4GB 이상에서 사용하는 것이 좋다.
  * Java8 에서는 성능에 이점이 많다

## 참고

* <http://asfirstalways.tistory.com/159>
* <http://heowc.tistory.com/51>