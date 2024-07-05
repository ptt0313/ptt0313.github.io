---
layout: post
title: Vector
category: DataStructure
---

## 벡터 자료구조

벡터 : 배열의 단점을 보완하기 위해 만든 동적 배열 클래스입니다.
배열과 비교하여 데이터의 삽입과 삭제,관리가 효율적입니다.

## 벡터 멤버 함수 구현
~~~c#
class Vector<T>
{
    int size;
    int capacity;
    T[] array;
    public Vector()
    {
        size = 0;
        capacity = 0;
        array = null;
    }
}
public void Resize(int newSize)
{
    capacity = newSize;
    T[] newArray = new T[capacity];
    for (int i = 0; i < size; i++)
    {
        newArray[i] = array[i];
    }
    array = newArray;
}
public void Add(T data)
{
    if (capacity <= 0)
    {
        Resize(1);
    }
    else if (capacity <= size)
    {
        Resize(capacity * 2);
    }
    array[size++] = data;
}
public void RemoveAt(int index)
{
    for (int i = index; i < size - 1; i++)
    {
        array[i] = array[i + 1];
    }
    array[size - 1] = default;
    size--;
}
public void Reserve(int newSize)
{
    if (newSize > capacity)
    {
        Resize(newSize);
    }
    else return;
}
public int Count()
{
    return size;
}
public T this[int index]
{
    get { return array[index]; }
}
~~~
