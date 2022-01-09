#### 문제

1. F = 건물 최고층, G = 스타트링크 있는 곳, S = 강호의 현재 위치, U = U층을 가는 버튼, D = D층을 가는 버튼
2. 강호가 G층에 도착하기 위해 버튼을 눌러야하는 최소 횟수 출력
3. G층을 갈 수 없다면 use the stairs 출력

#### 해결방법

1. BFS

2. SWEA의 연산과 비슷하게 해결

3. 방문체크를 통해 같은 층에 두번 가지 않게 만들었다.

   > 방문 체크를 해야 G에 도착하지 못하는 경우, q의 무한 반복을 방지할 수 있음

#### 주의사항

- 엘리베이터가 이동할 수 있는 범위는 F층 이하여야 하고, 1층 이상이어야 한다.

  > 1층 이상(tmp-D>=1)인데.... tmp-D >= S (강호의 현재 위치) 로 작성해서 시간 날림....
  >
  > 반례를 아무리 체크해봐도 다 맞는데..??? 했다가 디버깅해보니까 Down 부분이 제대로 계산되지 않는 것을 알았다.



```python
F, S, G, U, D = map(int, input().split())
q = []
cnt = 0
visited = [0]*10000000
q.append([S, cnt])


while q:
    tmp, cnt = q.pop(0)
    if G == tmp:
        ans = cnt
        break
    for i in range(2):
        if i == 0 and tmp+U <= F and visited[tmp+U] == 0:
            visited[tmp+U] = 1
            q.append([tmp+U, cnt+1])
        if i == 1 and tmp-D >= 1 and visited[tmp-D] == 0:
            visited[tmp-D] = 1
            q.append([tmp-D, cnt+1])
    if len(q) == 0:
        print('use the stairs')
        exit(0)

print(ans)
```



