```python
'''
가장 작은 경로를 찾기 위해 해당 위치에서 상, 하, 좌, 우 탐색을 해야 하므로 BFS로 풀어야 한다. 경로를 탐색하면서 더 적은 비용이라면 CHECK[now_dr][now_dc]를 갱신하면서 MAP을 탐색한다. 계속 적은 값을 갱신하기 때문에 CHECK[N-1][N-1]에는 가장 적은 비용의 경로가 저장되어 있게 된다.
'''
def bfs():     # BFS 탐색
    dr = [-1, 1, 0, 0]
    dc = [0, 0, -1, 1]
    while len(q) != 0:    # q에 값이 있을 때까지 반복
        x, y = q.pop(0)   # 값 꺼내기
        for i in range(4):   # 상, 하, 좌, 우 탐색
            now_dr = x + dr[i]
            now_dc = y + dc[i]
            if 0 <= now_dr < N and 0 <= now_dc < N:   # 다음 경로가 범위 안에 있다면 탐색
                # 현재의 경로가 더 적은 비용이라면
                if CHECK[now_dr][now_dc] > MAP[x][y] + CHECK[x][y]:   
                    CHECK[now_dr][now_dc] = MAP[x][y] + CHECK[x][y]   # 갱신
                    q.append([now_dr, now_dc])   # 탐색할 경로 추가

T = int(input())
for TC in range(T):
    N = int(input())
    MAP = [list(map(int, list(input()))) for _ in range(N)]
    CHECK = [[999999]*N for _ in range(N)]
    CHECK[0][0] = 0   # 출발점은 0
    q = []
    q.append([0, 0])
    bfs()

    print('#{} {}'.format(TC+1, CHECK[N-1][N-1]))    # 도착점 최소 비용 출력
```

