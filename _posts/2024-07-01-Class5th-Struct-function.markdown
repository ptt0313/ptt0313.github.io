---
layout: post
title: Function
tags: [c# grammar]
---
## 함수

하나의 특별한 목적의 작업을 수행하기 위해 독립적으로 설계된 코드의 집합입니다.

~~~c#
static int Damage()
{
    int damage = 10;
    return damage;
}
~~~

함수의 경우 자료형과 반환하는 값의 형태가 일치하지 않으면
원하는 값을 얻을 수 없습니다.

## 매개 변수

함수의 정의에서 전달받은 인수를 함수 내부로 전달하기
위해 사용하는 변수입니다.

~~~C#
static int Damage(int a)
{
    int damage = a;
    return damage;
}
Damage(10)
~~~

매개 변수는 함수 내부에서만 연산이 이루어지며, 함수가 종료되면 메모리에서 사라지는 특징을 갖고 있습니다.
