---
layout: post
title: Stack
category: DataStructure
---

## 스택 자료구조

스택 : 데이터가 LIFO(Last In Fist Out)형식으로 저장되는 자료구조입니다.

![스택 자료구조](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20230726165552/Stack-Data-Structure.png)

~~~c#
public class Stack<T>
{
    int top;
    readonly int arraySize;
    T[] array;
    private T error;
    private int count;
    public Stack()
    {
        count = 0;
        top = -1;
        arraySize = 10;
        array = new T[arraySize];
    }
}
~~~

## 스택 멤버 함수 구현

~~~c#
public bool Empty()
{
    if (top == -1)
    {
        Console.WriteLine("Stack is Empty");
        return true;
    }
    return false;
}
public bool Full()
{
    if (top >= arraySize)
    {

        return true;
    }
    return false;
}
public void Push(T data)
{
    if (top >= arraySize - 1)
    {
        Console.WriteLine("Stack Overflow");
    }
    else
    {
        array[++top] = data;

        count++;
    }
}
public T Peek()
{
    return array[top];
}
public T Pop()
{
    if (top <= -1)
    {
        Console.WriteLine("Stack is Empty");
        return error;
    }
    else
    {
        count--;
        return array[top--];
    }
}
public int Count()
{
    return count;
}
public bool Contains(T data)
{
    for (int i = 0; i <= top; i++)
    {
        if (array[i].ToString() == data.ToString())
        {
            return true;
        }
    }
    return false;
}
static bool CheckBracket(string content)
{
    if (content.Length == 0)
    {
        return false;
    }
    Stack<char> stack = new Stack<char>();

    for (int i = 0; i < content.Length; i++)
    {
        char character = content[i];

        if (character == '[' || character == '{' || character == '(')
        {
            stack.Push(character);
        }
        else if (character == ']' || character == '}' || character == ')')
        {
            char bracket = stack.Pop();
            if (bracket == '(' && character != ')')
            {
                return false;
            }
            else if (bracket == '{' && character != '}')
            {
                return false;
            }
            else if (bracket == '[' && character != ']')
            {
                return false;
            }
        }
    }
    if (stack.Count() == 0)
    {
        return true;
    }
    else
    {
        return false;
    }
}
~~~


___
> 참고 자료 : https://www.geeksforgeeks.org/stack-data-structure/?ref=header_search