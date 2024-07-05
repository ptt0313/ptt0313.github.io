---
layout: post
title: Inheritance
category: c# grammar
---

## 상속

상위 클래스의 속성을 하위 클래스가 사용할 수 있도록 설정해주는 기능입니다.

클래스의 상속 관계에서 상위 클래스는 하위 클래스의 속성을 사용할 수 없으며,
하위 클래스는 상위 클래스의 메모리를 포함한 상태로 메모리의 크기가 결정됩니다.

~~~c#
internal class Unit
{
    protected int health;
    protected int attack;
    protected int defense;
    public Unit()
    {
        Console.WriteLine("Create Unit");
    }

    public void Skill()
    { 
        Console.WriteLine("Unit Skill");
    }
}
~~~

~~~c#
internal class Marine : Unit
{
    private int steamPack;
    public Marine() 
    {
        health  = 40;
        attack  = 5;
        defense = 0;

        steamPack = 5;  

        Console.WriteLine("Create Marine");
    }
    new public void Skill()
    {
        Console.WriteLine("Steam Pack");
    }
    
}

Unit unit = new Unit();

Marine marine = new Marine();
~~~
