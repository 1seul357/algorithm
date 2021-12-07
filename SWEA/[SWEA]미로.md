```python
def dfs(row, col):  # 현재점
    dr = [-1, 1, 0, 0]
    dc = [0, 0, -1, 1]
    for i in range(4):  # 현재점에서 다음 점으로 이동
        next_row = row + dr[i]
        next_col = col + dc[i]
        if 0 <= next_row < N and 0 <= next_col < N:  # 맵 안에 있을때만 진행
            if MAP[next_row][next_col] == 1:   # 가려는 곳이 벽이면 무시
                continue
            if visited[next_row][next_col] == 1:  # 이미 방문한 곳이면 무시
                continue
            visited[next_row][next_col] = 1    # 방문 표시하기
            dfs(next_row, next_col)


T = int(input())
for TC in range(T):
    ans = 0
    N = int(input())
    MAP = [list(map(int, input().rstrip())) for _ in range(N)]
    visited = [[0] * N for _ in range(N)]

    for row in range(N):
        for col in range(N):
            if MAP[row][col] == 2:   # 2 위치 찾기
                break

    dfs(row, col)      

    for row in range(N):
        for col in range(N):
            # 값이 3이고, 방문한 곳이면 길이 있다는 뜻
            if MAP[row][col] == 3 and visited[row][col] == 1:
                ans = 1
    print('#{} {}'.format(TC + 1, ans))
```

