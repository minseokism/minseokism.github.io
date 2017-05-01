---
layout: post
title: Java Data Types
description: "Java Data Type에 대해 기술"
date: 2017-04-04
tags: [java,data type,class,interface,enum]
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
        ㄴ Abstract Class
    ㄴ Interface Type
    ㄴ Array Type
    ㄴ Enum Type
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
        char     ─┘
```
## 3. Reference Types
---
참조형은 기본형을 제외한 나머지 타입으로, null 또는 객체의 주소 (4 byte , OxO-Oxf f f f f f f f)를 저장합니다. java.lang.Object 클래스를 상속받으면 참조형이 됩니다.
  
### 3.1 Class Types
클래스형은 기본형과 다르게 객체를 참조합니다. 
```java
class HearthStone {
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

    public String toSting() {
        return String.valueOf(number);
    }
}
  
public class ClassType {
    public static void main(String[] args) {
        HearthStone a = new HearthStone(6);
        HearthStone b = new HearthStone(4);
        
        System.out.println(a); // "a" result is 6.
        a = b;

        System.out.println(a); // "a" result is 4.
        b.setNumber(9);

        System.out.println(a); // "a" result is 9.
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
  
#### 3.1.2 String Class
String Class는 참조형에 속하지만, 기본형처럼 사용합니다. String Class는 문자열을 저장하기 위해서 문자형 배열 변수(char[]) value를 인스턴스 변수로 정의해놓고 있습니다. 인스턴스 생성 시 생성자의 매개변수로 입력받는 문자열은 이 인스턴스변수(value)에 문자열 배열(char[])로 저장됩니다.

- String은 immutable(불변하는) 객체입니다. [ 참조 : String, StringBuilder, StringBuffer 차이 ] 
- 기본형에서 사용하는 비교 연산자인 `=` 대신 `.equals()` 메소드를 이용해 비교합니다. 
  
#### 3.1.2 Abstract Class
Abstarct Class는 실체 클래스들의 공통적인 특성을 추출해서 선언한 Class 입니다.

- 실체 클라스들의 공통된 필드와 메소드의 이름을 통일할 목적으로 사용합니다.
- 실체 클래스를 작성할 때 시간을 절약 할 수 있습니다.
- 자체적으로 객체 생성이 불가능하며, 참조 변수 타입으로는 가능합니다.

abstract class 작성법 입니다.
```java
public abstract class ClassName {

    // 필드
    // 생성자
    // 메소드

    [public|protected] abstract ReturnType MethodName (parameter, ...) ; // 꼭 선언할 필요는 없습니다.
}
```  
  
### 3.2 Interface Type
Java에서 Interface Type은 객체의 사용 방법을 정의한 Type입니다. 

- interface는 개발코드와 객체가 서로 통신하는 접점 역할을 합니다.
- 개발코드는 객체의 내부구조를 알 필요가 없고, 인터페이스의 메소드만 알면 됩니다.
- 개발코드를 수정하지 않고, 사용하는 객체를 변경할 수 있습니다.
- abstarcat class와 같이 자체적으로 객체 생성이 불가능하며, 참조 변수 타입으로는 가능합니다.
- interface는 interface로부터만 상속받을 수 있으며, class와는 달리 다중상속이 가능합니다.

interface 작성법은 다음과 같습니다.
```java
[public] interface InterfaceName {
    [public static final] Type ConstantName = Value; // 상수
    [public abstract] ReturnType MethodName (parameter, ...) ; // 추상 메소드
    [public] default ReturnType MethodName (parameter, ...) { }// default 메소드
    [public] static ReturnType MethodName (parameter, ...) { } // static 메소드
}
```
  
익명 구현 객체 (일회성 구현 객체를 소스파일로 만들지 않고 만드는 방법)로 선언 할 수 있습니다.
```java
인터페이스명 변수 = new 인터페이스명() {
    // interface에서 선언된 추상 메소드의 실체 메소드를 선언
};
```
  
### 3.3 Array Type
배열형은 기본형으로도 만들 수 있고 참조형으로도 만들 수 있습니다.

```java
public class ArrayTypes {
    public static void main(String[] args) {
        int[] intArray = new int[3];
        double[] doubleArray = new double[4];
        boolean[][] booleanArray = new boolean[4][5];
        Object[] objectArray = null;
        String[] stringArray = new String[10];
    }
}
```
  
### 3.4 Enum Type
자바의 열거형인 Enum은 서로 연관된 상수들의 집합을 뜻합니다. 
- Enum Type 또한 class이기 때문에 생성자를 가질 수 있습니다. 하지만 직접 생성 할 수는 없습니다.
- 키워드 Enum을 사용하게 되면 구현의 의도가 열거임을 분명히 알 수 있습니다.
  
```java
// java 파일로 생성
public enum EnumName {
    ConstantName, ConstantName, ConstantName ...
}

// class 내부에서 선언
public class ClassName {
    private String name;
    enum EnumName { 
        ConstantName, ConstantName, ConstantNamet
    }
    ...
}

// class 외부에서 선언
public enum EnumName { 
    ConstantName, ConstantName, ConstantName
}

public class ClassName {
    private String name;
    ...
}
```
  
---
 [^Literal]: 리터럴(Literal)은 '문자 그대로'라는 뜻을 가지고 있습니다. 리터럴은 어떠한 숫자 또는 기호로서 다른 데이터를 가리키는 역할을 하지 않고 그 자신이 바로 데이터로써 사용되는 것을 이릅니다.