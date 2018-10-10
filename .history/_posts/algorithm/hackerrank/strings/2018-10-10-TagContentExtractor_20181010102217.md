---
layout: archive
title: "[Hackerrank] Strings - TagContentExtractor 풀이"
date: 2018-10-10
excerpt: ""
tags: [algorithm, hackerrank, strings, TagContentExtractor]
category: [algorithm/hackerrank/strings]

sidebar:
  nav: "algorithm"
---

# 예문

* * *

https://www.hackerrank.com/challenges/tag-content-extractor/problem

* * *

## 해석

* 태그 내용 추출기

## 풀이

* 정규식 <(.+)>([^<]+)</\\\1> 사용
* * <(.+)> : < 로 시작하는 하나 이상의 문자 그룹
* * ([^<]+) : ^가 아닌 하나 이상의 문자
* * </\\\1> : </ 로 시작하는 앞의 첫번째 그룹 (.+)

## 제약사항

* 1 <= n <= 100

## 코드

``` java
public String solution(String input){
  String regex = "<(.+)>([^<]+)</\\1>";

  boolean matchFound = false;
  Pattern p = Pattern.compile(regex);
  Matcher m = p.matcher(input);
  String output = "";

  while (m.find()) {
    input = m.group(2);
    output += input;
    System.out.println(output);
    matchFound = true;
  }

  if(!matchFound){
    output = "None";
    System.out.println(output);
  }
  return output;
}
```