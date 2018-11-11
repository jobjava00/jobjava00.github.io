---
layout: archive
title: "[Java] Primitive 과 Reference Type"
date: 2018-10-19
excerpt: ""
tags: [language, java, basic, Primitive 과 Reference Type]
category: [language/java/basic]
#read_time: true
#share: true

sidebar:
  nav: "language"
---

# 정리

* * *

## Primitive type

| type    | size           | default value | wrapper class |
|---------|----------------|---------------|---------------|
| byte    | 8 bit(1 byte)  | 0             | Byte          |
| short   | 16 bit(2 byte) | 0             | Short         |
| int     | 32 bit(4 byte) | 0             | Int           |
| long    | 64 bit(8 byte) | 0             | Long          |
| float   | 32 bit(4 byte) | 0.0f          | Float         |
| double  | 64 bit(8 byte) | 0.0d          | Double        |
| char    | 16 bit(2 byte) | '\u0000'      | Character     |
| boolean | 1 bit          | false         | Boolean       |

* type 마다 size가 fix
* 기본값이 있으므로 null이 존재하지 않음
* generic을 이용할 때 필요한 wraper class가 존재(Integer, Long..)
* 컴파일 시, 크기를 초과하면 에러가 발생
* primitive type의 변수는 thread의 stack memory에 저장

## Reference Type

* 기본형을 제외한 모든 타입은 Reference Type 이며 java.lang.Object 를 상속
* Class, Interface, Array, Enum Type
* 기본값은 아무런 참조 정보가 없으므로 null을 리턴
* new, Reflection, sun.misc.Unsafe 등으로 객체를 생성
* HotSpot 기준 아무것도 없는 Class도 8Byte를 차지
* boolean type 1개가 존재하는 Class는 16Byte를 차지합니다. (기본 1Byte + 1Byte (boolean 1bit 나머지 padding값)
* 생성된 객체는 Heap Memory에 저장
  * (Java Object Size Calculations in 64-bit)

## String은 무엇인가

* String은 char의 Array
  * Array는 `Reference Type`
* String constant pool을 이용한 메모리 관리

## 참고

* <https://againsee.com/2018/06/15/java-datatype/>