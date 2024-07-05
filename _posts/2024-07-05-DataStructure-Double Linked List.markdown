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