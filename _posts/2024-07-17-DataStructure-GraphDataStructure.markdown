---
layout: post
title: Graph Adjacency Matrix
category: DataStructure
---
# 그래프 인접 행렬

요소들이 서로 복잡하게 연결되어 있는 관계를 표현하는 자료구조입니다.   
정점과 간선들의 집합으로 구성되어 있습니다.    
   
정점(vertex) : 노드(Node) 데이터가 저장되는 그래프의 기본 원소입니다.   
간선(edge) : 노드들을 연결하는 선입니다.   
인접 정점(Adjacent Vertex) : 간선으로 직접 연결된 정접을 의미합니다.   
차수(Degree) : 정점에 연결된 간선의 수를 의미합니다.   
경로(Path) : 정점들을 연결하는 간선들의 순서입니다.
트리와 그래프의 차이: 그래프는 자기 자신을 가리키는 '사이클'이 존재합니다.

### 그래프의 종류

* 무방향 그래프 : 간선에 방향이 없는 그래프입니다. 특징: 대칭 행렬

![무방향그래프](https://media.geeksforgeeks.org/wp-content/uploads/20230727130331/Undirected_to_Adjacency_matrix.png)    

* 방향 그래프 : 진입차수(자신에 들어오는 차수의 갯수), 진출차수(다른 정점을 향하는 차수의 갯수), 특징: 비대칭 행렬

![방향 그래프](https://media.geeksforgeeks.org/wp-content/uploads/20230727130528/Directed_to_Adjacency_matrix.png)    

* 가중치 그래프 : 간선에 가중치가 있는 그래프입니다.

![가중치 그래프](https://media.geeksforgeeks.org/wp-content/uploads/20220519165117/weightedgraph.png)    


___
> 참고 자료 : https://www.geeksforgeeks.org/