---
layout: post
title: Linear Queue
category: DataStructure
---

## 선형 큐 자료구조

선형 큐 : 데이터가 FIFO(First In First Out)형식으로 저장되는 자료구조입니다.  
Rear가 배열의 마지막에 도달하면 배열의 빈 부분있어도 더이상 삽입연산을 하지 못합니다.  
이는 메모리의 비효율적인 관리로 이어집니다.

![선형 큐](https://media.geeksforgeeks.org/wp-content/uploads/20220816162225/Queue.png)

~~~c#
class LinearQueue<T>
{
    private T Error;
    int front;
    int rear;
    T[] array;
    readonly int arraySize;
    public LinearQueue()
    {
        front = 0;
        rear = 0;
        arraySize = 5;
        array = new T[arraySize];
    }
}
~~~

## 선형 큐 멤버 함수 구현

~~~c#
public void Enqueue(T data)
{
    if (rear < arraySize)
    {
        array[rear++] = data;
    }
    else
    {
        Console.WriteLine("Linear Queue is Full");
    }
}
public T Dequeue()
{

    if (front != rear)
    {
        T dequeueData = array[front];
        array[front++] = default;
        return dequeueData;
    }
    else
    {
        Console.WriteLine("LinearQueue is Empty");
        return default;
    }
}
public T Peek()
{
    if (front == rear)
    {
        Console.WriteLine("Linear Queue is Empty");
        return Error;
    }
    else
    {
        return array[front];
    }
}
public int Count()
{
    return rear - front;
}
~~~