---
layout: archive
title: "OddOccurrencesInArray"
date: 2018-08-29
excerpt: ""
tags: [algorithm, codility, lesson2, arrays]
category: [algorithm/codility/lesson2]

sidebar:
  nav: "algorithm"
---

### 예문 
* * *
A non-empty array A consisting of N integers is given. The array contains an odd number of elements, and each element of the array can be paired with another element that has the same value, except for one element that is left unpaired.

For example, in array A such that:
```
  A[0] = 9  A[1] = 3  A[2] = 9
  A[3] = 3  A[4] = 9  A[5] = 7
  A[6] = 9
```
the elements at indexes 0 and 2 have value 9,
the elements at indexes 1 and 3 have value 3,
the elements at indexes 4 and 6 have value 9,
the element at index 5 has value 7 and is unpaired.
Write a function:

class Solution { public int solution(int[] A); }

that, given an array A consisting of N integers fulfilling the above conditions, returns the value of the unpaired element.

For example, given array A such that:
```
  A[0] = 9  A[1] = 3  A[2] = 9
  A[3] = 3  A[4] = 9  A[5] = 7
  A[6] = 9
```
the function should return 7, as explained in the example above.

Write an efficient algorithm for the following assumptions:
```
N is an odd integer within the range [1..1,000,000];
each element of array A is an integer within the range [1..1,000,000,000];
all but one of the values in A occur an even number of times.
```
* * *

### 풀이
* 배열 A : N개의 정수로 이루어진 비어있지 않는 배열
* 배열은 홀수 개의 요소들로 구성
* 배열의 각 요소는 다른 요소와 같은 값으로 쌍을 이룬다.
* 한개의 요소는 쌍을 이루지 않음.
* 쌍을 이루지 않는 값을 리턴하라!

### 제약사항
* N은 홀수 개이고 범위는 정수 [1..1,000,000]
* 배열 A의 각 요소의 범위는 정수 [1..1,000,000,000]
* A의 값 중 하나를 제외하고 모두 짝수번 발생

### 코드
``` java
//비트 연산 활용 - XOR로 각 요소가 페어하게 발생했는지 체크
public int solution(int[] A) {
    int temp = 0;
    for (int i = 0; i < A.length; ++i) {
        temp = temp ^ A[i];
    }
    return temp;
}
```

### 결과
* https://app.codility.com/demo/results/training9BNNP4-5EB/

### 참고
* http://hojak99.tistory.com/314