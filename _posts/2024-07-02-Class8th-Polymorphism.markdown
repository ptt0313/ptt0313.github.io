---
layout: post
title: Polymorphism
tags: [c# grammar]
---

## 다형성

여러 개의 서로 다른 객체가 동일한 기능을
서로 다른 방법으로 처리할 수 있는 작업입니다.

다형성은 컴파일 시점에 함수의 속성이 결정되는 정적 바인딩을 하지않고,
실행 시간에 함수와 속성이 결정될 수 있는 동적 바인딩을 가능하게 합니다.

### 함수의 오버로딩

같은 이름의 함수를 매개 변수의 자료형과 매개 변수의 수로
구분하여 여러 개를 선언할 수 있는 기능입니다.

~~~c#
internal class Program
{
    static void Process(int x)
    {
        Console.WriteLine(x + "(int)의 값이 처리되었습니다.");
    }
    static void Process(string x)
    {
        Console.WriteLine(x + "(string)의 값이 처리되었습니다.");
    }

    static void Process(int x, int y)
    {
        Console.WriteLine(x + "(int)" + y + "(int)의 값이 처리되었습니다.");
    }
}
Process(10);
Process("StarCraft");
Process(10, 20);
~~~

함수의 오버로딩의 경우 함수의 매개 변수에 전달하는 인수의
형태를 보고 호출하므로, 반환형으로 함수의 오버로딩은 생성할 수 없습니다.

### 함수의 오버라이딩

상위 클래스에 있는 함수를 하위 클래스에서 재정의하여 사용하는 기능입니다.

~~~c#
internal class Unit
{
    public void Skill()
    { 
        Console.WriteLine("Unit Skill");
    }
}
internal class Marine : Unit
{
    new public void Skill()
    {
        Console.WriteLine("Steam Pack");
    }
}
~~~

함수의 오버라이드는 상속 관계에서만 이루어지며, 하위 클래스에서
함수를 재정의할 때 상위 클래스의 함수 형태와 일치해야 합니다.


### 가상 함수

상속하는 클래스 내에서 같은 형태의 함수로 재정의 될 수 있는 함수입니다.
가상 함수의 경우 가상 함수 테이블을 사용하여 호출되는 함수를 실행 시간에 결정하며,
정적으로 선언된 함수는 가상 함수로 선언할 수 없습니다.

~~~c#
 virtual public void Show()
 {
     Console.WriteLine("Unit Information");

 }
Unit unit = new Marine();

unit.Show();

unit = new Firebet();

unit.Show();

unit = new Ghost();

unit.Show();
~~~

가상 함수 실행 시간은 상위 크래스에 대한 참조로 하위 클래스에 재정의된
함수를 호출할 수 있으며, 접근 지정자는 공개로 설정해야 합니다.
