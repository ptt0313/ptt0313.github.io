---
layout: post
title: SelectSort
category: Algorithm
---
## 선택정렬

주어진 리스트 중에 최소값을 찾아서 맨 앞에 위치한 결과를 교체하는 방식으로 정렬하는 알고리즘입니다.

시간 복잡도 : 최선,평균,최악 O(n^2)
~~~c#
void Swap(ref int a, ref int b)
        {
            int c;
            c = a;
            a = b;
            b = c;
        }
void Main(string[] args)
{
    int[] array = new int[] { 13, 1, 21, 25, 4 };

    for (int i = 0; i < array.Length; i++)
    {
        int min = array[i];
        int select = i;

        for (int j = i + 1; j < array.Length; j++)
        {
            if (min > array[j])
            {
                min = array[j];
                select = j;
            }
        }
        Swap(ref array[i], ref array[select]);
    }
}
~~~