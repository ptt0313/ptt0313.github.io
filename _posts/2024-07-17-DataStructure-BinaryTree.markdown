---
layout: post
title: Binary Tree
category: DataStructure
---
# 이진 트리 구조

이진 트리 구조 : 각 노드가 왼쪽 자식과 오른쪽 자식을 가지며 최대 2개의 자식을 갖는 계층적 데이터 구조입니다.   
삽입,삭제,순회 등 다양한 작업을 통해 데이터의 효율적인 저장 및 검색을 위해 컴퓨터 과학에서 일반적으로 사용됩니다.   
이진 트리의 종류로는 완전 이진 트리(complete binary tree) 정 이진 트리(full binary tree) 포화 이진 트리(perfect binary tree)등이 있습니다.

#### 이진 탐색 트리 순회 순서

전위순회: 1-> 2-> 4-> 5-> 3-> 6-> 7   
중위순회: 4-> 2-> 5-> 1-> 6-> 3-> 7   
후위순회: 4-> 5-> 2-> 6-> 7-> 3-> 1   

![BinaryTree](https://media.geeksforgeeks.org/wp-content/cdn-uploads/binary-tree-to-DLL.png)

## 이진 탐색 구조 멤버 함수 구현
~~~c#
public class Node
{
    public int data;

    public Node right;
    public Node left;
}

internal class Program
{
    static Node CreateNode(int data, Node left, Node right)
    {
        Node newNode = new Node();
        newNode.data = data;
        newNode.left = left;
        newNode.right = right;
        return newNode;
    }
    static void Preorder(Node root)
    {
        if (root != null)
        {
            Console.Write(root.data + " ");
            Preorder(root.left);
            Preorder(root.right);
        }
    }
    static void Inorder(Node root)
    {
        if (root != null)
        {
            Inorder(root.left);
            Console.Write(root.data + " ");
            Inorder(root.right);
        }
    }
    static void Postorder(Node root)
    {
        if (root != null)
        {
            Postorder(root.left);
            Postorder(root.right);
            Console.Write(root.data + " ");
        }
    }
}
~~~



___
> 참고 자료 : https://www.geeksforgeeks.org/binary-tree-data-structure/?ref=gcse_ind