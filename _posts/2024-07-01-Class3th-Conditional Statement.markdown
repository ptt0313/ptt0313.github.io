---
layout: post
title: Conditional Statement
tags: [c# grammar]
---

# 조건문

어떤 조건이 주어줄 때 해당 조건에 따라 동작을 수행하도록 실행하는 명령문입니다.

## 관계 연산자

두 개의 피 연산자의 값을 비교하여 그 결과를 0 또는 1이라는 값으로 나타내는 연산자입니다.

~~~c#
bool result1 = 10 > 5;
bool result2 = 10 < 5;
bool result3 = 10 == 5;
bool result4 = 10 != 5;
bool result5 = 10 >= 5;
bool result6 = 10 <= 5;
~~~

관계 연산자는 조건이 맞을 때 1 이라는 값을 반환하며, 조건이 틀릴때 0이라는 값으로 반환합니다.

## if문
어떤 특정한 조건을 비교하여 조건이 맞다면 실행되는 명령문입니다.

~~~c#
int health = 100;

health = 0;

if (health <= 0)
{
    Console.WriteLine("Destroy GameObject");
}
~~~

## else if문
else if문은 if문의 조건이 틀릴 때 else if문의 조건이 맞다면 실행되는 명령문입니다.
else if문은 if문이 존재하며 여러 개를 생성할 수 있습니다.

~~~c#
char key = 'A';

if (key == 'W')
{
    Console.WriteLine("↑");
}
else if (key == 'A')
{
    Console.WriteLine("←");
}
else if (key == 'S')
{
    Console.WriteLine("↓");
}
~~~


## else문
if문과 else if문의 조건이 다 틀리면 실행되는 명령문입니다.
if문에 연결된 모든 조건문의 조건이 맞을 때 가장 위에 있는 조건문만 실행됩니다.

~~~c#
int level = 99;

if (level == 11)
{
    Console.WriteLine("1차 전직");
}
else if (level == 41)
{
    Console.WriteLine("2차 전직");
}
else
{
    Console.WriteLine("전직을 할 수 없습니다.");
}
~~~


## switch문
어떤 결과에 따라 그 결과부터 실행되는 명령문입니다.
switch문의 경우 조건에 해당하는 값에 따라 조건의 위치로 이동합니다.

~~~c#
int state = 0;

switch (state)
{
    // break문
    // 특정한 지점에서 분기를 탈출하는 제어문입니다.
    case 0:
        Console.WriteLine("IDLE");
        break;
    case 1:
        Console.WriteLine("MOVE");
        break;
    case 2:
        Console.WriteLine("ATTACK");
        break;
    case 3:
        Console.WriteLine("DIE");
        break;
    default:
        Console.WriteLine("ERROR");
        break;
}
~~~