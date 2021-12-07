```python
def bfs(now, cnt):
    global ans
    q.append([now, cnt])
    while len(q) != 0:
        tmp, count = q.pop(0)
        if tmp == e:
            ans = count
            break
        for i in range(N+1):
            if node[tmp][i] == 1:
                q.append([i, count+1])
                
T = int(input())
for TC in range(T):
    N, M = map(int, input().split())
    node = [[0]*(N+1) for _ in range(N+1)]
    q = []
    ans = 0

    for i in range(M):
        x, y = map(int, input().split())
        node[y][x] = node[x][y] = 1

    s, e = map(int, input().split())
    bfs(s, 0)

    print('#{} {}'.format(TC+1, ans))
```

