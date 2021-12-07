```python
'''
시작하는 시간을 기준으로 탐색하면 시작하는 시간은 똑같은데 먼저 끝나는 시간이 뒤에 있을 경우, 정확한 계산을 할 수 없다. 그러므로 끝나는 시간을 기준으로 계산해야 한다. 끝나는 시간을 정렬하고, 그 다음 시작시간이 작업 가능한 시간이라면 now = arr[i][1] 끝나는 시간을 저장해주면 된다. 
'''
T = int(input())
for TC in range(T):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    now = 0
    ans = 0
    for i in range(N):
        for j in range(i, N):
            if arr[i][1] > arr[j][1]:
                arr[i], arr[j] = arr[j], arr[i]

    for i in range(N):
        if now <= arr[i][0]:
            now = arr[i][1]
            ans += 1
    print('#{} {}'.format(TC+1, ans))
```

