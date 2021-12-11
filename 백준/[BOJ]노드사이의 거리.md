```python
'''
노드는 1부터 시작하니까 트리의 크기는 (N+1)
visited 리스트 사용해서 거리의 합 저장
visited 리스트는 거리를 알고 싶은 노드의 쌍 입력받을 때 초기화해야 함
아직 방문하지 않은 노드만 탐색
'''

def dfs(now, cnt):
    for i in range(N+1):
        # 노드가 연결되어 있고, 아직 방문하지 않은 노드라면
        if tree[now][i] != 0 and visited[i] == 0:
            if l == i:                                # 만약 노드가 자기 자신이면
                continue                              # 넘어가기
            visited[i] = cnt + tree[now][i]           # 노드 사이의 거리 저장
            dfs(i, cnt+tree[now][i])


N, M = map(int, input().split())
tree = [[0]*(N+1) for _ in range(N+1)]

for i in range(N-1):
    a, b, c = map(int, input().split())       # 트리 상의 연결된 두 점과 거리 입력받기
    tree[a][b] = tree[b][a] = c               # 이차원 리스트 사용

for i in range(M):
    visited = [0] * (N + 1)                   # 방문체크 초기화
    l, k = map(int, input().split())          # 거리를 알고 싶은 노드의 쌍 입력받기
    dfs(l, 0)                                 # dfs 탐색
    print(visited[k])                         # 거리 출력
```

