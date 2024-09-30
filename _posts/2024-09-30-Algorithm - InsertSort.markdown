---
layout: post
title: InsertSort
category: Algorithm
---
## 삽입정렬

데이터를 하나씩 확인하면서 이미 정렬된 부분과 비교하여 자신의 위치를 찾아 삽입하는 방식으로 정렬하는 알고리즘 입니다.

시간 복잡도 : 최선 O(n) 평균,최악 O(n^2)
~~~c#
int[] array = new int[] { 3, 7, 5, 9, 1 };

int key = 0;
int j = 0;
for (int i = 1; i < array.Length; i++)
{
    key = array[i];

    for (j = i - 1; j >= 0 && array[j] > key; j--)
    {
        array[j + 1] = array[j];
    }

    array[j + 1] = key;
}
~~~