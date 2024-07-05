---
layout: post
title: Delegate
category: c# grammar
---

# 대리자(Delegate)

함수의 주소 값을 저장한 다음 함수를 대신 호출하는 기능입니다.
대리자는 함수의 반환형과 매개 변수의 타입이 일치해야 합니다.
접근지정자 : delegate 반환형 : delegateName

~~~c#
internal class Program
{
    public delegate void Calculator(int x, int y);

    static void Add(int x, int y)
    {
        Console.WriteLine(x + y);
    }
    static void subtraction(int x, int y)
    {
        Console.WriteLine(x - y);
    }
    static void Multiplication(int x, int y)
    {
        Console.WriteLine(x * y);
    }
    static void Devision(int x, int y)
    {
        Console.WriteLine(x / y);
    }
}
Calculator calculator;

calculator = Add;
calculator(10, 20);

calculator = subtraction;
calculator(10, 20);

calculator = Multiplication;
calculator(10, 20);

calculator = Devision;
calculator(20, 10);

~~~

## 델리게이트 체인

하나의 호출자에 여러 개의 함수를 등록해서 사용하는 기법입니다.

~~~c#
Calculator calculator;
calculator = Add;
calculator += subtraction;
calculator += Multiplication;
calculator += Devision;

calculator(5, 5);

calculator -= Devision;

calculator(10, 2);
~~~