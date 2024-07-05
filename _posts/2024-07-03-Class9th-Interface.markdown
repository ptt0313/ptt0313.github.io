---
layout: post
title: Interface
category: c#
---

## Interface

인터페이스는 클래스와 비슷하게 메서드,속성,이벤트 등을 갖지만, 이를 직접 구현하지 않습니다.
추상클래스와 비슷한 개념으로 클래스가 인터페이스를 상속받을시 인터페이스의 모든 멤버를 구현해야합니다.

인터페이스는 일반 상속과 다르게 다중 상속이 가능합니다.

~~~c#
public interface IMouse
{
    public void Select();
}
public interface IKeyboard
{
    public void Input();
}
public class Computer : IMouse, IKeyboard
{
    public void Input()
    {
        Console.WriteLine("Keyboard Input");
    }

    public void Select()
    {
        Console.WriteLine("Select Mouse");
    }
}
~~~
