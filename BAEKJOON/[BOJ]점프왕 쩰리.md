```python
def dfs(x, y):
    dr = [0, 1]   # 우측과 아래로만 이동
    dc = [1, 0]
    for i in range(2):
        now_dr = x + dr[i] * MAP[x][y]  # 곱해줌으로써 한쪽 방향으로만 이동할 수 있도록 하기
        now_dc = y + dc[i] * MAP[x][y]  # 1 * MAP[x][y] = MAXP[x][y], 0 * MAP[x][y] = 0
        if 0 <= now_dr < N and 0 <= now_dc < N:   # 범위 내에 있고,
            if visited[now_dr][now_dc] == 0:   # 아직 방문 안했으면
                visited[now_dr][now_dc] = 1    # 방문 체크
                dfs(now_dr, now_dc)


N = int(input())
MAP = [list(map(int, input().split())) for _ in range(N)]
visited = [[0]*N for _ in range(N)]    # 방문체크

dfs(0, 0)   # 0, 0에서 출발

if visited[N-1][N-1] == 1:   # 방문했다면
    print('HaruHaru')    
else:                        # 못갔으면
    print('Hing')
```

