---
layout: post
title: Dijkstra's algorithm
tags:
  - algorithms
  - graph
---
## Finding the shortest path from a given source to every other vertex 

Given a graph and a source vertex, Dijkstra's algorithm can used to find the shortest path to all vertices from the source vertex. 

## Algorithm
1. Maintain two arrays
  * An array to track visited vertices and initialize its values to 0.
  ```python
  visited = [0] * Number of vertices + 1
  ```
  * An array to track distance and initialize it to infinity (max value).
  ```python
  distance = [1000000] * Number of vertices + 1
  ```
2. Set distance[1] = 0
3. Repeat the following until all vertices are visited:
  * Find j with minimum distance and make sure its not visited previously.
  * Set visited[j] to true.
  * Recompute distance[k] for each neighbor k of j.

## Sample code

  ```python
  # V - number of nodes
  # Adjacency matrix is used

    # variable initialization
    distArray = [1000000] * V
    vistSet = [False] * V    
  
    def minDistance(distArray, vistSet): 
        minimum = 1000000
        for v in range(V): 
            if distArray[v] < minimum and vistSet[v] == False: 
                minimum = distArray[v] 
                min_index = v 
        return min_index

    def dijkstra(srcNode):
        distArray[srcNode] = 0
        for i in range(V): 
            u = minDistance(distArray, vistSet) 
            vistSet[u] = True

            for v in range(V): 
                if graph[u][v] > 0 and vistSet[v] == False and distArray[v] > distArray[u] + graph[u][v]: 
                        distArray[v] = distArray[u] + graph[u][v] 
  
        return distArray
  ```

## References

[NPTEL DAA playlist - youtube](https://youtu.be/gY0MwGLq9W8) \
[section.io](https://www.section.io/engineering-education/dijkstra-python)