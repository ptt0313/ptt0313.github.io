---
layout: post
title: Function
category: c# grammar
---
## 함수

하나의 특별한 목적의 작업을 수행하기 위해 독립적으로 설계된 코드의 집합입니다.

~~~c#
static int Damage()
{
    int damage = 10;
    return damage;
}
~~~

함수의 경우 자료형과 반환하는 값의 형태가 일치하지 않으면
원하는 값을 얻을 수 없습니다.

### 재귀 함수

어떤 함수에서 자신을 다시 호출하여 작업을 수행하는 함수입니다.

~~~c#
static void Start(int count)
{
    if (count <= 0)
    {
        return;
    }
    else
    {
        Start(count - 1);
    }
    Console.WriteLine("Start");
}
Start(3);

Console.WriteLine("Process 함수가 반환하는 값 :" + Process(3));
~~~

재귀 함수는 함수를 계속 호출하기 때문에 스택 영역에 메모리가 계속 쌓이게 되므로
스택 오버플로우가 일어나게 됩니다.

## 매개 변수

함수의 정의에서 전달받은 인수를 함수 내부로 전달하기
위해 사용하는 변수입니다.

~~~c#
static int Damage(int a)
{
    int damage = a;
    return damage;
}
Damage(10)
~~~

매개 변수는 함수 내부에서만 연산이 이루어지며, 함수가 종료되면 메모리에서 사라지는 특징을 갖고 있습니다.

## 인수

함수가 호출될 때 매개 변수에 실제로 전달되는 값입니다.

인수의 경우 함수에 있는 매개변수의 수에 따라 전달할 수 있는
인수의 수가 결정되며, 값을 전달하는 인수와 값을 전달받는
매개변수의 자료형이 서로 일치해야 합니다.

### ref 키워드

변수를 참조형태로 전달하여 메서드 안에서 매개 변수의 값을 변경할 때 사용됩니다.
매개 변수를 전달하기 위해서 반드시 초기화 되어야합니다.

~~~c#
static void Swap(ref int a, ref int b)
{
    int c;
    c = a;
    a = b;
    b = c;
}
int a = 10;
int b = 20;

Console.WriteLine("a : " + a);
Console.WriteLine("b : " + b);

Swap(ref a, ref b);

Console.WriteLine("바뀐 a :" + a);
Console.WriteLine("바뀐 b :" + b);
~~~

### out 키워드

변수를 참조형태로 전달하며 주로 메서드 내에서 전달하는 변수를 초기화할때 사용됩니다.
변수를 전달하기 위해서 변수를 초기화 하지않아도 되지만 전달된 메서드 내에서는 반드시 초기화되어야 합니다.

~~~c#
static void Damage(out int health)
{
    health = 100;
}

int health;

Damage(out health);

Console.WriteLine("health 변수의 값 : " + health);
~~~

### in 키워드

데이터를 읽기 전용으로 사용하는 매개 변수 한정자입니다.

~~~c#
static void Printf(in int value)
{
    Console.WriteLine("value의 값 : " + value);
}

 int data = 300;

 Printf(data);
 ~~~