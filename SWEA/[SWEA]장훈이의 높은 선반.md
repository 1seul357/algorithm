```python
def dfs(now, ans):
    global min_height
    if ans >= B:           # 키가 B이상이고,
        if min_height > ans:   # 최소키보다 ans가 작으면
            min_height = ans   # 갱신
        return
    if now > min_height:   # 가지치기. 가망 없으면 리턴
        return
    for i in range(now, N):
        if visited[i] == 0:    # 중복체크. 아직 안쓴 키면 탐색하기
            visited[i] = 1
            dfs(i, ans + Height[i])
            visited[i] = 0

T = int(input())
for TC in range(T):
    N, B = map(int, input().split())
    Height = list(map(int, input().split()))
    visited = [0]*N
    min_height = 999999
    dfs(0, 0)

    print('#{} {}'.format(TC+1, min_height-B))
```

