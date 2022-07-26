**문제**

> 문자열 S가 주어졌을 때, 이 문자열에서 단어만 뒤집으려고 한다.
>
> 먼저, 문자열 S는 아래와과 같은 규칙을 지킨다.
>
> 1. 알파벳 소문자('`a`'-'`z`'), 숫자('`0`'-'`9`'), 공백('` `'), 특수 문자('`<`', '`>`')로만 이루어져 있다.
> 2. 문자열의 시작과 끝은 공백이 아니다.
> 3. '`<`'와 '`>`'가 문자열에 있는 경우 번갈아가면서 등장하며, '`<`'이 먼저 등장한다. 또, 두 문자의 개수는 같다.
>
> 태그는 '`<`'로 시작해서 '`>`'로 끝나는 길이가 3 이상인 부분 문자열이고, '`<`'와 '`>`' 사이에는 알파벳 소문자와 공백만 있다. 단어는 알파벳 소문자와 숫자로 이루어진 부분 문자열이고, 연속하는 두 단어는 공백 하나로 구분한다. 태그는 단어가 아니며, 태그와 단어 사이에는 공백이 없다.

</br>

**해결방법**

- 조건문만 잘 설정하면 된다.
- flag 변수를 통해 문자가 "`<`" 인 경우에는 flag를 1로 만들어서 문자를 뒤집지 않고 그대로 추가한다.
- flag가 0인 경우에는 "`<>`" 안에 문자열이 있는 것이 아니므로 뒤집어서 추가한다.

</br>

**소스코드**

```python
arr = list(input())
flag = 0
ans = []
answer = ""

for str in arr:
    if str == "<":
        if len(answer) >= 1:
            ans.append(answer)
        flag = 1
        answer = ""
        ans.append(str)
    elif flag == 1 and str != ">":
        ans.append(str)
    elif flag == 1 and str == ">":
        flag = 0
        ans.append(str)
    elif flag == 0:
        if str == " ":
            answer += str
            ans.append(answer)
            answer = ""
        else:
            answer = str + answer

if len(answer) >= 1:
    ans.append(answer)

for str in ans:
    print(str, end="")
```

테스트 케이스가 7개 정도 있었는데, 조건문 작성할 때 도움이 되었다. 문제 자체는 어렵지 않았는데, 테스트 케이스에 맞게 조건문을 작성하느라 생각보다 시간이 오래 걸렸던 문제이다.