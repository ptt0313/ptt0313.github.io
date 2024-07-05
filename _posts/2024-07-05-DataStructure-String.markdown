---
layout: post
title: String
category: DataStructure
---

## 문자열 자료구조

문자열(string)은 문자(character)의 집합체입니다.   
문자열 안에 있는 각 문자를 엑세스하고 싶으면, [Index](square bracket)을 사용하여 문자열에 접근합니다.

~~~c#
public class String
{
    char[] array;
    int eroorCode = -99999;
    public String()
    {
        array = null;
    }
}
~~~

## 문자열 멤버 함수 구현

~~~c#
public void Add(char[] content)
{
    array = new char[content.Length + 1];

    for (int i = 0; i < content.Length; i++)
    {
        array[i] = content[i];
    }

}
public int Size()
{
    return array.Length - 1;
}
public void Concat(char[] content)
{
    char[] newArray = new char[(array.Length - 1) + content.Length + 1];

    for (int i = 0; i < array.Length - 1; i++)
    {
        newArray[i] = array[i];
    }
    for (int i = 0; i < content.Length; i++)
    {
        newArray[i + array.Length - 1] = content[i];
    }
    array = newArray;
}
public void Show()
{
    for (int i = 0; i < array.Length; i++)
    {
        Console.Write(array[i]);
    }
}
public int IndexOf(char alphabet)
{
    for (int i = 0; i < array.Length; i++)
    {
        if (array[i] == alphabet)
        {
            return i;
        }
    }
    return eroorCode;

}
public bool Equals(char[] content)
{
    if (array.Length != content.Length + 1)
    {
        return false;
    }
    else
    {
        for (int i = 0; i < array.Length - 1; i++)
        {
            if (array[i] != content[i])
            {
                return false;
            }
        }
        return true;
    }
}
~~~
