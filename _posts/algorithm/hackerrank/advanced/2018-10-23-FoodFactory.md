---
layout: archive
title: "[Hackerrank] Data Structures - Comparator 풀이"
date: 2018-10-20
excerpt: ""
tags: [algorithm, hackerrank, structures, Comparator]
category: [algorithm/hackerrank/structures]

sidebar:
  nav: "hackerrank"
---

# 예문

---

<https://www.hackerrank.com/challenges/java-factory/problem>

Sample Input

```markdown
cake
```

Sample Ouput

```markdown
The factory returned class Cake
Someone ordered a Dessert!
```

---

## 해석

- FactoryPattern 구현

## 풀이

- Factory 에서 문자열 비교로 생성
- Enum으로 관리 하는 방법도 있음

## 제약사항

## 코드

```java
interface Food {
    String getType();
}

class Pizza implements Food {
    public String getType() {
        return "Someone ordered a Fast Food!";
    }
}

class Cake implements Food {
    public String getType() {
        return "Someone ordered a Dessert!";
    }
}

class FoodFactory {
    public Food getFood(String order) {
        if ("pizza".equals(order))
            return new Pizza();
        else if ("cake".equals(order))
            return new Cake();
        else
            return null;
    }
}
```
