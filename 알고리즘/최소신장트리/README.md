# 상호배타집합

- make-set
- find-set
- union



### 연산의 효율을 높이는 방법

1. Rank를 이용한 Union
   - 원소마다 자신의 높이(rank)를 가지고 있음
2. Path compression



# 최소 신장 트리(MST)



최소 신장 트리를 만드는 알고리즘 두 가지

1.  Prim 알고리즘
   1.  임의의 정점 하나 선택
   2. 선택한 정점과 인접 정점들 중 최소 비용의 간선이 존재하는 정점을 선택
   3. 모든 정점이 선택될 때까지 1, 2 과정을 반복

- pseudo code

```python
MST_PRIM(G, r)             // G : 그래프, r: 시작 정점
	FOR u in G[V]			
    	u.key = INF             // u.key : u에 연결된 가중치 중 최소 가중치
    	u.pi = NULL				// u.pi : 트리에서 u의 부모
    r.key = 0
    Q = [G[v]]                   // 우선순위 Q에 모든 정점을 넣는다
    while Q
    	u <= Extract_MIN(Q)         // 목록 중 key(최소가중치)값이 가장 작은 정점 가져오기
        FOR v in G.Adj[u]          // u의 인접 정점들 중에
        	if v in Q and w(u,v) < v.key  //Q에 있는 v의 key값 갱신
            	v.pi <- u
                v.key <- w(u, v)
```







2. KRUSKAL 알고리즘

- pseudo code

```python
MST_KRUSKAL(G, w)
A <- 0  //공집합
FOR vertex v in G.V:
    Make_Set(v)         // 대표원소 초기화
    
    
G.E에 포함된 간선들을 가중치 w에 의해 정렬

For 가중치가 가장 낮은 간선 (u, v) -> G, E 선택(n-1개)
	if find_set(u) != Find_set(v):        // 같은 집합이 아니라면
        A <- A | {(u, v)}     // 가중치가 가장 낮은 간선을 A에 포함 시켜줌!
        union(u, v)    // v가 속한 집합을 u가 속한 집합에 합쳐줌
     
return A
```

