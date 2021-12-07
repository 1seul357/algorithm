```python
def dfs(idx):
    global count
    if idx == N:
        count += 1
        return
    for i in range(N):
        if visited[i] == 0:
            visited[i] = 1
            dfs(idx+1)
            visited[i] = 0

T = 10
for TC in range(T):
    N = int(input())
    visited = [0]*N
    count = 0

    dfs(0)
    print('#{} {}'.format(TC+1, count))
```

