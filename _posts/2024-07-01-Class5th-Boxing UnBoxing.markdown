---
layout: post
title: boxing unboxing
category: c#
---
## 박싱과 언박싱

박싱은 값형식을 참조형식으로 변환하는 과정을 의미하며,
언박싱은 참조형식을 값형식으로 변환하는 과정입니다.

박싱과 언박싱은 스택 메모리와 힙 메모리를 오가고 복제하는 과정에서 낭비되는 메모리가 발생합니다.
MSDN에 의하면 박싱은 참조에 단순 할당(힙에 할당)하는 작업보다 20배 오래 걸리고,
언박싱 시 4배정도 시간이 소요됩니다.

### 박싱

~~~c#
int attack = 10;
object box = attack;

Console.WriteLine("box의 값 : " + box);
~~~

### 언박싱

~~~c#
int result = (int)box;

Console.WriteLine("result의 값 : " + result);

object[] dataList = new object[3];

dataList[0] = 10;       // Attack    
dataList[1] = "Marine"; // Name
dataList[2] = 55.5f;    // Health

Information(dataList);
~~~