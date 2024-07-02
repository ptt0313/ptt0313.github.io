---
layout: post
title: Arrangement
tags: [c# grammar]
---
## 배열
같은 자료형의 변수들로 이루어진 유한 집합입니다.
배열의 경우 첫 번째 원소는 0부터 시작합니다.

~~~c#
int[] array = new int[5];

array[0] = 10;
array[1] = 20;
array[2] = 30;
array[3] = 40;
array[4] = 50;

for (int i = 0; i < array.Length; i++)
{
    Console.WriteLine("배열 " + i + "의 " + array[i]);
}

foreach (int i in array)
{
    Console.WriteLine(i);
}
~~~
배열의 크기는 생략할 수 있으며, 초기화 목록에서 설정한 요소에 따라 배열의 크기가 결정됩니다.

~~~c#
int[] list = new int[] { 1, 2, 3, 4, 5 };
for (int i = 0; i < list.Length; i++)
{
    Console.WriteLine("배열 " + i + "의 " + list[i]);
}

int[] items = new int[3] { 1, 2, 3 };

for (int i = 0; i < items.Length; i++)
{
    Console.Write("배열 " + i + "의 " + items[i] + "");
}

items = new int[5];

for (int i = 0; i < items.Length; i++)
{
    Console.Write("배열 " + i + "의 " + items[i] + "");
}
~~~

## 문자열

연속적인 메모리 공간에 저장된 문자 변수의 집합입니다.

~~~c#
string name = "Marine";

Console.WriteLine("name 변수의 값 : " + name);
~~~
문자열은 공백도 함께 메모리 공간에 포함하여 코기가 결정되며,
마지막에는 문자열의 끝을 알려주는 제어 문자(NULL 문자)가 추가됩니다.

문자열의 경우 서로 연속적인 메모리 공간으로 연결되어 있지만,
문자 배열 사이에 무효의 문자를 넣게 되면 무효의 문자까지만 문자열을 출력합니다.