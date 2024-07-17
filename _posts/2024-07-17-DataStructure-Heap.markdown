---
layout: post
title: Heap
category: DataStructure
---
# Heap
힙 : 힙 특징을 만족하는 이진 트리 기반 데이터 구조입니다. 즉, 각 노드의 값은 해당 자식 노드의 값보다 크거나 같습니다.
이 속성은 루트 노드에 최대 값 또는 최소값 (힙 유형에 따라 다름)이 포함되고 트리 아래로 이동할 때 값이 감소하거나 증가하는지 확인합니다.

![Heap](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20221220165711/MinHeapAndMaxHeap1.png)

## 힙 멤버 함수 구현

~~~c#
public class Heap
{
    int arraySize;
    int size;
    int[] array;
    public Heap()
    {
        arraySize = 8;
        size = 0;
        array = new int[arraySize];
    }
    public void Insert(int data)
    {
        if (size >= arraySize - 1)
        {
            Console.WriteLine("Heap is Full");
        }
        else
        {
            array[++size] = data;

            int child = size;
            int parent = size / 2;

            while (child > 1)
            {
                if (array[child] > array[parent])
                {
                    Swap(ref array[child], ref array[parent]);
                }
                child = parent;
                parent = child / 2;
            }
        }
    }
    public int Remove()
    {
        if (size <= 0)
        {
            Console.WriteLine("Heap is Empty");
            return -9999;
        }
        int result = array[1];
        array[1] = array[size];
        array[size] = 0;
        size--;
        int parent = 1;

        while (parent * 2 <= size)
        {
            int child = parent * 2;
            if (array[child] < array[child + 1])
            {
                child++;
            }
            if (array[child] < array[parent])
            {
                break;
            }
            Swap(ref array[parent], ref array[child]);

            parent = child;
        }
        return result;

    }
    void Swap(ref int x, ref int y)
    {
        int temporary = x;
        x = y;
        y = temporary;
    }
    public void Show()
    {
        for (int i = 1; i <= size; i++)
        {
            Console.Write(array[i] + " ");
        }
    }
}
~~~


___
> 참고 자료 : https://www.geeksforgeeks.org/heap-data-structure/?ref=gcse_ind