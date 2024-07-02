---
layout: post
title: Property
tags: [c# grammar]
---

## 프로퍼티

캡슐화를 통해 보호되고있는 객체에 접속하는 명령어로
get(ter),set(ter) 두가지로 나누어진다.
get은 데이터를 호출,set은 데이터를 초기화한다.

~~~c#
public class Position
{
    private int x;
    private int y;

    public int X
    {
        get
        {
            return x;
        }
        set
        {
            if (value >= 100)
            {
                Console.WriteLine("100이상의 수는 입력되지 않습니다.");
            }
            else
            {
                x = value;
            }
        }
    }
    public int Y
    {
        get { return y; }
        set { y = value; }
    }
}
Position position1 = new Position();
position1.X = 100; // setter
position1.Y = 20; // setter

Console.WriteLine("position1.X : " + position1.X); // getter
Console.WriteLine("position1.Y : " + position1.Y); // getter
~~~