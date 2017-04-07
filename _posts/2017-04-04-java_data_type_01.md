---
layout: post
title: Java Data Types
description: "Java Data Type에 대해 기술"
date: 2017-04-04
tags: [java,data type]
comments: true
share: true
---
## 1. Java Data Types 분류
---
자바에는 기본형(Primitive Types)과 참조형(Reference Types)이 있습니다. 일반적인 분류는 다음처럼 가집니다.
```
Java Data Types
ㄴ Primitive Types
    ㄴ Boolean Type(boolean)
    ㄴ Numeric Types
        ㄴ Integral Types
            ㄴ Integer Types(byte, short, int, long)
            ㄴ Floating Point Types(float, double)
        ㄴ Character Type(char)
ㄴ Reference Types
    ㄴ Class Types
        ㄴ Wrapper Class
        ㄴ String Class
    ㄴ Interface Types
    ㄴ Array Types
    ㄴ Enum Types
    ㄴ etc.
ㄴ Null Type
```

## 2. Primitive Types
---
Java에서 지원하는 기본 자료형 유형은 8가지입니다. 
- Java에서 기본 자료형은 반드시 사용하기 전에 선언되어야 합니다.
- 비 객체 타입으로 Null 값을 가질 수 없고, 기본값을 가집니다.


유형은 아래와 같습니다.
```
Type        Bits      Range of Values
-------------------------------------
byte         8bits    -2^7 ~ 2^7-1 (-128 ~ 127)
short       16bits    -2^15 ~ 2^15-1 (-32768 ~ 32767)
int         32bits    -2^31 ~ 2^31-1 (-2147483648 ~ 2147483647)
long        64bits    -2^63 ~ 2^63-1 (-9223372036854775808 ~ 9223372036854775807)
float       32bits    0x0.000002P-126f ~ 0x1.fffffeP+127f
double      64bits    0x0.0000000000001P-1022 ~ 0x1.fffffffffffffP+1023
char        16bits    \u0000 ~ \uffff (0 ~ 2^15-1) unsigned
boolean       1bit    true, false
```
기본값은 아래와 같습니다.
```
Data Type   Default Value (for fields)
--------------------------------------
byte        0
short       0
int         0
long        0L
float       0.0f
double      0.0d
char        '\u0000'
boolean     false
```
### 2.1 Casting (형 변환)
형 변환이란, 변수 또는 리터럴[^Literal]의 타입을 다른 타입으로 변환하는 것입니다.

- boolean을 제외한 나머지 7개의 기본형은 서로 형 변환이 가능합니다.
- 원칙적으로 형 변환 시 캐스트연산자를 이용한 형 변환이 이루어져야 하지만 값의 범위가 작은 쪽에서 큰 쪽으로 형 변환시 값의 손실이 없으므로 생략 가능합니다.

기본형의 자동 형 변환이 가능한 방향은 아래와 같습니다.
```
byte -> short -> int -> long -> float -> double
                  ↑
        char    ─┘
```
## 3. Reference Types
---
참조형은 기본형을 제외한 나머지 타입으로, null 또는 객체의 주소 (4 byte , OxO-Oxf f f f f f f f)를 저장합니다. java.lang.Object 클래스를 상속받으면 참조형이 됩니다.

### 3.1 Class Types
클래스형은 기본형과 다르게 객체를 참조합니다. 
```java
class HearthStone{
    private int number;
    HearthStone(int numuber) {
        this.number = number;
    }
    public int getNumber() {
        return number;
    }
    public void setNumber(int number) {
        this.number = number;
    }
}
public class ClassType {
    public static void main(String[] args) {
        HearthStone a = new HearthStone(6);
        HearthStone b = new HearthStone(4);
        System.out.println(a.getNumber()); // "a" result is 6.
        a = b;
        System.out.println(a.getNumber()); // "a" result is 4.
        b.setNumber(9);
        System.out.println(a.getNumber()); // "a" result is 9.
    }
}
```
b 객체의 멤버 변수 값을 바꿨지만, a 객체도 같은 객체를 참조하기 때문에 같은 값을 출력하는 것을 볼 수 있습니다. **참조형은 실제 객체를 가지고 있는 게 아니라 객체의 주소를 가지고 있으므로** 이러한 결과가 나온 것을 알 수 있습니다.

#### 3.1.1 Wrapper Class
기본형 변수도 때로는 객체로 다루어져야 하는 경우가 있습니다. 예를 들면, 매개변수로 객체를 요구할 때, 기본형 값이 아닌 객체로 저장해야 할 때, 객체 간의 비교가 필요할 때 등등의 경우에는 기본형 값들을 객체로 변환해서 사용해야 합니다. 이때 사용되는 것이 Wrapper Class입니다.

```
기본형   대응 래퍼 클래스
byte     Byte
short    Short
int      Integer
long     Long
float    Float
double   Double
char     Char
boolean  Boolean
```

#### 3.1.1 String Class
String Class는 참조형에 속하지만, 기본형처럼 사용합니다. String Class는 문자열을 저장하기 위해서 문자형 배열 변수(char[]) value를 인스턴스 변수로 정의해놓고 있습니다. 인스턴스 생성 시 생성자의 매개변수로 입력받는 문자열은 이 인스턴스변수(value)에 문자열 배열(char[])로 저장됩니다.

- String은 immutable(불변하는) 객체입니다. [ 참조 : String, StringBuilder, StringBuffer 차이 ] 
- 기본형에서 사용하는 비교 연산자인 `=` 대신 `.equals()` 메소드를 이용해 비교합니다. 

### 3.2 Interface Types
[참조]
### 3.3 Array Types
배열형은 기본형으로도 만들 수 있고 참조형으로도 만들 수 있습니다.

```java
public class ArrayTypes{
    public static void main(String[] args) {
        int[] intArray = new int[3];
        double[] doubleArray = new double[4];
        boolean[][] booleanArray = new boolean[4][5];
        Object[] objectArray = null;
        String[] stringArray = new String[10];
    }
}
```
### 3.4 Enum Types
[참조]

---
 [^Literal]: 리터럴(Literal)은 '문자 그대로'라는 뜻을 가지고 있습니다. 리터럴은 어떠한 숫자 또는 기호로서 다른 데이터를 가리키는 역할을 하지 않고 그 자신이 바로 데이터로써 사용되는 것을 이릅니다.