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
- 자연스러운 순서로 정렬할 때 사용합니다.

```java
public class ComparableTest {
	public static void main(String[] args) {
		Card[] cards = { new Card(5), new Card(4), new Card(9), new Card(1) };
		
		for (int i = 0 ; i < cards.length ; i++) {
			System.out.print(cards[i].toString() + " ");
		}
		
		System.out.println();
		
		Arrays.sort(cards);
		
		for (int i = 0 ; i < cards.length ; i++) {
			System.out.print(cards[i].toString() + " ");
		}	
	}
}

class Card implements Comparable<Card> {
	  private int number;
	  
	  public Card(int number) {
		  this.number = number;
	  }
	  
	  public int compareTo(Card card) {
		  return this.number - card.number;
	  }
	  
	  public int getNumber() {
		  return number;
	  }
	  
	  @Override
	  public String toString() {
		  return String.valueOf(number);
	  }
}
```