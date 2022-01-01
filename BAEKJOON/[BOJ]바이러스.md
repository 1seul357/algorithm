```python
# 1번 컴퓨터를 통해 걸리게 되는 웜바이러스 개수
def dfs(now):
    for i in range(N+1):   # N번 컴퓨터까지 탐색
        if visited[i] == 0 and computer[now][i] == 1:  # 컴퓨터끼리 연결되어 있다면
            visited[i] = 1   # 방문 체크
            dfs(i)


N = int(input())
M = int(input())
computer = [[0]*(N+1) for _ in range(N+1)]
visited = [0]*(N+1)
result = 0

for i in range(M):
    x, y = map(int, input().split())
    computer[y][x] = computer[x][y] = 1

dfs(1)      # 1번 컴퓨터에서 출발

for i in range(2, len(visited)):  # 1번 컴퓨터 제외하고 바이러스 개수 세어야 함
    if visited[i] == 1:     # 바이러스 걸려있으면
        result += 1    # + 1

print(result)
```

