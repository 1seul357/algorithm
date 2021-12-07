```python
'''
노트의 그림을 참고하면 이해하기 쉽다. 중요한 점은 check[0][0] = 0으로 설정. 설정하지 않으면 값이 이상하게 나온다. 마지막 5줄이 가장 중요한데, 다음 칸이랑 비교해서 최소값이 안나온다면 q에 좌표 값을 append하지 않아도 된다. (최소값 아니므로) temp 값을 구할 때, 다음칸이 현재칸보다 큰지 체크해야 한다. (안하면 fail) 다음칸이 현재칸보다 작다면 -값이 나오는데 이런 경우 결과 값이 이상해지기 때문이다. 다음 칸이 현재칸보다 작거나 같다면 temp = 1인 상태로 계산하면 된다. (추가비용 없음)
'''
T = int(input())
for TC in range(T):
    N = int(input())
    MAP = [list(map(int, input().split())) for _ in range(N)]
    check = [[10000] * N for _ in range(N)]
    check[0][0] = 0
    q = []
    q.append((0, 0))
    dr = [-1, 1, 0, 0]
    dc = [0, 0, -1, 1]

    while len(q) != 0:
        now_dr, now_dc = q.pop(0)
        for i in range(4):
            next_dr = now_dr + dr[i]
            next_dc = now_dc + dc[i]
            if 0 > next_dr or next_dr >= N or 0 > next_dc or next_dc >= N:
                continue
            temp = 1
            if MAP[next_dr][next_dc] > MAP[now_dr][now_dc]:
                temp = MAP[next_dr][next_dc] - MAP[now_dr][now_dc] + 1
            if check[next_dr][next_dc] > check[now_dr][now_dc] + temp:
                check[next_dr][next_dc] = check[now_dr][now_dc] + temp
                q.append((next_dr, next_dc))

    print('#{} {}'.format(TC+1, check[N-1][N-1]))
```

