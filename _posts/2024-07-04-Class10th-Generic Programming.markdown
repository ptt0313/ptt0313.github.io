---
layout: post
title: Generic Programming
category: c#
---

## 일반화 프로그래밍

특정 데이터 타입에 의존하지 않고, 모든 타입을 멤버 변수의
타입으로 설정할 수 있는 프로그래밍 기법입니다.

c#에서는 제네릭(Generic)으로 사용됩니다.

< T > 형식 매개 변수

~~~c#
public static void Debug<T>(T data)
{
    Console.WriteLine("data 변수의 값 : " + data);
}
Debug('A');
Debug(10);
Debug(20.5f);
Debug(57.85);
Debug("Hello World");
~~~

