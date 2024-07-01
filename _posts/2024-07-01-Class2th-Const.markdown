---
layout: post
title: Const
tags: [c# grammar]
---

## 상수


프로그램이 실행되는 동안 더 이상 변경할 수 없는
메모리 공간입니다.

~~~
const int data = 10;
data = 20;
Console.WriteLine("상수 data의 값 : " + data);
ex)상수 data의 값 : 10
~~~

상수는 메모리 공간을 생성하는 동시에 초기화해야 하며,
한 번 저장된 값을 더 이상 변경할 수 없습니다.

리터럴 상수 = 메모리 공간을 가지지 않음(10, 값 그자체)
심볼릭 상수 = 메모리 공간을 가짐(data, 메모리를 가진 상수 )