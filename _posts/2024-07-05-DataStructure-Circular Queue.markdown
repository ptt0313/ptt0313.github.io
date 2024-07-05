---
layout: post
title: Circular Queue
category: DataStructure
---

## 원형 큐 자료구조

원형 큐 : 큐의 마지막 요소가 큐의 첫 번째 요소에 연결된 자료구조입니다.   
선형 큐의 비효율적인 메모리 관리때문에 만들어졌습니다.

![원형 큐](https://media.geeksforgeeks.org/wp-content/uploads/Circular-queue.png)

~~~c#
public class CircularQueue<T>
{
    int count;
    int front;
    int rear;
    T error;

    readonly int arraySize;
    T[] array;
    public CircularQueue()
    {
        count = 0;
        arraySize = 5;
        front = arraySize - 1;
        rear = arraySize - 1;
        array = new T[arraySize];
    }
}
~~~

## 원형 큐 멤버 함수 구현

~~~c#
public T Peek()
{
    return array[(front + 1) % arraySize];
}
public int Count()
{
    return count;
}
public void Enqueue(T data)
{
    if (front == (rear + 1) % arraySize)
    {
        Console.WriteLine("Circular Queue is full");
    }
    else
    {
        rear = (rear + 1) % arraySize;
        array[rear] = data;
        count++;
    }
}
public T Dequeue()
{
    if (front != rear)
    {
        front = (front + 1) % arraySize;
        count--;
        return array[front];
    }
    else
    {
        Console.WriteLine("Circular Queue is Empty");
        return default;
    }
}
public int Size()
{
    return (int)MathF.Abs(front - rear);
}
~~~


___
> 참고 자료 : https://www.geeksforgeeks.org/introduction-to-circular-queue/?ref=gcse_ind