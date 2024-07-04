---
layout: post
title: Operator Overloading
tags: [c# grammar]
---

## 연산자 오버로딩

연산자 오버로딩은 사용자 정의 타입에 연산자를 새롭게 정의 할 수 있도록 해주는 기법입니다.

~~~c#
public class Vector2
{
    private int x;
    private int y;

    public int X
    {
        get { return x; }
        set { x = value; }
    }
    public int Y
    {
        get { return y; }
        set { y = value; }
    }
    static public Vector2 operator +(Vector2 left, Vector2 right)
    {
        Vector2 result = new Vector2();
        result.x = left.X + right.X;
        result.y = left.Y + right.Y;

        return result;
    }
}
Vector2 vector1 = new Vector2();
vector1.X = 10;
vector1.Y = 20;

Vector2 vector2 = new Vector2();
vector2.X = 20;
vector2.Y = 10;

Vector2 vector3 = vector1 + vector2;
~~~
---
## 비교연산자 오버로딩
  
연산자 오버로딩은 사칙연산뿐 아니라 다른 연산자에도 오버로딩이 가능합니다.
1. 동일성 비교
~~~
    == : 두값의 일치여부  
    != : 두 값의 불일치여부
~~~
1. 크기비교
~~~
    <  : 보다작음 비교  
    >  : 보다큼 비교  
    <= : 보다 작거나 같음 비교  
    >= : 보다 크거나 같음 비교
~~~
비교연산자를 오버로딩 할시 반드시 서로 쌍이 되도록 오버로딩 해주어야합니다.
  
~~~c# 
public static bool operator == (
    string a,
    string b
)
public static bool operator != (
    string a,
    string b
)
~~~


___
> 참고 자료 : https://m.mkexdev.net/entry/C-%EA%B8%B0%EC%B4%88%EA%B0%95%EC%A2%8C-14-C-%EC%97%B0%EC%82%B0%EC%9E%90-%EC%98%A4%EB%B2%84%EB%A1%9C%EB%94%A9