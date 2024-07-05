---
layout: post
title: Class
category: c# grammar
---
## 클래스

사용자 정의 데이터 유형으로 속성(변수)과 기능(함수)가 포함되어 있으며,
클래스를 통해 객체를 생성하여 접근하고 사용할 수 있는 집합체입니다.

~~~c#
public class GameObject
{

    private int x;
    private int y;
    private int z;

    private double weight;

    public void Information()
    {
        Console.WriteLine("x의 값 : " + x);
        Console.WriteLine("y의 값 : " + y);
        Console.WriteLine("z의 값 : " + z);
    }
}

static void Main(string[] args)
{
GameObject gameObject = new GameObject();

gameObject.Information();
}
~~~

클래스의 경우 클래스 내부에 있는 변수는 클래스의 메모리 영역에 포함되지만,
정적 변수와 함수의 메모리는 클래스 영역에 포함되지 않습니다.

### 지역 변수

선언된 블록(영역) { } 안에서만 사용할 수 있으며,
블록을 벗어나면 메모리에서 사라지는 특징을 가지고 있습니다.

~~~c#
{
    int data = 10;
    GameObject gameObject1 = new GameObject();
}

data = 30;
~~~

### 정적 변수

프로그램이 실행될 때 단 한 번만 초기화가 이루어지며,
프로그램이 실행될 때 메모리에 생성되고, 프로그램이 종료되어야만
메모리에서 사라지는 특징을 가지고 있습니다.

~~~c#
public class Collider
{
    int size = 0;
    static int score = 0;

    public void IncreaseScore()
    {
        score++;

        Console.WriteLine("score 변수의 값 : " + score);
    }
}
Collider collider = new Collider();

collider.IncreaseScore();
collider.IncreaseScore();
~~~