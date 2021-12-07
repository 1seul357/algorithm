```python
postfix = input()
stack = []

for ch in postfix:       # 값을 하나씩 빼면서
    if ch.isalpha():           # ch가 문자열인지 확인
        print(ch, end="")      # 문자열이면 바로 출력
    elif ch == '(':            # 만약 '(' 라면
        stack.append(ch)       # 스택에 추가
    elif ch == ')':            # 만약 ')' 라면
        while len(stack) != 0 and stack[-1] != '(':  # 스택이 비어있지 않고, '(' 나오기 전까지
            print(stack.pop(-1), end="")               # 모든 요소 pop
        stack.pop(-1)          # 반복문이 끝난다면 stack[-1]이 '('라는 뜻이므로 '(' pop
    elif ch == '*' or ch == '/':   # '*' 과 '/' 라면
        # 스택이 비어있지 않고, '(' 나오기 전까지, stack[-1]이 * 혹은 / 라면 (우선순위 높은 것)
        while len(stack) != 0 and stack[-1] != "(" and (stack[-1] == "*" or stack[-1] == "/"):
            print(stack.pop(-1), end="")     # pop
        stack.append(ch)       # append
    elif ch == '+' or ch == '-':        # + 혹은 - 라면
        while len(stack) != 0 and stack[-1] != '(': # 스택이 비어있는지 체크, '(' 만나기 전까지
            print(stack.pop(-1), end="")     # pop
        stack.append(ch)       # append


while len(stack) != 0:         # 아직 스택에 남아있는게 있으면
    print(stack.pop(-1), end="")    # 모두 꺼내기
```

