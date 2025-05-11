---
title: "[CS Fundamentals] DFS and BFS"
seoTitle: "[CS Fundamentals] DFS and BFS"
seoDescription: "In this article, I will introduce the basic concept of Depth-First Search(DFS) and Breadth-First Search(BFS). Both focuses searching, but the difference is "
datePublished: Sun May 11 2025 07:50:37 GMT+0000 (Coordinated Universal Time)
cuid: cmajcttcx000c08l4dmbobws6
slug: cs-fundamentals-dfs-and-bfs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1746937304620/0bfc6fdc-4edc-4475-b491-3405e5c30211.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1746949182143/1dee34eb-deea-4544-bc4c-f919be420b36.png
tags: data-structures, queue, stack, bfs, linkedlists, dfs

---

---

In this article, I will introduce the basic concept of Depth-First Search(DFS) and Breadth-First Search(BFS). Both focuses **searching**, but the difference is the way of doing it.

---

## DFS

To understand DFS, you need to know stack and recursive function. I will explain how they are related to each other as I go through the example below.

Example:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1746945656001/cf2403ed-e1fa-4e0e-b6aa-871ae53180d8.png align="center")

We have a graph above, and let’s say the starting node is `1`, and `1` is connected to `2, 3, 8`. In DFS, we move to the node that holds the smalles value. In this case, it is `2`. Now, `2` is only connected to `7`. `7` is connected to `8` and `6`, but 6 is the smallest, so we move to `6`. Now we have reached the deepest part of the graph. So far, we have a stack that looks like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1746946179036/39e897d7-80b5-49d5-9448-dade98845a81.png align="center")

We can say `stack = [1,2,7,6]` currently. Now we are at `6`, however, the only connected node is `7,` and it is already visited (i.e. searched), so we pop `6` from the stack.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1746946322355/f87ca085-0d07-40e9-9533-7ba69e84cb66.png align="center")

If you keep doing that recursively until all the nodes are visited, DFS ends.

Now, let’s write this in Python:

```python
def dfs(graph, visited, v):
    visited[v] = True
    
    for i in graph[v]:
        if not visited[i]:
            visited[i] = True
            dfs(graph, visited, i)

graph = [
    [],
    [2, 3, 8],
    [1, 7],
    [1, 4, 5],
    [3, 5],
    [3, 4],
    [7],
    [2, 6, 8],
    [1, 7]
]

visited = [False] * 9
dfs(graph, visited, 1)
```

Le’ts have a look at 2D list `graph`. I set the index 0 as an empty list because the smallest value in our graph is `1`, so it is much easier to deal with index if I set index 0 as `[]`. Furthermore, `graph[1] = [2, 3, 8]`. This means that the node `1` is connected to node `2`, `3` and `8`.

Notice that we need to keep track of the nodes that are visited by using visited list. Also, notice th use of recursive function, so we can search until all the nodes are visited.

---

## BFS

BFS is not much different from DFS. It uses queue rather than stack, and it searches nodes widely.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1746948010431/2427a295-51d8-4585-bf8e-f9cefbd10887.png align="center")

Like the previous DFS example, the graph is the same, and the starting node is `1`. We have three nodes that are directly connected to 1, which are `2, 3, 8`. So, I am going to add them to my queue.

`queue = [2, 3, 8]`

We `pop` the left-most element from the queue, and move to that node. It is `2`, so we do the same thing as we did on node `1`. We have two nodes that are directly connected to `2`, which are `1` and `7`. `1` was visited previously, so we add `7` to queue.

`queue = [3,8,7]`

We pop the left-most element from the queue, and do the same thing.

`queue = [8,7,4,5]` and so on..

Let’s write this in Python:

```python
from collections import deque

def bfs(graph, visited, v):
    Q = deque([start])
    visited[v] = True
    
    while Q:
        v = Q.popleft()
        for i in graph[v]:
            if not visited[i]:
                Q.append(i)
                visited[i] = True
                
graph = [
    [],
    [2, 3, 8],
    [1, 7],
    [1, 4, 5],
    [3, 5],
    [3, 4],
    [7],
    [2, 6, 8],
    [1, 7]
]

visited = [False] * 9
dfs(graph, visited, 1)
```