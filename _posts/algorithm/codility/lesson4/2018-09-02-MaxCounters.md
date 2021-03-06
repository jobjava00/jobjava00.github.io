---
layout: archive
title: "[Codility] Counting Elements - MaxCounters 풀이"
date: 2018-09-02
excerpt: ""
tags: [algorithm, codility, lesson4, Counting Elements]
category: [algorithm/codility/lesson4]

sidebar:
  nav: "codility"
---

# 예문

* * *

<https://app.codility.com/programmers/lessons/4-counting_elements/max_counters/>

You are given N counters, initially set to 0, and you have two possible operations on them:

increase(X) − counter X is increased by 1,
max counter − all counters are set to the maximum value of any counter.
A non-empty array A of M integers is given. This array represents consecutive operations:

if A[K] = X, such that 1 ≤ X ≤ N, then operation K is increase(X),
if A[K] = N + 1 then operation K is max counter.
For example, given integer N = 5 and array A such that:

``` markdown
    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
```

the values of the counters after each consecutive operation will be:

``` markdown
    (0, 0, 1, 0, 0)
    (0, 0, 1, 1, 0)
    (0, 0, 1, 2, 0)
    (2, 2, 2, 2, 2)
    (3, 2, 2, 2, 2)
    (3, 2, 2, 3, 2)
    (3, 2, 2, 4, 2)
```

The goal is to calculate the value of every counter after all operations.

Write a function:

class Solution { public int[] solution(int N, int[] A); }

that, given an integer N and a non-empty array A consisting of M integers, returns a sequence of integers representing the values of the counters.

Result array should be returned as an array of integers.

For example, given:

``` markdown
    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
```

the function should return [3, 2, 2, 4, 2], as explained above.

Write an efficient algorithm for the following assumptions:

``` markdown
N and M are integers within the range [1..100,000];
each element of array A is an integer within the range [1..N + 1].
```

* * *

## 해석

* N개의 카운터가 주어짐
  * 기본값은 0
* 두가지 명령 가능
  * increase(X) : 카운터 X를 1 증가
  * max counter: 최대 값인 카운터의 값으로 모든 카운터 값 설정
* A : 비어있지 않는 M 개의 정수로 이루어짐
* A[K] = K 일때 1 <= X <= N 이면 증가
* A[K] = N + 1 이면 max counter
* 카운터의 시퀀스 값들을 리턴하라!

## 풀이

* maxCounter 될 때 전체 couters를 업데이트 하지 말고 현재 max를 기록
* 최종 counters 응답 시 maxCounter 보다 작으면 maxCounter로 설정

## 제약사항

* N, M의 범위는 정수 [1..100,000]
* A의 각 요소의 범위는 정수 [1..N + 1]

## 코드

``` java
public int[] solution(int N, int[] A) {
    int[] counter = new int[N];
    int maxCounterNum = 0;
    int num, counterIndex, max = 0;
    for (int i = 0; i < A.length; i++) {
        num = A[i];
        counterIndex = num - 1;
        if (num >= 1 && num <= N) {
            if (maxCounterNum >= counter[counterIndex])
                counter[counterIndex] = maxCounterNum + 1;
            else
                counter[counterIndex] = counter[counterIndex] + 1;
            max = Math.max(max, counter[counterIndex]);
        } else if (num == N + 1)
            maxCounterNum = max;
    }

    for (int i = 0; i < counter.length; i++) {
        if (maxCounterNum > 0 && maxCounterNum > counter[i])
            counter[i] = maxCounterNum;
    }
    return counter;
}
```

## 결과

* <https://app.codility.com/demo/results/trainingVHXYME-K45/?showingAll=1>