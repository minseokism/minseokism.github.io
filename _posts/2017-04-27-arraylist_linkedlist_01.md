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
- 비교할 대상에 직접 구현해서 `int compareTo(T o)`를 오버라이딩해 사용합니다.
- Comparable이 구현된 객체의 `compareTo(T o)` 메소드는 주어진 객체(비교 대상)보다 적으면 **음수**, 주어진 객체보다 같으면 **0**, 주어진 객체보다 크면 **양수**를 리턴하게 됩니다. [오름차순으로 정렬됩니다.] 
- 자연스러운 순서로 정렬할 때 사용합니다.
- Integer, Double, String 모두 Comparable 인터페이스를 구현하고 있습니다.
- `Arrays.sort(T[] arr)`, `Collection.sort(List<T> list)`에 Comparable를 구현한 배열이나, List를 넣으면 정렬이 됩니다.

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
- `int compare(T o1, T o2)`를 오버라이딩해서 사용합니다.
- `compare(T o1, T o2)`의 메소드에서 o1이 o2보다 앞에 오게하려면 **양수**, o1이 o2보다 뒤에 오게 하려면 **음수**, 동등하다면 **0**을 return 하도록 설정해서 사용합니다.
- Comparator interface를 구현한 클래스를 활용하는 방법과, 익명 내부 클래스를 형태로 활용하는 방법이 있습니다.
- 사용자가 직접 정렬 방법을 정하고 싶을 때 사용합니다.
- `Arrays.sort(T[] arr, Comparator<? super<T> c)`, `Collections.sort(List<T> list, Comparator<? super<T> c)`을 사용합니다.

```java
public class ComparatorTest {

    public static void main(String[] args) {
        List<Card> cards = new ArrayList<>();
        cards.add(new Card(5));
        cards.add(new Card(4));
        cards.add(new Card(9));
        cards.add(new Card(1));
        
        for (Card card : cards) {
            System.out.print(card); // result is 5 4 9 1
        }

        System.out.println();

        Collections.sort(cards, new CardComparator());    // 1. Comparator 구현한 클래스 활용

        Collections.sort(cards, new Comparator<Card>() {  // 2. 익명 내부 클래스 활용

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