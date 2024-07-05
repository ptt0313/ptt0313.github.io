---
layout: post
title: Single Linked List
category: Data Structure
---

## 양방향 연결 리스트

양방향 연결 리스트 : 노드라는 구조체에 데이터와 이전 노드와 다음 노드의 포인터를 가지는 자료구조입니다.

![양방향 연결 리스트](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/03/DLL1.png)

~~~c#
public class DoubleLinkedList<T>
{
    Node head;
    Node tail;
    int size;
    public DoubleLinkedList()
    {
        head = null;
        tail = null;
        int size = 0;
    }
    public class Node
    {
        public Node next;
        public Node previous;
        public T data;
    }
}
~~~

## 양방향 연결 리스트 기능

~~~c#

public void PushBack(T data)
{
    Node newNode = new Node();
    if (tail == null)
    {
        head = newNode;
        tail = newNode;
        newNode.data = data;
        newNode.next = null;
        newNode.previous = null;
    }
    else
    {
        tail.next = newNode;
        newNode.previous = tail;

        tail = newNode;

        newNode.data = data;
        newNode.next = null;
    }
    size++;
}
public void RemoveBack()
{
    if (tail == null)
    {
        Console.WriteLine("Linked List is Empty");
    }
    else
    {
        if (head == tail)
        {
            tail = tail.next;
            head = tail;
        }
        else
        {
            tail.previous.next = null;
            tail = tail.previous;
        }
    }
    size--;
}
public void PushFront(T data)
{
    Node newNode = new Node();
    if (head == null)
    {
        newNode.next = null;
        newNode.previous = null;
        newNode.data = data;
        head = newNode;
        tail = newNode;
    }
    else
    {
        head.previous = newNode;
        newNode.next = head;
        head = newNode;
        newNode.data = data;
        newNode.previous = null;
    }
    size++;
}
public void RemoveFront()
{
    if (head == null)
    {
        Console.WriteLine("Linked List is Empty");
    }
    else
    {
        if (head == tail)
        {
            head = null;
            tail = null;
        }
        else
        {
            head.next.previous = null;
            head = head.next;
        }
        size--;
    }
}
public void AddAfter(Node position, T data)
{
    Node previousNode;
    Node nextNode;
    if (position.next == null)
    {
        PushBack(data);
    }
    else if (position.previous == null)
    {
        PushFront(data);
    }
    else
    {
        previousNode = position.previous;
        nextNode = previousNode.next;

        position = new Node();
        position.data = data;

        previousNode.next = position;
        position.previous = previousNode;

        position.next = nextNode;
        nextNode.previous = position;
        size++;
    }
}
public bool Find(T data)
{
    Node currentNode = head;
    for (int i = 0; i < size; i++)
    {
        if (currentNode != null)
        {
            if (currentNode.data.ToString() == data.ToString())
            {
                return true;
            }
            else
            {
                currentNode = currentNode.next;
            }
        }
    }
    return false;
}
public void Remove(T data)
{
    Node currentNode = head;

    if (Find(data) == false)
    {
        Console.WriteLine("No data Exists");
    }
    else
    {
        while (currentNode != null)
        {
            if (currentNode.data.ToString() == data.ToString())
            {
                break;
            }
            else
            {
                currentNode = currentNode.next;
            }
        }
        if (Find(data) == true)
        {
            if (head == tail)
            {
                head = null;
                tail = null;

                size--;
            }
            else if (currentNode.next == null)
            {
                RemoveBack();
            }
            else if (currentNode.previous == null)
            {
                RemoveFront();
            }
            else
            {
                Node previousNode = currentNode.previous;
                Node nextNode = currentNode.next;

                previousNode.next = nextNode;
                nextNode.previous = previousNode;

                size--;
            }
        }

    }
}
public Node First()
{
    return head;
}
public Node Last()
{
    return tail;
}
~~~


___
> 참고 자료 : https://www.geeksforgeeks.org/doubly-linked-list-tutorial/?ref=lbp