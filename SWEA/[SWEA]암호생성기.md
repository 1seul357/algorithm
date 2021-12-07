```python
T = 10
for TC in range(T):
    tc = int(input())
    password = list(map(int, input().split()))
    cnt = 1

    while True:
        data = password.pop(0)       # 가장 첫번째 요소 꺼내기
        data -= cnt                  # cnt만큼 빼주기
        cnt += 1                     # cnt+1
        if data <= 0:                # 값이 0과 같거나 작아지면
            password.append(0)       # 0으로 추가하고 반복문 끝내기
            break
        else:                        # 값이 양수라면
            password.append(data)    # password에 추가하기
        if cnt >= 6:                 # cnt는 1~5까지만 반복되어야하므로 6과 같아지면
            cnt = 1                  # cnt를 다시 1로 초기화

    print('#{} '.format(TC+1), end='')
    print(*password)
```

