# DFS(Depth First Search)

> 깊이 우선 탐색

DFS는 그래프 혹은 트리를 깊이를 우선으로 탐색하는 비선형적 탐색방법이다.

- stack을 이용하여 비선형적인 탐색을 한다.
- 재귀를 이용한 시스템 stack을 이용해 DFS를 구현할수도 있다.
- stack은 과거에 지나온 곳을 기록하는 곳이라고 할 수 있다.

다음 단계를 반복한다.

1. 시작 노드와 인접한 노드를 순차적으로 탐색한다. 
2. 인접한 노드가 방문기록이 없다면 그 노드를 방문처리한다.
3. 현재 탐색보다 먼저 해당 노드와 인접한 노드를 순차적으로 탐색한다.

### DFS와 백트래킹과의 차이점?

> Prunning(가지치기)

- 어떤 노드에서 출발하는 경로가 해결책으로 이어질 것 같지 않으면 더 이상 그 경로를 따라가지 않음으로써 시도의 횟수를 줄인다. 

- DFS는 모든 경로를 추적하는데 비해 백트래킹은 불필요한 경로를 조기에 차단


# BFS(Breadth First Search)
> 너비 우선 탐색

BFS는 그래피 혹은 트리를 너비를 우선으로 탐색하는 방법이다.
- queue를 사용한다는 특징이 있다. 
- queue는 앞으로 갈 곳을 기록하는 곳이라고 할 수 있다.
- 시작노드를 queue에 삽입하며 시작하며, 다음 단계를 반복한다.

1. queue에서 노드를 꺼낸다.
2. 그 노드에 대한 인접 노드를 순차적으로 탐색한다.
3. 방문기록이 없다면 그 노드를 queue에 삽입하고, 방문처리한다.
4. 탐색이 끝나면, queue가 비워질 때까지 1번부터 반복한다.

# #1260 -  DFS와 BFS


```python
N, m, v = map(int, input().split())


graph = [[] for _ in range(N+1)]
visited = []

c = [False for _ in range(N+1)]
d = [False for _ in range(N+1)]

for _ in range(m):
    p, q = map(int, input().split())
    graph[p].append(q)
    graph[q].append(p)

for nodes in graph:
    nodes.sort()
    
def dfs(n):
    
    if c[n]:
        return
    
    c[n] = True
    print(n)
    
    for node in graph[n]:
        dfs(node)
        

def bfs(n):
    queue = []
    queue.append(n)
    d[n] = True
    while queue:
        x = queue.pop(0)
        print(x)
        for node in graph[x]:
            if not d[node]:
                queue.append(node)
                d[node] = True

#visited.append(v)
dfs(v)
bfs(v)

```

    5 5 3 
    5 4
    5 2
    1 2
    3 4
    3 1
    3
    1
    2
    5
    4
    3
    1
    4
    2
    5

