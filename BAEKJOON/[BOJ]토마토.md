#### 문제

1. 토마토가 모두 익었을 경우 최소 일수 구하기
2. 모두 익지 않은 경우에는 -1을 출력

#### 해결방법

1. BFS

2. 1의 값을 가지고 있는 열과 행을 q에 모두 추가한다.

   > bfs 방식이므로 1이 여러 개일 경우, 여러 방향에서 동등하게 토마토를 익힐 수 있음

3. 상하좌우로 한칸씩 이동하면서 토마토가 안익었을 경우(0) + 1 해준다.

   > +1은 일수를 구하기 위한 것

4. 리스트에서 가장 큰 값 = 토마토를 모두 익히는데에 걸리는 일수 

```python
from collections import deque

def bfs():
    dr = [-1, 1, 0, 0]
    dc = [0, 0, -1, 1]
    while q:                                     # 갈 곳이 있는 경우에만 반복
        x, y = q.popleft()
        for i in range(4):
            now_dr = x + dr[i]
            now_dc = y + dc[i]
            if 0 <= now_dr < N and 0 <= now_dc < M:          # 범위를 벗어나지 않는지 체크
                if arr[now_dr][now_dc] == 0:              # 토마토가 있고, 아직 익지 않았다면
                    arr[now_dr][now_dc] = arr[x][y] + 1   # 토마토 익히기 (일 수 +1)
                    q.append([now_dr, now_dc])     # 다음 위치에서 또 탐색해야 하므로 q에 추가


M, N = map(int, input().split())
arr = [list(map(int, input().split())) for _ in range(N)]
q = deque()
ans = 0

for i in range(N):
    for j in range(M):
        if arr[i][j] == 1:               # 익은 토마토라면
            q.append([i, j])             # 해당 인덱스 값을 q에 추가!

bfs()                                    # bfs 탐색

for i in arr:
    for j in i:
        if j == 0:                       # 안익은 토마토가 남아있으면
            print(-1)                    # -1 출력
            exit(0)

    ans = max(ans, max(i))               # 일수 구하기

print(ans-1)                             # 1의 상태에서 시작했으므로 -1
```

