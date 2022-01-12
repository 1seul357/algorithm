#### 문제

1. 쩰리는 오른쪽과 아래로만 이동할 수 있다.
2. 쩰리는 현재 밟고 있는 칸에 적힌 수만큼 한번에 이동할 수 있다.
3. 쩰리가 목적지에 도착할 수 있으면 HaruHaru를, 없으면 Hing을 출력한다.

#### 해결방법

1. visited 방문 체크 리스트를 사용해서 가장 오른쪽, 가장 아래의 값이 1이라면 HaruHaru를 출력한다.
2. 밟고 있는 칸에 적힌 수만큼 이동하기 위해서는 곱하기를 해야한다.

```python
def dfs(x, y):
    dr = [0, 1]
    dc = [1, 0]
    for i in range(2):
        now_dr = x + dr[i] * MAP[x][y]
        now_dc = y + dc[i] * MAP[x][y]
        if 0 <= now_dr < N and 0 <= now_dc < N:
            if visited[now_dr][now_dc] == 0:
                visited[now_dr][now_dc] = 1
                dfs(now_dr, now_dc)


N = int(input())
MAP = [list(map(int, input().split())) for _ in range(N)]
visited = [[0]*N for _ in range(N)]

dfs(0, 0)

if visited[N-1][N-1] == 1:
    print('HaruHaru')
else:
    print('Hing')
```

