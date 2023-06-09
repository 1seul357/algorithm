### 문제

다음 규칙을 지키는 문자열을 올바른 괄호 문자열이라고 정의합니다.

- `()`, `[]`, `{}` 는 모두 올바른 괄호 문자열입니다.
- 만약 `A`가 올바른 괄호 문자열이라면, `(A)`, `[A]`, `{A}` 도 올바른 괄호 문자열입니다. 예를 들어, `[]` 가 올바른 괄호 문자열이므로, `([])` 도 올바른 괄호 문자열입니다.
- 만약 `A`, `B`가 올바른 괄호 문자열이라면, `AB` 도 올바른 괄호 문자열입니다. 예를 들어, `{}` 와 `([])` 가 올바른 괄호 문자열이므로, `{}([])` 도 올바른 괄호 문자열입니다.

대괄호, 중괄호, 그리고 소괄호로 이루어진 문자열 `s`가 매개변수로 주어집니다. 이 `s`를 왼쪽으로 x (*0 ≤ x < (`s`의 길이)*) 칸만큼 회전시켰을 때 `s`가 올바른 괄호 문자열이 되게 하는 x의 개수를 return 하도록 solution 함수를 완성해주세요.

</br>

</br>

### 해결방법

- stack
- 여는 괄호가 나오면 스택에 넣고, 닿는 괄호가 나오면 스택에 가장 위에 있는 여는 괄호와 짝이 되는지 확인
- 짝이 된다면 스택에서 제거하고, 짝이 되지 않으면 올바르지 않은 괄호이므로 반복문 종료

</br>

</br>

### 소스코드

```python
def solution (s):
    arr = []
    answer = 0
    arr = list(s)
    def onCheck (s):
        stack = []
        flag = True
        for i in s:
            if (i == '(' or i == '{' or i == '['):
                stack.append(i)
            else:
                if (stack and stack[-1] == '(' and i == ')'):
                    stack.pop()
                elif (stack and stack[-1] == '{' and i == '}'):
                    stack.pop()
                elif (stack and stack[-1] == '[' and i == ']'):
                    stack.pop()
                else:
                    flag = False
                    break
        if (len(stack) != 0):
            flag = False
        return flag
    for i in range(len(s)):
        result = onCheck(arr)
        tmp = arr.pop(0)
        arr.append(tmp)
        if (result):
            answer += 1
    return answer
```

