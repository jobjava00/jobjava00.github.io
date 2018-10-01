---
layout: archive
title: "[Hackerrank] Strings - Reverse 풀이"
date: 2018-10-01
excerpt: ""
tags: [algorithm, hackerrank, strings, Reverse]
category: [algorithm/hackerrank/strings]

sidebar:
  nav: "algorithm"
---

# 예문

* * *

palindrome

Given a string A, print Yes if it is a palindrome, print No otherwise.

Constraints

A will consist at most 50 lower case english letters.

Sample Input

``` markdown
madam
```

Sample Output

``` markdown
Yes
```

* * *

## 해석

* 팰린드롬 : 앞뒤가 똑같은 문자열
* 문자열 A가 팰린드롬이면 Yes, 아니면 No

## 풀이

* StringBuilder reverse 사용

## 제약사항

* A : 최대 50자의 소문자 영문자로 구성

## 코드

``` java
public class Reverse {
  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);
    String A = sc.next();

    StringBuilder sb = new StringBuilder(A);
    if (A.equals(sb.reverse().toString())) {
      System.out.println("Yes");
    } else {
      System.out.println("No");
    }
  }
}
```