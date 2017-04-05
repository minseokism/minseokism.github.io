---
layout: post
title: Java Data Types
description: "Java Data Type에 기술"
date: 2017-04-04
tags: [java,data type]
comments: true
share: true
---
## 1. Java Data Types 분류

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
    ㄴ Class Type
    ㄴ Interface Types
    ㄴ Array Types
    ㄴ Enum Types
    ㄴ String Type
    ㄴ etc.
ㄴ Null Type
```

## 2. Primitive Types
Java에서 지원하는 기본 자료형 유형은 8가지 입니다. 
- Java에서 기본 자료형은 반드시 사용하기 전에 선언되어야 합니다.
- 비객체 타입으로 Null 값을 가질 수 없고, 기본값을 가집니다.


유형은 아래와 같습니다.
```
Type        Bits      Range of Values
---------------------------------------------------------------------------------------
byte         8bits    -2^7 ~ 2^7-1 (-128 ~ 127)
short       16bits    -2^15 ~ 2^15-1 (-32768 ~ 32767)
int         32bits    -2^31 ~ 2^31-1 (-2147483648 ~ 2147483647)
long        64bits    -2^63 ~ 2^63-1 (-9223372036854775808 ~ 9223372036854775807)
float       32bits    0x0.000002P-126f ~ 0x1.fffffeP+127f
double      64bits    0x0.0000000000001P-1022 ~ 0x1.fffffffffffffP+1023
char        16bits    \u0000 ~ \uffff (0 ~ 2^15-1) unsgined
boolean      1bit     true, false
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