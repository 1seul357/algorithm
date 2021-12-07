```python
'''
문제를 완벽하게 이해하는데 일주일이 걸렸다. 핵심은 0열이 무조건 마지막에 더해져야 한다는 점이다. 그러므로 for i in range(1, N)으로 설정해서 0열은 탐색하지 못하게 해야 하는 것과 마지막에 arr[idx][0]을 더해주는 것이 중요하다.
'''
def dfs(idx, cnt, sum1):
    global ans
    if cnt == N:
        sum1 += arr[idx][0]   # 도착지점(0열) 마지막에 더해주기
        if ans > sum1:        # 최소비용 찾기
            ans = sum1
        return
    if ans < sum1:            # 가지치기. cnt == N이 아닌데, 최솟값을 넘었다면 return
        return
    for i in range(1, N):     # 1~N열까지 탐색
        if visited[i] == 0 and arr[idx][i] != 0:   # 값이 0인 것은 제외한다.
            visited[i] = 1
            dfs(i, cnt+1, sum1 + arr[idx][i])
            visited[i] = 0

T = int(input())
for TC in range(T):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    visited = [0] * N
    ans = 9999999
    dfs(0, 1, 0)
    print('#{} {}'.format(TC+1, ans))
```

