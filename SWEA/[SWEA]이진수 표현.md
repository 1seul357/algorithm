```python
T = int(input())

for TC in range(T):
    N, M = map(int, input().split())
    ans = ''
    flag = "ON"

    for i in range(N):       # 총 N번 반복
        if M & (1<<i) == 0:  # M의 i번째 요소가 0이면 <왼쪽으로 1비트씩 밀면서 왼쪽부터 확인>
            flag = "OFF"     # flag = OFF
            break
    print('#{} {}'.format(TC + 1, flag))
```

