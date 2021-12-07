```python
def dfs(now, ans):
    global min_sum
    if now == N:
        if min_sum > ans:
            min_sum = ans
        return
    if min_sum < ans:
        return
    for i in range(N):
        if visited[i] == 0:
            visited[i] = 1
            dfs(now+1, ans+arr[now][i])
            visited[i] = 0

T = int(input())
for TC in range(T):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    visited = [0]*N
    min_sum = 9999999
    dfs(0, 0)
    print('#{} {}'.format(TC+1, min_sum))
```

