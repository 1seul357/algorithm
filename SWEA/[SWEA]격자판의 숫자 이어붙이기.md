```python
'''
중복 체크를 set으로 하지 않으면 시간 초과가 발생한다. if not in 이렇게 하면 왜 시간초과가 나는걸까... 
한 인덱스에서 동서남북으로만 이동하고 끝이 아니라 이동 -> 이동 -> 이동하면서 길이가 7이기만 하면 된다. 
인덱스 동쪽 - > 동, 서, 남, 북 이런식으로 탐색
'''
def dfs(row, col, cnt, ans):
    dr = [-1, 1, 0, 0]
    dc = [0, 0, -1, 1]
    if cnt == 7:
        answer.append(ans)
        return
    for i in range(4):
        now_dr = row + dr[i]
        now_dc = col + dc[i]
        if 0 <= now_dr < 4 and 0 <= now_dc < 4:
            tmp = ans
            ans += arr[now_dr][now_dc]
            dfs(now_dr, now_dc, cnt+1, ans)
            ans = tmp

T = int(input())
for TC in range(T):
    arr = [list(map(str, input().split())) for _ in range(4)]
    answer = []

    for i in range(4):
        for j in range(4):
            dfs(i, j, 0, '0')
    result = set(answer)
    a = len(result)

    print('#{} {}'.format(TC+1, a))
```

