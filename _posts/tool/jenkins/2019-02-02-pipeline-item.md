---
layout: archive
title: "[Jenkins] pipeline item 생성"
date: 2019-02-02
excerpt: ""
tags: [tool, jenkins, pipeline item 생성]
category: [tool/jenkins]
#read_time: true
#share: true

sidebar:
  nav: "tool"
---

* * *

## pipeline item 생성

![pipeline-item01](/assets/image/tool/jenkins/pipeline-item01.png)
![pipeline-item02](/assets/image/tool/jenkins/pipeline-item02.png)

* Clone : 기존에 생성한 github 계정에 clone 해와서 빌드 시킴
* Build : gradlew 파일에 실행 권한이 없으므로 권한 변경 후 clean build print 실행
  * print task 는 출력용 task 로 미리 github 소스에 정의 해둠 - 아래 참고
* Run
  * 스프링 부트 jar 파일 실행

```js
task print(){
    doLast{
        println "github push complete"
    }
}
```

* 결과 화면

![pipeline-item03](/assets/image/tool/jenkins/pipeline-item03.png)
