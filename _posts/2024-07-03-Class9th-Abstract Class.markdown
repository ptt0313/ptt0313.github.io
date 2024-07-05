---
layout: post
title: Abstract Class
category: c#
---

## 추상 클래스(Abstract Class)

추상 클래스는 추상 함수를 선언한 다음 상속을 통해 하위 클래스에서
함수를 완성하도록 유도하는 클래스입니다.

## 추상클래스 특징
- 추상 클래스는 인스턴스를 할 수 없습니다.
- 오직 자식 클래스에서 상속을 통해서 구현 가능합니다.
- 추상 메소드와 추상 프로퍼티를 가질 수 있습니다.

~~~c#
abstract public class Vehicle
{
    private string name;
    private float speed;

    abstract public void Move();
}
Vehicle vehicle = new Vehicle(); //인스턴스 불가

public class Bicycle : Vehicle
{
    public override void Move() //Vehicle의 Move를 override하여 사용
    {
        Console.WriteLine("Bicycle Move");
    }
}

Bicycle bicycle = new Bicycle(); 

bicycle.Move(); 

~~~