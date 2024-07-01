---
layout: post
title: Quadrant
tags: [c# grammar]
---

## 사분면

조건문과 관계연산자를 이용해 좌표평면을 계산할 수 있습니다.

~~~c#
int x = 10;
int y = 5;

if (x >= 1 && y >= 1)
{
    Console.WriteLine("해당 좌표는 제 1사분면 입니다.");
}
else if (x <= -1 && y >= 1)
{
    Console.WriteLine("해당 좌표는 제 2사분면 입니다.");
}
else if (x <= -1 && y <= -1)
{
    Console.WriteLine("해당 좌표는 제 3사분면 입니다.");
}
else if (x >= 1 && y <= -1)
{
    Console.WriteLine("해당 좌표는 제 4사분면 입니다.");
}
else if (x == 0 && y != 0)
{
    Console.WriteLine("해당 좌표는 y절편 입니다.");
}
else if (x != 0 && y == 0)
{
    Console.WriteLine("해당 좌표는 x절편 입니다.");
}
else if (x == 0 && y == 0)
{
    Console.WriteLine("해당 좌표는 원점입니다.");
}
~~~