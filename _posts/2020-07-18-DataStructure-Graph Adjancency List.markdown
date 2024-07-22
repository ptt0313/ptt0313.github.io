---
layout: post
title: GraphAdjancencyList
category: DataStructure
---
# 그래프 인접 리스트
그래프의 각 정점에 인접한 정점들을 링크드 리스트로 표현하는 방법입니다.

장점 : 그래프의 모든 간선의 수를 O(V+E)로 표현할 수 있습니다.

단점 : 두 정점을 연결하는 간선을 조회하거나 정점의 차수를 알기 위해 정점의 인접 리스트를 모두 탐색해야 하므로, 정적의 차수만큼의 시간이 필요합니다.

![인접 리스트](https://media.geeksforgeeks.org/wp-content/uploads/20230727155209/Graph-Representation-of-Directed-graph-to-Adjacency-List.png)

### 그래프 인접 리스트 구현
~~~c#
public class AdjacencyList<T>
{
    int size; // 정점의 개수
    int arraySize; // 인접 리스트의 크기
    T[] vertex; // 정점의 집합
    Node[] list; // 인접 리스트
    class Node
    {
        public T data;
        public Node next;

        public Node(T data, Node link = null)
        {
            this.data = data;
            next = link;
        }
    }
    public AdjacencyList()
    {
        size = 0;
        arraySize = 10;
        vertex = new T[arraySize];
        list = new Node[arraySize];
    }
    public void Insert(T data)
    {
        if (size >= arraySize)
        {
            Console.WriteLine("Adjacency Overflow");
            return;
        }
        vertex[size++] = data;
    }
    public void Connect(int u, int v)
    {
        if (size <= 0)
        {
            Console.WriteLine("Adjacency List is Empty");
            return;
        }
        if (u >= size || v >= size)
        {
            Console.WriteLine("Index Out of Range");
            return;
        }

        list[u] = new Node(vertex[v], list[u]);
        list[v] = new Node(vertex[u], list[v]);
    }
    public void Show()
    {
        if (size <= 0)
        {
            Console.WriteLine("Adjacency List is Empty");
            return;
        }
        for (int i = 0; i < size; i++)
        {
            Console.Write(vertex[i] + " : ");

            Node currentNode = list[i];
            while (currentNode != null)
            {
                Console.Write(currentNode.data + "  ");

                currentNode = currentNode.next;
            }
            Console.WriteLine();
        }
    }
}

~~~


___
> 참고 자료 : https://www.geeksforgeeks.org/graph-and-its-representations/