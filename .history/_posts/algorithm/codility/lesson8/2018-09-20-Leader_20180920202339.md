---
layout: archive
title: "[Codility] Stacks and Queues - StoneWall 풀이"
date: 2018-09-19
excerpt: ""
tags: [algorithm, codility, lesson7, Stacks and Queues]
category: [algorithm/codility/lesson7]

sidebar:
  nav: "algorithm"
---

# 예문

* * *

You are going to build a stone wall. The wall should be straight and N meters long, and its thickness should be constant; however, it should have different heights in different places. The height of the wall is specified by an array H of N positive integers. H[I] is the height of the wall from I to I+1 meters to the right of its left end. In particular, H[0] is the height of the wall's left end and H[N−1] is the height of the wall's right end.

The wall should be built of cuboid stone blocks (that is, all sides of such blocks are rectangular). Your task is to compute the minimum number of blocks needed to build the wall.

Write a function:

class Solution { public int solution(int[] H); }

that, given an array H of N positive integers specifying the height of the wall, returns the minimum number of blocks needed to build it.

For example, given array H containing N = 9 integers:

``` markdown
  H[0] = 8    H[1] = 8    H[2] = 5
  H[3] = 7    H[4] = 9    H[5] = 8
  H[6] = 7    H[7] = 4    H[8] = 8
```

the function should return 7. The figure shows one possible arrangement of seven blocks.

![StoneWall01](/assets/image/algorithm/codility/StoneWall01.png)

Write an efficient algorithm for the following assumptions:

``` markdown
N is an integer within the range [1..100,000];
each element of array H is an integer within the range [1..1,000,000,000].
```

* * *

## 해석

* 돌벽 : N 미터 길이, 두께는 일정
* * 다른 곳에 다른 높이를 가져야 함.
* 배열 H : 돌벽의 높이가 적힌 양의 정수 N으로 구성 됨
* * H[i] : 왼쪽에서 오른쪽으로 i 에서 i + 1까지의 벽의 높이
* * H[0] : 벽의 왼쪽 끝의 높이
* * H[N-1] : 벽의 오른쪽 끝의 높이
* 벽은 직육면체로 지어야 한다.
* 각 블록의 모든 면은 직사각형
* 돌벽을 모두 짓는데 필요한 최소 블록 수를 반환하라.

## 풀이

* 이전 높이 보다 다른 높이여야 한다.
* 이전 높이 보다 높아야 한다.
* Stack에 남아있으면 중첩이 아님.

## 제약사항

* N의 범위는 정수 [0..100,000]
* 배열 H 의 요소의 범위는 [0..1,000,000,000]

## 코드

``` java
import java.util.Stack;
public int solution(String S) {
  Stack<Character> stack = new Stack<>();
  char bracket;

  for (int i = 0; i < S.length(); i++) {
    bracket = S.charAt(i);

    if (stack.isEmpty()) {
      stack.push(bracket);
      continue;
    }

    if ('(' == stack.peek() && ')' == bracket) stack.pop();
    else stack.push(bracket);
  }
  return stack.size() > 0 ? 0 : 1;
}
```

## 결과

* <https://app.codility.com/demo/results/training3G4N84-JDG/?showingAll=1>