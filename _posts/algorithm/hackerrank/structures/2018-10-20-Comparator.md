---
layout: archive
title: "[Hackerrank] Data Structures - Comparator 풀이"
date: 2018-10-20
excerpt: ""
tags: [algorithm, hackerrank, structures, comparator]
category: [algorithm/hackerrank/structures]

sidebar:
  nav: "hackerrank"
---

# 예문

---

<https://www.hackerrank.com/challenges/java-comparator/problem>

Sample Input

```markdown
5
amy 100
david 100
heraldo 50
aakansha 75
aleksa 150
```

Sample Ouput

```markdown
aleksa 150
amy 100
david 100
aakansha 75
heraldo 50
```

---

## 해석

- Comparator 구현

## 풀이

- Arrays.sort 사용
- 점수가 같을 시 이름으로 compareTo 호출
- 내림차순이므로 2 번째 매개변수 - 1 번째 매개변수 해준다.
  - 음수 or 0 이면 자리 바꾸지 않고 양수이면 자리 바꾸므로...

## 제약사항

## 코드

```java
class Checker implements Comparator<Player> {
    @Override
    public int compare(Player o1, Player o2) {
        if (o1.score == o2.score) {
            return o1.name.compareTo(o2.name);
        } else {
            return o2.score - o1.score;
        }
    }
}

class Player {
    String name;
    int score;

    Player(String name, int score) {
        this.name = name;
        this.score = score;
    }
}

public class ComparatorData {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();

        Player[] player = new Player[n];
        Checker checker = new Checker();

        for (int i = 0; i < n; i++) {
            player[i] = new Player(scan.next(), scan.nextInt());
        }
        scan.close();

        Arrays.sort(player, checker);
        for (int i = 0; i < player.length; i++) {
            System.out.printf("%s %s\n", player[i].name, player[i].score);
        }
    }
}
```
