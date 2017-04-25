---
layout: post
title: Comparable & Comparator
description: "Comparable, Comparator을 이용해서 Collections, Arrays 사용법에 대해서 기술"
date: 2017-04-19
tags: [java,Comparable,Comparator,Arrays,Collections,sort]
comments: true
share: true
---
## Comparable
`public interface Comparable<T>`
- `int compareTo(T o)`를 오버라이딩해서 사용합니다.

```java
public class ComparableTest {

    public static void main(String[] args) {
        Card[] cards = { new Card(5), new Card(4), new Card(9), new Card(1) };

        for (Card card : cards) {
            System.out.print(card); // result is 5 4 9 1
        }

        System.out.println();
        
        Arrays.sort(cards);

        for (Card card : cards) {
            System.out.print(card); // result is 1 4 5 9
        }
    }
}

class Card implements Comparable<Card> {
    private int number;

    public Card(int number) {
        this.number = number;
    }

    public int getNumber() {
        return number;
    }

    @Override
    public int compareTo(Card card) {
        return this.number - card.number;
    }

    @Override
    public String toString() {
        return number + " ";
    }
}
```

## Comparator
`public interface Comparator<T>`
- `int compare(T o1,T o2)`를 오버라이딩해서 사용합니다.
- Comparator interface를 구현한 클래스를 활용하는 방법과, 익명 내부 클래스를 형태로 활용하는 방법이 있습니다.

```java
public class ComparatorTest {

    public static void main(String[] args) {
        Card[] cards = { new Card(5), new Card(4), new Card(9), new Card(1) };

        for (Card card : cards) {
            System.out.print(card); // result is 5 4 9 1
        }

        System.out.println();

        Arrays.sort(cards, new CardComparator()); // Comparator 구현한 클래스 활용

        Arrays.sort(cards, new Comparator<Card>() { // 익명 내부 클래스 활용

        @Override
        public int compare(Card card1, Card card2) {
            return card1.getNumber() - card2.getNumber();
        }

        });

        for (Card card : cards) {
            System.out.print(card); // result is 1 4 5 9
        }
    }
}

class Card {
    private int number;

    public Card(int number) {
        this.number = number;
    }

    public int getNumber() {
        return number;
    }

    @Override
    public String toString() {
        return number + " ";
    }
}

class CardComparator implements Comparator<Card> {
    @Override
    public int compare(Card card1, Card card2) {
        return card1.getNumber() - card2.getNumber();
    }
}

```