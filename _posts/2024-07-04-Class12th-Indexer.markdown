---
layout: post
title: Indexer
category: c#
---

# 인덱서

C#에서 인덱서는 객체의 데이터를 배열 형태로 만들어서 인덱스에 엑세스 할수 있게 해줍니다.
배열처럼 []를 사용하여 클래스 내의 특정 데이터에 접근을 가능하게 합니다.

~~~c#
class Bullet
{
    private int[] Damage = new int[10];

    public int this[int index]
    {
        get { return Damage[index]; }
        set { Damage[index] = value; }
    }
}
Bullet bullet = new Bullet();

for (int i = 0; i < 10; i++)
{
    bullet[i] = i + 1;
    Console.WriteLine("bullet [" + i + "]의 값 : " + bullet[i]);
}
~~~
