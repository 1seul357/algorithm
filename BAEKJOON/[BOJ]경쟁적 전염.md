#### 문제

1. 시험관의 크기와 바이러스의 위치 정보가 주어졌을 때, *S*초가 지난 후에 (X,Y)에 존재하는 바이러스의 종류를 출력하기
2. 해당 위치에 바이러스가 존재하지 않는다면 0 출력

#### 해결방법

1. BFS
2. 바이러스 값이 작은 순서부터 퍼질 수 있도록 리스트 정렬
3. 1초당 바이러스가 있는 모든 위치에서 탐색할 수 있도록 범위 설정 len(li)

#### 의견

가장 어려웠던 부분이 '1초당 바이러스가 있는 모든 위치에서 탐색할 수 있도록 어떻게 설정하는가?' 였다.  예제를 보면 시작 위치가 (1, 1), (1, 3), (3, 1)인데, 1초당 해당 위치에서 모두 탐색을 해야 한다. 먼저 S초까지 셀 수 있도록 count 변수를 생성하고, len(li)의 반복문이 끝날 때 마다 1씩 증가시켰다. 그리고, 1초당 li의 길이만큼 반복하면서 바이러스가 상, 하, 좌, 우로 퍼질 수 있도록 구현하였다. 1초에는 li의 길이가 3이므로 3번 데이터를 꺼내서 상, 하, 좌, 우로 탐색하고, 2초에는 li의 길이가 4이므로 4번 데이터를 꺼내서 반복하게 된다.



```python
N, K = map(int, input().split())
arr = [list(map(int, input().split())) for _ in range(N)]
S, X, Y = map(int, input().split())
li = []
count = 0

for i in range(N):
    for j in range(N):
        if arr[i][j] != 0:           # 처음 입력받은 리스트에서 값이 0이 아니라면 (바이러스)
            li.append([arr[i][j], i, j])            # li리스트에 바이러스 값, 위치 추가

li.sort()            # 바이러스 값이 작은 순서부터 퍼져야 하므로 정렬하기!

while li:
    if count == S:                    # S초까지만 반복될 수 있도록 조건 설정
        break                         # S초가 되면 멈추기
    dr = [-1, 1, 0, 0]
    dc = [0, 0, -1, 1]
    for num in range(len(li)):   # li의 길이만큼 반복 (모든 바이러스 위치에서 탐색할 수 있도록)
        a, b, c = li.pop(0)
        for l in range(4):            # 상, 하, 좌, 우 탐색
            now_dr = b + dr[l]
            now_dc = c + dc[l]
            if 0 <= now_dr < N and 0 <= now_dc < N:      # N*N 리스트 범위 체크
                if arr[now_dr][now_dc] == 0:             # 아직 바이러스가 퍼지지 않았다면
                    arr[now_dr][now_dc] = a              # 바이러스 표시
                    li.append([arr[now_dr][now_dc], now_dr, now_dc]) # li에 다음 탐색할 위치 추가
    count += 1       # 1초 경과


print(arr[X-1][Y-1])
```

