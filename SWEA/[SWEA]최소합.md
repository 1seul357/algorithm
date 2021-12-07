```python
def dfs(row, col, sum_num):
    dr = [1, 0]              # '우', '하'만 이동할 수 있음
    dc = [0, 1]
    global min_num
    if row == N-1 and col == N-1:    # 행과 열이 오른쪽 끝, 맨아래에 있는 경우 탐색 끝
        if sum_num < min_num:        # 합계가 최소값인가?
            min_num = sum_num        # 최소값 갱신
            return
    if sum_num > min_num:            # 가지치기. row와 col이 N-1이 되기 전에 합계가 최소값보다 			return			           커지면 탐색 멈추고 리턴
    for i in range(2):               # 우측과 아래측으로만 이동가능하므로 2
        now_dr = row + dr[i]         # 델타 검색
        now_dc = col + dc[i]
        if 0 <= now_dr < N and 0 <= now_dc < N:    # 이중리스트 범위 안에 있다면
            sum_num += arr[now_dr][now_dc]         # 합계 구하기
            dfs(now_dr, now_dc, sum_num)
            sum_num -= arr[now_dr][now_dc]         # 다른 곳도 탐색해야하므로 다시 원상태로.


T = int(input())
for TC in range(T):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]  # 이중리스트 형태로 입력받기
    min_num = 999999
    sum_num = arr[0][0]                # 인덱스 0,0번부터 출발
    dfs(0, 0, sum_num)
    print('#{} {}'.format(TC+1, min_num))
```

