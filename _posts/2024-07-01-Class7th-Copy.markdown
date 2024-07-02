---
layout: post
title: Copy
tags: [c# grammar]
---

## 얕은 복사

객체를 복사할 때 주소 값을 복사하여 같은 메모리를 
가리키게 하는 복사입니다.

~~~c#
Unit unit1 = new Unit(20, "Slime");
unit1.Show();

Unit unit2 = unit1;
unit2.Show();
~~~

얕은 복사의 경우 같은 객체가 서로 같은 메모리 공간을
참조하고 있기 때문에 하나의 객체로 값을 변경하게 되면
서로 참조된 객체도 함께 영향을 받습니다.

## 깊은 복사

객체를 복사할 때, 참조 값이 아닌 인스턴스 자체를
새로 복사하여 서로 다른 메모리를 생성하는 복사입니다.

~~~c#
Unit slime1 = new Unit(30, "Slime");
Unit slime2 = new Unit(slime1);

slime1.SetData(10);
slime2.SetData(20);

slime1.Show();
slime2.Show();
~~~

# 전체 코드
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

    public Unit(Unit unit)
    {
        health = unit.health;
        name = unit.name;
        attack = new int[3];
    }

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
~~~