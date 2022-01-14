#### 문제

1. 두 가지 함수 R(뒤집기)과 D(버리기)가 주어졌을 때, 최종 결과 구하기

#### 해결방법

1. D(버리기)는 바로바로 수행하고, R(뒤집기)은 마지막에 한번만 수행한다. (시간초과 발생하므로)
2. flag 변수를 통해 최종 flag가 0이면 짝수번 뒤집어야하는 것이므로 뒤집지 않아도 된다. 그러므로 flag가 1인 경우에만 뒤집으면 된다.
3. 버릴 때는 뒤집은 상태에서 버려야 할 수도 있으므로, pop(0)과 pop(-1)을 통해 맨 앞과 맨 뒤가 삭제될 수 있도록 한다.

#### 주의사항

- R이 들어올 때마다 뒤집기를 수행하면 시간초과가 발생한다.
- 처음부터 입력이 [] 빈 값으로 들어오는 경우, 해당 배열의 길이 값은 1이 된다. 그러므로 첫 번째 데이터가 빈 값 ' ' 인지 체크하는 조건문이 추가되어야 한다.

```python
t = int(input())

for test_case in range(t):
    AC = input()
    N = int(input())
    arr = input()[1:-1].split(',')
    ans = ''
    flag = 0

    for data in AC:
        if data == 'R' and flag == 0:     # R이고, flag가 0이라면
            flag = 1                             # flag를 1로 바꿔주기
        elif data == 'R' and flag == 1:   # R이고, flag가 1이라면
            flag = 0                             # flag를 0으로 바꿔주기
        elif data == 'D':                 # D라면
            if len(arr) == 0:             # 배열의 길이가 0이라면
                ans = 'error'             		 # error
                break                     		 # 반복문 종료
            elif arr[0] == '':            # 처음부터 [ ]이 입력된 경우,
                ans = 'error'             		 # error
                break                     		 # 반복문 종료
            else:                         # 아직 데이터가 남아있는 경우,
                if flag == 0:             		 # flag가 0이면 맨 앞 데이터 삭제
                    arr.pop(0)      
                elif flag == 1:           		 # flag가 1이면 맨 뒤의 데이터를 삭제
                    arr.pop(-1)

    if len(ans) == 0:                     # ans가 0이라면 error가 아니라는 뜻이므로
        print('[', end='')                # 최종 arr 값을 출력하면 된다.
        if flag == 1:                     # flag가 1이라면 뒤집어주자
            arr = arr[::-1]               # 뒤집기
        print(*arr, sep=',', end='')
        print(']')
    else:                                 # ans가 0이 아니라면 error가 저장되어 있는 것이므로
        print(ans)                        # error 출력
```

