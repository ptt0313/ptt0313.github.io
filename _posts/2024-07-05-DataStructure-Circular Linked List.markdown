---
layout: post
title: Circular Linked List
category: DataStructure
---

## 원형 연결 리스트

원형 연결 리스트 : 모든 노드가 연결되어 원을 형성하는 연결 리스트입니다.
원형 연결 리스트에서는 첫 번째 노드와 마지막 노드가 서로 연결되어 원을 형성합니다.
마지막 노드에 NULL이 없습니다.

![원형 연결 리스트](https://media.geeksforgeeks.org/wp-content/uploads/20240402130347/circular-linked-list-copy.webp)

~~~c#
public class CircularLinkedList<T>
{
    int size;
    Node head;
    public CircularLinkedList()
    {
        head = null;
        size = 0;
    }
    class Node
    {
        public T data;
        public Node next;
    }
}
~~~

## 원형 연결 리스트 기능 구현

~~~c#
public void PushBack(T data)
{
    Node newNode = new Node();
    newNode.data = data;

    if (head == null)
    {
        head = newNode;
        newNode.next = head;
    }
    else
    {
        newNode.next = head.next;
        head.next = newNode;
        head = newNode;
    }
    size++;
}
public void PushFront(T data)
{
    Node newNode = new Node();
    newNode.data = data;
    if (head == null)
    {
        head = newNode;
        newNode.next = head;
    }
    else
    {
        newNode.next = head.next;
        head.next = newNode;
    }
    size++;
}
public void Show()
{
    if (head != null)
    {
        Node currentNode = head.next;
        for (int i = 0; i < size; i++)
        {
            Console.WriteLine(currentNode.data);
            currentNode = currentNode.next;
        }
    }
}
public void RemoveFront()
{
    if (head == null)
    {
        Console.WriteLine("Circular Linked List is Empty");
    }
    else
    {
        if (head == head.next)
        {
            head = null;
        }
        else
        {
            head.next = head.next.next;
        }
        size--;
    }
}
public void RemoveBack()
{
    if (head == null)
    {
        Console.WriteLine("Circular Linked List is Empty");
    }
    else
    {
        if (size == 1)
        {
            head = null;
        }
        else
        {
            Node currentNode = head;
            for (int i = 0; i < size - 1; i++)
            {
                currentNode = currentNode.next;
            }
            currentNode.next = head.next;
            head = currentNode;

        }
        size--;
    }
}
~~~


___
> 참고 자료 : https://www.geeksforgeeks.org/circular-linked-list/?ref=header_search