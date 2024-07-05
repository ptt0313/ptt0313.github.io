---
layout: post
title: HashTable
category: DataStructure
---

## 해쉬 테이블 자료구조

해쉬 테이블은 빠른 접근이 가능한 방식으로 데이터를 효율적으로 저장하고 검색하는 기본적인 데이터 구조입니다.   
해시 함수를 사용하여 해시 테이블의 특정 인덱스에 데이터를 매핑하는 것을 포함하며, 이를 통해 키에 따라 정보를 빠르게 검색할 수 있습니다.

![해쉬 테이블](https://media.geeksforgeeks.org/wp-content/uploads/20200609180838/HashingDataStructure-min.png)

~~~c#
 public class HashTable<KEY, VALUE>
{

    public class Node
    {
        public KEY key;
        public VALUE value;

        public Node next;
    }

    public class Bucket
    {
        public int count;
        public Node head;
    }
    readonly int arraySize;
    Bucket[] bucket;

    public HashTable()
    {
        arraySize = 6;
        bucket = new Bucket[arraySize];

        for (int i = 0; i < arraySize; i++)
        {
            bucket[i] = new Bucket();
        }
    }
}
~~~

## 해쉬 테이블 멤버 함수 구현

~~~c#
int HashFunction(KEY key)
{
    return int.Parse(key.ToString()) % arraySize;
}
Node CreateNode(KEY key, VALUE value)
{
    Node newNode = new Node();
    newNode.key = key;
    newNode.value = value;
    newNode.next = null;
    return newNode;
}
public void Insert(KEY key, VALUE value)
{
    // 해시 함수를 통해서 값을 받는 임시 변수
    int hashIndex = HashFunction(key);

    // 새로운 노드를 생성합니다.

    Node newNode = CreateNode(key, value);

    // 노드가 1개라도 존재하지 않는다면
    if (bucket[hashIndex].count <= 0)
    {
        // 1. bucket[hashIndex]에 head 포인터에 새로운 노드를 저장합니다.
        bucket[hashIndex].head = newNode;

        bucket[hashIndex].count++;
    }
    // 노드가 1개라도 존재한다면
    else if (bucket[hashIndex].count > 0)
    {
        // 1. newNode의 next에 bucket[hashIndex] 의 head 값을 저장합니다.
        newNode.next = bucket[hashIndex].head;

        // 2. bucket[hashIndex].head 를 방금 생성한 노드의 주소를 가리키게 합니다.
        bucket[hashIndex].head = newNode;

        // 3. bucket[hashIndex]의 count 변수의 값을 증가시킵니다.
        bucket[hashIndex].count++;
    }
}
public void Show()
{
    for (int i = 0; i < arraySize; i++)
    {
        Node currentNode = bucket[i].head;

        while (currentNode != null)
        {
            Console.Write("[" + i + "]" + "KEY" + currentNode.key + " VALUE : " + currentNode.value + "");
            currentNode = currentNode.next;
        }
        Console.WriteLine();
    }
}
public void ReMove(KEY key)
{
    // 1. 해시 함수를 통해서 값을 받는 임시 변수
    int hashIndex = HashFunction(key);
    // 2. Node를 탐색 할 수 있는 순회용 포인터를 선언
    Node currentNode = bucket[hashIndex].head;
    // 3. 이전 노드를 저장할 수 있는 포인터 변수 선언 
    Node previousNode = null;
    // 4. currentNode가 null과 같다면 함수를 종료합니다.
    if (currentNode == null)
    {
        Console.WriteLine("HashTable is Empty");
        return;
    }
    // 5. currentNode를 이용해서 내가 찾고자 하는 KEY값을 찾습니다.
    while (currentNode != null)
    {
        if (currentNode.key.ToString() == key.ToString())
        {
            // 내가 삭제하고자 하는 key가 head 노드라면
            if (currentNode == bucket[hashIndex].head)
            {
                bucket[hashIndex].head = currentNode.next;
            }
            else
            {
                previousNode.next = currentNode.next;
            }
            bucket[hashIndex].count--;
            return;
        }
        else
        {
            previousNode = currentNode;
            currentNode = currentNode.next;
        }
    }
    Console.WriteLine("Not Key Found");
}
~~~


___
> 참고 자료 : https://www.geeksforgeeks.org/hashing-data-structure/?ref=header_search