---
layout: archive
title: "[Hackerrank] Strings - DuplicateWords 풀이"
date: 2018-10-04
excerpt: ""
tags: [algorithm, hackerrank, strings, duplicateWords]
category: [algorithm/hackerrank/strings]

sidebar:
  nav: "hackerrank"
---

# 예문

---

<https://www.hackerrank.com/challenges/duplicate-word/problem>

Sample Input

```markdown
5
Goodbye bye bye world world world
Sam went went to to to his business
Reya is is the the best player in eye eye game
in inthe
Hello hello Ab aB
```

Sample Output

```markdown
Goodbye bye world
Sam went to his business
Reya is the best player in eye game
in inthe
Hello Ab
```

---

## 해석

- 중복단어 제거

## 풀이

- 정규식 \b(\w+)(\W+\1\b)+ 사용
  - 공백이 여러개 있을 경우 한번만 나타냄. 단어 경계로 끊음
  - \w : [a-zA-Z0-9]의 줄임 표현
  - \W : [^a-za-z0-9] 영문자와 숫자만 아니면 됨.
  - \b : 단어 경계
  - \1 : 첫번째 괄호(\w+) 그룹과 일치하는 항목
  - \+ : 바로 앞의 문자가 하나 이상

## 제약사항

- 1 <= n <= 100

## 코드

```java
public String solution(String input){
  String regex = "\\b(\\w+)(\\W+\\1\\b)+";
  Pattern p = Pattern.compile(regex, Pattern.CASE_INSENSITIVE);
  Matcher m = p.matcher(input);

  while (m.find()) {
    input = input.replaceAll(m.group(), m.group(1));    //전체 일치 항목 중에 첫번째 일치하는 것으로 바꿔줌
  }

  System.out.println(input);
  return input;
}
```
