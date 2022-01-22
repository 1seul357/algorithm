#### 문제

1. 그래프를 DFS로 탐색한 결과와 BFS로 탐색한 결과를 출력
2. 번호가 작은 순서대로 방문

#### 해결방법

1. DFS와 BFS

#### 주의사항

- 처음에 dfs에서 범위 설정을 now부터 N+1까지 했는데, 출발 노드 번호가 1이 아닐 수 있으므로 0부터 N+1까지로 해야 한다.

```python
def dfs(now):
    visited[now] = 1
    print(now, end=" ")
    for i in range(N+1):                              # 범위는 N까지
        if visited[i] == 0 and node[now][i] == 1:   # 아직 방문 안했고, 노드가 연결되어 있으면
            dfs(i)

def bfs(now):
    visited[now] = 1
    q.append(now)
    while q:                               # q의 길이가 0이 아닌 동안 반복!
        n = q.pop(0)                       # q에서 값을 꺼내고,
        print(n, end=" ")
        for i in range(N+1):               # 범위는 N까지 반복
            if visited[i] == 0 and node[n][i] == 1: # 아직 방문 안했고, 노드가 연결되어 있으면
                visited[i] = 1             # 방문 체크하고,
                q.append(i)                # q에 넣기

N, M, V = map(int, input().split())
node = [[0]*(N+1) for _ in range(N+1)]     # 노드번호는 1부터 N까지
visited = [0]*10000000                     # 방문 체크
q = []

for i in range(M):
    a, b = map(int, input().split())
    node[a][b] = node[b][a] = 1                   # 연결되어 있는 노드 1로 표시하기

dfs(V)                                     # dfs 탐색
visited = [0]*10000000                     # bfs 탐색 시 사용해야 하므로 visited 초기화
print()
bfs(V)                                     # bfs 탐색
```

