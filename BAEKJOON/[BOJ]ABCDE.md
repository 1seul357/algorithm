#### 문제

1. A-B, B-C, C-D, D-E, E-F 와 같은 친구 관계 찾기
2. 조건에 맞는 A, B, C, D, E가 존재하면 1을 없으면 0을 출력한다.

#### 해결방법

1. DFS
2. dfs가 4번 연속으로 되면 1 출력, 반복문 종료

#### 주의사항

- 모두가 친구 관계일 필요 없음, 총 5명만 연결되어 있으면 된다.

- 친구 관계 표현할 때, append 형식을 사용해야 시간 초과 발생하지 않는다.

  > N*N 리스트를 사용하면 시간초과 발생

```python
def dfs(now, cnt):
    if cnt == 4:
        print(1)
        exit()
    for F in friend[now]:
        if visited[F] == 0:
            visited[F] = 1
            dfs(F, cnt+1)
            visited[F] = 0

N, M = map(int, input().split())
friend = [[] for i in range(N)]
visited = [0] * N

for i in range(M):
    a, b = map(int, input().split())
    friend[a].append(b)
    friend[b].append(a)

for i in range(N):
    visited[i] = 1
    dfs(i, 0)
    visited[i] = 0

print(0)
```

