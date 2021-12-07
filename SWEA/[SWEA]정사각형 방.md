```python
'''
가지치기 없이도 풀 수 있는 문제. 가장 어려웠던 부분은 cnt와 최댓값이 같을 경우 작은 방 번호를 저장해줘야하는데, 이 부분을 구현하는 것이었다. 그냥 메인메서드에서 방 번호를 tmp로 저장한 후에, dfs로 같이 호출했다. 주의할 점은 cnt가 큰 경우에는 무조건 min_room을 갱신해야 하고, cnt가 같은 경우에는 min_room 번호를 비교한 후에 갱신해야 한다. 두번째 부분은 구현했는데, 첫번째 부분에서 min_room = temp를 안써서 계속 답이 이상하게 나왔다. cnt가 최댓값보다 큰 경우에는 방 번호 비교 없이 바로 값을 갱신해야 한다.
'''
def dfs(i, j, cnt, temp):
    global max_cnt, min_room
    if max_cnt < cnt:
        max_cnt = cnt
        min_room = temp
    elif max_cnt == cnt and min_room > temp:
        min_room = temp
    dr = [-1, 1, 0, 0]
    dc = [0, 0, -1, 1]
    for k in range(4):
        now_dr = i + dr[k]
        now_dc = j + dc[k]
        if 0 <= now_dr < N and 0 <= now_dc < N:
            num = arr[now_dr][now_dc] - arr[i][j]
            if num == 1:
                dfs(now_dr, now_dc, cnt+1, temp)

T = int(input())
for TC in range(T):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    max_cnt = 0
    min_room = 999999

    for row in range(N):
        for col in range(N):
            tmp = arr[row][col]
            dfs(row, col, 1, tmp)

    print('#{} {} {}'.format(TC+1, min_room, max_cnt))
```

