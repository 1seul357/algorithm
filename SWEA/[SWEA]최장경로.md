```python
def dfs(now, cnt):
    global max_cnt
    if max_cnt < cnt:          # 최장 경로이면
        max_cnt = cnt          # 저장
    for i in range(1, N+1):
        if visited[i] == 0 and arr[now][i] == 1:  # 중복방문 체크, 경로 있는지 확인
            visited[i] = 1
            dfs(i, cnt+1)
            visited[i] = 0
  
T = int(input())
for TC in range(T):
    N, M = map(int, input().split())
    visited = [0]*(N+1)
    arr = [[0]*(N+1) for _ in range(N+1)]    # 노드 1번부터 N번까지 사용해야 하므로 N+1
    max_cnt = 0
  
    for i in range(M):
        x, y = map(int, input().split())
        arr[y][x] = arr[x][y] = 1            # 무방향이므로  x->y와 y->x 모두 경로가 있음
  
    for i in range(1, N+1):
        visited[i] = 1
        dfs(i, 1)
        visited[i] = 0
  
    print('#{} {}'.format(TC+1, max_cnt))
```

