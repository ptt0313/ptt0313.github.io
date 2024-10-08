---
layout: post
title: Single Linked List
category: DataStructure
---

## 단일 연결 리스트

단일 연결 리스트 : 노드라는 구조체에 데이터와 다음 노드의 포인터를 가지는 자료구조입니다.   
마지막 노드의 다음 노드를 가리키는 포인터는 NULL이 됩니다.

![단일 연결 리스트](https://media.geeksforgeeks.org/wp-content/uploads/20240219155344/Singly-Linked-List.webp)

~~~c#

public class SingleLinkedList<T>
{
    Node head;
    int size;
    public SingleLinkedList()
    {
        Node head = null;
        int size = 0;
    }
    public class Node
    {
        public T data;
        public Node next;
    }
}

~~~

## 단일 연결 리스트 멤버 함수 수현

### 1. PushFront

~~~c#

public void PushFront(T data)
{
    if (head == null)
    {
        head = new Node();

        head.data = data;
        head.next = null;
    }
    else if (head != null)
    {
        Node newNode = new Node();

        newNode.data = data;
        newNode.next = head;

        head = newNode;
    }
    size++;
}
~~~
### 2. PushBack

~~~c#

public void PushBack(T data)
{
    if (head == null)
    {
        head = new Node();

        head.data = data;
        head.next = null;
    }
    else
    {
        Node currentNode = head;
        Node newNode = new Node();

        if (currentNode.next == null)
        {
            newNode.data = data;
            currentNode.next = newNode;
        }
        else
        {
            while (currentNode.next != null)
            {
                currentNode = currentNode.next;
            }

            newNode.data = data;
            currentNode.next = newNode;
        }
    }
    size++;
}
~~~
### 3. RemoveFront

~~~c#

public void RemoveFront()
{
    if (head != null)
    {
        head = head.next;
        size--;
    }
    else if (head == null)
    {
        Console.WriteLine("Linked List is Empty");
    }
}
~~~
### 4. RemoveBack

~~~c#

public void RemoveBack()
{
    if (head == null)
    {
        Console.WriteLine("Linked List is Empty");
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
            Node previousNode = currentNode;
            while (currentNode.next != null)
            {
                previousNode = currentNode;
                currentNode = currentNode.next;
            }
            previousNode.next = currentNode.next;
        }
        size--;
    }
}
~~~

___
> 참고 자료 : (https://www.geeksforgeeks.org/introduction-to-singly-linked-list/?ref=gcse_ind)