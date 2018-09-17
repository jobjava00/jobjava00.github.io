---
layout: archive
title: "[Codility] Sorting - NumberOfDiscIntersections 풀이"
date: 2018-09-11
excerpt: ""
tags: [algorithm, codility, lesson6, NumberOfDiscIntersections]
category: [algorithm/codility/lesson6]

sidebar:
  nav: "algorithm"
---

# 예문

* * *

We draw N discs on a plane. The discs are numbered from 0 to N − 1. An array A of N non-negative integers, specifying the radiuses of the discs, is given. The J-th disc is drawn with its center at (J, 0) and radius A[J].

We say that the J-th disc and K-th disc intersect if J ≠ K and the J-th and K-th discs have at least one common point (assuming that the discs contain their borders).

The figure below shows discs drawn for N = 6 and A as follows:

``` markdown
  A[0] = 1
  A[1] = 5
  A[2] = 2
  A[3] = 1
  A[4] = 4
  A[5] = 0
```

![NumberOfDiscIntersections01](/assets/image/algorithm/codility/NumberOfDiscIntersections01.png)

There are eleven (unordered) pairs of discs that intersect, namely:

discs 1 and 4 intersect, and both intersect with all the other discs;
disc 2 also intersects with discs 0 and 3.
Write a function:

class Solution { public int solution(int[] A); }

that, given an array A describing N discs as explained above, returns the number of (unordered) pairs of intersecting discs. The function should return −1 if the number of intersecting pairs exceeds 10,000,000.

Given array A shown above, the function should return 11, as explained above.

Write an efficient algorithm for the following assumptions:

``` markdown
N is an integer within the range [0..100,000];
each element of array A is an integer within the range [0..2,147,483,647].
```

* * *

## 해석

* N개의 disc가 있다.
* disc : 0 ~ N -1 까지 번호를 가짐
* A : N 개의 양수들로 구성 된 배열
* A[N] : 디스크의 반경
* J번째 디스크의 중심 : (J,0)과 반경 A[J]로 그려짐
* J번째랑 K번째 디스크가 J ≠ K 이면 교차하고 적어도 하나의 공통점을 가진다.
* 배열A개 주어졌을 때 교차하는 디스크의 수를 반환하라!
* * 교차 쌍이 10,000,000을 초과하면 함수는 -1을 반환

## 풀이

* 교차하거나 원을 포함하는 디스크의 개수를 구해야 함.
* * 해당 위치에 도달하는 디스크들의 수
* 현재 J 기준으로 반지름을 구해서 lower, upper 배열에 담는다.
* * lower 배열 : J - A[J]
* * upper 배열: J + A[J]
* 각 배열을 정렬한다.
* upper 보다 작은 lower 들은 반드시 가장 작은 upper 보다 큰 반지름을 갖는다. = 접점
* 다음 upper 에서 겹치지 않게 현재 J 만큼 빼준다.

## 제약사항

* N의 범위는 정수 [0..100,000]
* 배열A의 각 요소의 범위는 정수 [0..2,147,483,647]

## 코드

``` java
import java.util.Arrays;
public int solution(int[] A) {
  int N = A.length;
  long[] lower = new long[N];
  long[] upper = new long[N];

  for (int i = 0; i < N; i++) {
    lower[i] = i - (long) A[i];
    upper[i] = i + (long) A[i];
  }

  Arrays.sort(lower);
  Arrays.sort(upper);

  int intersection = 0;
  int j = 0;

  for (int i = 0; i < N; i++) {
    while (j < N && upper[i] >= lower[j]) {
      intersection += j;
      intersection -= i;
      j++;
    }
  }

  if (intersection > 10000000) return -1;
  return intersection;
}
```

## 결과

* <https://app.codility.com/demo/results/training9RU7BZ-7Z9/?showingAll=1>

## 참고

* <https://github.com/Mickey0521/Codility/blob/master/NumberOfDiscIntersections.java>