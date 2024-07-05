---
layout: post
title: Constructor
category: c# grammar
---

## 생성자
클래스의 인스턴스가 생성되는 시점에서 자동으로
호출되는 특수한 멤버 함수입니다.

~~~c#
public class Unit
{
    private int health;
    private string name;
    private int[] attack;
    public Unit(int health, string name)
    {
        this.health = health;
        this.name = name;

        attack = new int[3];
    }
    ...
}
Unit unit1 = new Unit(40, "Marine");
Unit unit2 = new Unit(100, "zealot");
Unit unit3 = new Unit(35, "zuggling");
~~~

생성자의 경우 객체가 생성될 때 단 한 번만 호출되며,
생성자는 반환형이 존재하기 때문에 호출되기 전에는
객체에 대한 메모리가 할당되지 않습니다.

## 복사 생성자

같은 객체를 복사하여 생성시킬 때 호출되는 생성자입니다.

~~~c#
public class Unit
{
    ...
    public void SetData(int value)
    {
        attack[0] = value;
    }
    public void Show()
    {
        Console.WriteLine("health 변수의 값 : " + health);
        Console.WriteLine("name 변수의 값 : " + name);
        for (int i = 0; i < attack.Length; i++)
        {
            Console.WriteLine("attack[ " + i + " ] " + attack[i]);
        }
    }
}
Unit skeleton1 = new Unit(30, "Skeleton");
Unit skeleton2 = new Unit(skeleton1);

skeleton1.SetData(10);
skeleton2.SetData(20);

skeleton1.Show();
skeleton2.Show();
~~~

복사 생성자를 정의하지 않고 객체를 복사하게 되면
기본 복사 생성자가 호출되기 때문에 얕은 복사로 객체가 복사됩니다.
           