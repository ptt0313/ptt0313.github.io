---
layout: post
title: Type Conversion
category: c#
---

## 자료형 변환

서로 다른 자료형을 가지고 있는 변수끼리 연산이 이루어질 때
기존에 지정했던 자료형을 다른 자료형으로 변환하는 과정입니다.

## 암묵적 형변환

서로 다른 자료형으로 연산이 이루어질 때 자료형의 크기가 큰 자료형으로 변환되는 과정입니다.

~~~c#
int integer = 10;
float z = 6.5f;

Console.WriteLine("integer 변수와 z 변수를 + 연산한 결과 : " + (integer + z));
~~~
표현 범위가 작은 데이터에 표현범위가 큰 데이터를 저장하게 되면 암묵적으로 데이터 손실이 발생할 수 있습니다.

~~~c#
float fat = 5.75f;
int weight = fat;
~~~
정수형 에서 실수형으로 암묵적 형변환은 가능하지만, 실수형에서 정수형으로
암묵적 자료형 변환은 불가능합니다.

## 명시적 형변환

연산이 이루어지기 전에 사용자가 직접 자료형을 변환하는 과정입니다.

~~~c#
int health = 10;
int armor = 3;

float rate = (float)health / armor;

Console.WriteLine("rate 변수의 값 : " + rate);
~~~
정수형 변수끼리 연산을 수행하게 되면 정수의 결과 값만 가질 수 있습니다.

## 단락 평가 (short-Circuit Evaluation)

첫 번째 값만으로 결과가 확실할 때 두 번째 값은 확인하지 않고, 실행하는 방법입니다.
~~~c#
int z = 0;

if (10 != 10 && ++z == z)
{
    Console.WriteLine("short-Circuit");
}

Console.WriteLine("z 변수의 값 :" + z);
~~~