### 문제

괄호가 바르게 짝지어졌다는 것은 '(' 문자로 열렸으면 반드시 짝지어서 ')' 문자로 닫혀야 한다는 뜻입니다. 예를 들어

- "()()" 또는 "(())()" 는 올바른 괄호입니다.
- ")()(" 또는 "(()(" 는 올바르지 않은 괄호입니다.

'(' 또는 ')' 로만 이루어진 문자열 s가 주어졌을 때, 문자열 s가 올바른 괄호이면 true를 return 하고, 올바르지 않은 괄호이면 false를 return 하는 solution 함수를 완성해 주세요.

##### 제한사항

- 문자열 s의 길이 : 100,000 이하의 자연수
- 문자열 s는 '(' 또는 ')' 로만 이루어져 있습니다.

</br>

</br>

### 해결방법

- 스택
- "(" 이면 arr 리스트에 추가한다.
- 만약 ")" 이면 arr 리스트에서 가장 앞에 있는 요소를 제거한다.
- 반복문이 끝나면 arr 리스트의 길이를 확인하고, 0이면 answer를 True로 저장한다.
- ❗ 가장 앞 요소가 ")" 이면 더 이상 확인할 필요 없이 false 이다.

</br>

</br>

### 소스코드

```python
def solution(s):
    answer = False
    arr = []
    if s[0] == ")":
        answer = False
    else:
        for i in s:
            if i == "(":
                arr.append(i)
            if arr and i == ")":
                arr.pop()
        if len(arr) == 0:
            answer = True
    return answer
```

