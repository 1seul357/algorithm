```python
def search(n):       # 16진수를 10진수로 바꿔주기 위한 함수
    if n == 'A': 
        return 10
    if n == 'B':
        return 11
    if n == 'C':
        return 12
    if n == 'D':
        return 13
    if n == 'E':
        return 14
    if n == 'F':
        return 15


T = int(input())
for TC in range(T):
    N, num = input().split()
    N = int(N)
    arr = [[0] * 4 for _ in range(N)]    # 2차원배열로 만들어야 함
    k = 0
    for n in num:          # 입력받은 문자 한글자씩 꺼내기
        if n == 'A' or n == 'B' or n == 'C' or n == 'D' or n == 'E' or n == 'F':
            result = search(n)           # 10진수로 바꿔오기 위한 함수 호출
        else:
            result = n     # 바꿀 필요 없는 숫자는 그냥 넣기
        result = int(result)    # 정수로 바꾸기
        for i in range(1 << 4):     # 2진수가 4비트이므로 2의 4승만큼만 반복하면 된다. (16번)
            if i == result:     
                for j in range(4):  # 4비트이므로 4번 반복
                    if i & (1 << j): # (1<<j) j가 0부터 3까지이고, 이진수는 2의 3승, 2승, 1승, 										0승 이렇게 나열되어 있음. 즉 j=0은 가장 오른쪽에 있음
                        arr[k][3 - j] = 1  # 2의 3승, 2승, 1승, 0승은 3-j로 해야           										인덱스 0, 1, 2, 3으로 저장 가능
        k += 1      # 리스트 행 +1
    print('#{} '.format(TC + 1), end="")
    for i in arr:
        for j in i:
            print(j, end="")
    print()
```

