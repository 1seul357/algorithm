```python
'''
백트래킹. 소수점은 곱할 수록 값이 작아지기 때문에 max_P보다 값이 작으면 가지치기해야 한다. 가지치기 안하면 시간초과 발생. 
'''
def dfs(idx, ans):
    global max_P
    if idx == N:
        if max_P < ans:
            max_P = ans
        return
    if max_P > ans:    # 가지치기. 일의 효율이 max_P보다 작으면 탐색 중지.
        return
    for i in range(N):
        if visited[i] == 0 and work[idx][i] != 0:
            visited[i] = 1
            dfs(idx+1, (ans * work[idx][i]) / 100)
            visited[i] = 0


T = int(input())
for TC in range(T):
    N = int(input())
    work = [list(map(int, input().split())) for _ in range(N)]
    visited = [0]*N
    max_P = 0

    dfs(0, 1)
    print('#{} {:6f}'.format(TC+1, max_P*100))   # 소수점 6자리까지 출력
```

