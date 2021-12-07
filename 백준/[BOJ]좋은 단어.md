```python
N = int(input())
ans = 0

for i in range(N):
    arr = input()
    stack = []

    for j in arr:
        if len(stack) == 0:         # 스택이 비었으면
            stack.append(j)         # 문자열 추가
        elif stack[-1] == j:        # 스택이 비어있지 않고, 맨 위의 값이 j와 같으면
            stack.pop(-1)           # 맨 위의 값 삭제 (AA)
        else:                       # 스택이 비어있지 않고, 맨 위의 값이 다르면
            stack.append(j)         # 문자열 추가
 
    if len(stack) == 0:             # 한줄을 다 탐색했으면 스택 길이 확인
        ans += 1                    # 스택이 비어있으면 좋은 단어 +1

print(ans)
```

