```python
import sys
sys.setrecursionlimit(3000)

def dfs(x, y):  # 현재 인덱스에서 갈 수 있는 곳(같은 섬)은 모두 방문 체크
    dr = [-1, 1, 0, 0, -1, 1, -1, 1]   # 8방 탐색
    dc = [0, 0, -1, 1, -1, -1, 1, 1]
    for i in range(8):
        now_dr = x + dr[i]
        now_dc = y + dc[i]
        # 범위 안에 있고, 갈 수 있으면(1이면)
        if 0 <= now_dr < h and 0 <= now_dc < w and MAP[now_dr][now_dc] == 1:  
            if visited[now_dr][now_dc] == 0:   # 아직 방문 안했으면
                visited[now_dr][now_dc] = 1    # 방문 체크
                dfs(now_dr, now_dc)


while True:
    w, h = map(int, input().split())
    MAP = [list(map(int, input().split())) for _ in range(h)]
    visited = [[0] * w for _ in range(h)]
    count = 0

    if w == 0 and h == 0:   # w와 h가 0, 0이면 입력 종료
        break

    for i in range(h):
        for j in range(w):
            if MAP[i][j] == 1 and visited[i][j] == 0: # MAP[i][j]가 1이고, 아직 방문 안했으면
                visited[i][j] = 1   # 방문 체크하고,
                dfs(i, j)   # dfs 탐색
                count += 1  # 섬의 개수 + 1

    print(count)
```

