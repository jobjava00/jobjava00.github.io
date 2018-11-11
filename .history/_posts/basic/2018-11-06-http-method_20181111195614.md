---
layout: archive
title: "[Basic] Http Method 종류"
date: 2018-11-06
excerpt: ""
tags: [language, java, basic, Http Method 종류]
category: [language/java/basic]
#read_time: true
#share: true

sidebar:
  nav: "main"
---

# 정리

* * *

## Http Method 종류

| HTTP Method | 목적 및 설명                                                                                                                                       |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| GET         | 요청받은 URI의 정보를 받아올 때 사용                                                                                                               |
| HEAD        | GET방식과 동일하지만, 응답에 BODY가 없고 응답코드와 HEAD만 응답 <br/> 웹서버 정보확인, 헬스체크, 버젼확인, 최종 수정일자 확인등의 용도로 사용            |
| POST        | 요청된 자원을 생성(CREATE)한다.                                                                                                                    |
| PUT         | POST와 비슷하지만 기존에 있는 정보를 UPDATE할 때 주로 사용.                                                                                        |
| PATCH       | PUT과 유사하게 요청된 자원을 수정(UPDATE)할 때 사용한다.  <br/> PUT의 경우 자원 전체를 갱신하는 의미지만, PATCH는 해당자원의 일부를 교체하는 의미로 사용 |
| DELETE      | 특정 리소스를 삭제할 때 사용                                                                                                                       |
| CONNECT     | 목적 리소스로 식별되는 서버로의 터널을 맺을 때 사용                                                                                                |
| TRACE       | 목적 리소스의 경로를 볼 때 사용                                                                                                                    |
| OPTIONS     | 웹서버에서 지원되는 메소드의 종류를 확인할 경우 사용.                                                                                              |

### HTTP PUT과 PATCH의 차이

* PUT
  * 해당 자원의 전체를 교체
* PATCH
  * 해당 자원의 일부를 교체

## 참고

* <http://javaplant.tistory.com/18>
* <https://blog.naver.com/dmswjd93/221278886830>