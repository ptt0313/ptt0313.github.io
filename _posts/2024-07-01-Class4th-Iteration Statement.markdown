---
layout: post
title: Iteration Statement
category: c# grammar
---

## 반복문

프로그램 내에서 특정한 작업을 반복적으로 수행하는 명령문입니다.

## for문

초기식을 연산하여 조건식의 결과에 따라 특정한 횟수만큼 반복하는 반복문입니다.
~~~c#
for (int i = 0; i < 5; i++)
{
    Console.WriteLine("for Statement");
}

for (int i = 1; i < 6; i++)
{
    Console.WriteLine(i);
}
~~~

for문의 경우 조건이 끝나는 형태와 반대로 초기식을 연산하게 되면
조건이 일치하지 않아 계속 반복적으로 실행되는 문제가 발생할 수 있습니다.

## while문

특정 조건을 만족할 때까지 계속해서 주어진 명령문을 실행하는 반복문
~~~c#
int count = 5;

while (count > 0)
{
    Console.WriteLine("count 변수의 값 : " + count);

    count--;
}
~~~

while문의 경우 위에서 아래로 실행되며, 아래에 있는 명령문의 실행이 다 끝나면
다시 위에 있는 명령문으로 돌아가서 반복하는 구조입니다.

## do-while문

조건과 상관없이 한 번의 작업을 수행한 다음 조건에 따라 명령문을 실행하는 반복문입니다.
~~~c#
int data = 0;

do
{
    Console.Write("Connect");
}
while (data == 1);
~~~

## continue문

해당하는 조건문만 실행하지 않고, 반복문은 이어서 실행하는 제어문입니다.
~~~c#
for (int i = 1; i <= 5; i++)
{
    if (i == 3)
    {
        continue;
    }

    Console.Write(i + " ");
}
~~~