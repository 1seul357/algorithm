```python
'''
1) bfs를 통해 같은 구간에 있는 양과 늑대는 모두 체크.
2) bfs 탐색이 끝나면 양과 늑대의 수 비교하고, 늑대의 수가 양의 수보다 같거나 많으면 더하고, 양의 수가 늑대의 수보다 많으면 양의 수 더해줌.
'''

from collections import deque

def bfs(a, b):
    global o_cnt, v_cnt
    dr = [0, 0, -1, 1]
    dc = [-1, 1, 0, 0]
    q.append([a, b])
    while q:                   # q에 값이 있으면 반복
        x, y = q.popleft()
        for i in range(4):
            now_dr = x + dr[i]
            now_dc = y + dc[i]
            if 0 <= now_dr < N and 0 <= now_dc < M:   # 범위를 벗어나는지 체크
                if arr[now_dr][now_dc] == '#':        # 울타리는 못지나가므로
                    continue                          # continue
                if visited[now_dr][now_dc] != 0:      # 이미 방문한 곳이라면
                    continue                          # continue
                visited[now_dr][now_dc] = 1           # 방문 체크하고,
                if arr[now_dr][now_dc] == 'o':        # 양을 만나면
                    o_cnt += 1                        # 양의 수 + 1
                elif arr[now_dr][now_dc] == 'v':      # 늑대 만나면
                    v_cnt += 1                        # 늑대의 수 + 1
                q.append([now_dr, now_dc])            # 다음 위치 q에 저장


N, M = map(int, input().split())
arr = [list(map(str, list(input()))) for _ in range(N)]
q = deque()
visited = [[0]*M for _ in range(N)]       # 방문 체크 리스트
o_ans, v_ans = 0, 0

for row in range(N):
    for col in range(M):
        if visited[row][col] == 0:        # 아직 방문하지 않았다면
            v_cnt, o_cnt = 0, 0           # 양과 늑대의 수 초기화하고, 
            visited[row][col] = 1         # 방문 체크
            bfs(row, col)
            if v_cnt >= o_cnt:            # 늑대의 수가 양의 수보다 많으면
                v_ans += v_cnt            # 늑대의 수만 더하기
            else:                         # 양의 수가 늑대의 수보다 많으면
                o_ans += o_cnt            # 양의 수만 더하기

print(o_ans, v_ans)
```

