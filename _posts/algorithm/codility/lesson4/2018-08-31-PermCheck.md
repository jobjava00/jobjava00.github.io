---
layout: archive
title: "PermCheck"
date: 2018-08-31
excerpt: ""
tags: [algorithm, codility, lesson4, Counting Elements]
category: [algorithm/codility/lesson4]

sidebar:
  nav: "algorithm"
---

### 예문 
* * *
A non-empty array A consisting of N integers is given.

A permutation is a sequence containing each element from 1 to N once, and only once.

For example, array A such that:
```
    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
```
is a permutation, but array A such that:
```
    A[0] = 4
    A[1] = 1
    A[2] = 3
```
is not a permutation, because value 2 is missing.

The goal is to check whether array A is a permutation.

Write a function:

class Solution { public int solution(int[] A); }

that, given an array A, returns 1 if array A is a permutation and 0 if it is not.

For example, given array A such that:
```
    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
```
the function should return 1.

Given array A such that:
```
    A[0] = 4
    A[1] = 1
    A[2] = 3
```
the function should return 0.

Write an efficient algorithm for the following assumptions:
```
N is an integer within the range [1..100,000];
each element of array A is an integer within the range [1..1,000,000,000].
```
* * *

### 풀이
* 배열 A : N개의 비어있지 않는 정수로 구성
* 순열 : 1 ~ N 까지 각 요소를 한번만 포함하는 시퀀스
* * 시퀀스이므로 순차적으로 증가 해야 함. 배열 크기 1 은 시퀀스가 아님
* 배열 A가 순열이면 1, 비순열이면 0 리턴하라!

### 제약사항
* N의 범위는 정수 [1..100,000]
* A의 각 요소의 범위는 정수 [1..1,000,000,000]

### 코드
``` java
//인덱스에 따른 체크 배열 사용
public int solution(int[] A) {
    boolean[] checker = new boolean[A.length + 1];
    int num;
    for (int i = 0; i < A.length; i++) {
        num = A[i];
        if (num < checker.length) checker[num] = true;
    }

    for (int i = 1; i < checker.length; i++) {  //A배열의 값을 checker의 인덱스로 활용
        if (false == checker[i]) return 0;
    }
    return 1;
}
```

### 결과
* https://app.codility.com/demo/results/training366M8Z-B4X/?showingAll=1