# Search

## Tree

### BFS (Breadth First Search)

Queue로 구현한다.

```
      A
  B       C
D   E   F   G
```

위와 같은 binary tree가 있다고 할 때, BFS 탐색을 하면 다음과 같다.

1. -> A ->
2. -> C B -> A
3. -> E D C -> B A
4. -> G F E D -> C B A
5. -> -> G F E D C B A

## DFS (Depth First Search)

Stack으로 구현한다.

```
      A
  B       C
D   E   F   G
```

위와 같은 binary tree가 있다고 할 때, DFS 탐색을 하면 다음과 같다.

1. A <->
2. C B <-> A
3. C E D <-> B A
4. C <-> E D B A
5. G F <-> C E D B A
6. <-> G F C E D B A
