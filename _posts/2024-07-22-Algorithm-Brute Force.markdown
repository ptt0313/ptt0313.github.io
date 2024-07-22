---
layout: post
title: Brute Force
category: Algorithm
---
# Brute Force

가능한 모든 경우의 수를 모두 탐색하면서 결과를 도출하는 알고리즘입니다.   
시간 복잡도는 O(2^n)이 걸리며 이론상 모든 경우의 수를 가정하여 정확한 결과를 도출하기 떄문에
암호 해독법으로 많이 쓰입니다.

## Brute Force 코드 구현
~~~c#
int[] array = { 4, 5, 6 };

for (int i = 0; i < 10; i++)
{
    for (int j = 0; j < 10; j++)
    {
        for (int k = 0; k < 10; k++)
        {
            if (array[0] == i && array[1] == j && array[2] == k)
            {
                Console.Write(i);
                Console.Write(j);
                Console.Write(k);
            }
        }
    }
}
~~~
