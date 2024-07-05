---
layout: post
title: Struct
category: c#
---
## 구조체

여러 개의 변수를 하나의 집합으로 구조화한 다음 하나의 객체를 생성하는 것입니다.
record 그리고 Object와 비슷한 개념입니다.

~~~c#
struct Man {
  char name = 'A';
  int  age;
  char gender = 'M';
};

struct Man man;
~~~

구조체를 선언하기 전에 구조체는 메모리 공간이 생성되지 않음으로,
구조체 내부에 있는 데이터를 초기화할 수 없습니다.