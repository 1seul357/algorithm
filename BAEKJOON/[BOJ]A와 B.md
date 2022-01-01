```python
# S를 T로 만들 수 있으면 1, 만들 수 없으면 0
# S를 T로 만드는 코드는 메모리 초과, 시간 초과, 런타임 에러 발생
'''
T에서 S를 만들 수 있는지 확인
문자열의 뒤에 A를 추가한다. -> 문자열 뒤에 A를 제거한다.
문자열을 뒤집고 뒤에 B를 추가한다. -> 문자열 뒤에 B를 제거하고 문자열을 뒤집는다.
'''

# 성공코드
S = list(map(str, input()))
T = list(map(str, input()))
ans = 0

while True:
    if T[-1] == 'A':          # 맨끝 문자가 'A'라면 
        T.pop()               # 제거
    elif T[-1] == 'B':        # 맨끝 문자가 'B'라면
        T.pop()               # 제거하고
        T = T[::-1]           # 뒤집기
    if len(S) >= len(T):
        if S == T:            # 동일한 문자열인지 확인
            ans = 1
        break

print(ans)

# 실패코드
S = input()
T = input()
q = []
q.append([S, len(S)])
flag = 0
N = len(S)

while True:
    tmp, N = q.pop(0)
    if N > len(T):
        break
    if tmp == T:
        flag = 1
        break
    for i in range(2):
        if i == 0:
            q.append([tmp + 'A', N+1])
        elif i == 1:
            q.append([tmp[::-1] + 'B', N+1])

print(flag)
```

