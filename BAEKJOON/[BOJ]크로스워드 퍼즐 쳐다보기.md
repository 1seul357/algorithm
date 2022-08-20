**문제**

크로스워드 퍼즐은 R*C크기의 직사각형으로 이루어져 있고, 각 칸은 비어있거나 막혀있다. 퍼즐은 가로(왼쪽->오른쪽) 또는 세로(위->아래)로 연속된 빈 칸에 단어를 채우면서 푼다.

동혁이는 크로스워드 퍼즐을 풀지 않는다. 그는 풀려있는 퍼즐을 쳐다본다. 그런 후에, 그는 그 퍼즐에서 사전순으로 제일 앞서는 단어를 찾는다. (단어는 적어도 2글자이다.)

크로스워드 퍼즐이 주어졌을 때, 사전순으로 제일 앞서는 단어를 출력하는 프로그램을 작성하시오.

</br>

</br>

**해결방법**

- `tmp` : 단어 만드는 변수, `cnt` : 반복문 끝인지 확인할 변수, `ans` : 완성된 단어 넣을 리스트
- 가로와 세로 반복문을 돌면서 단어가 될 수 있는 문자열을 찾고, `ans`에 추가한다.
- "#"을 만나면 `tmp`가 한 글자 이상인지 확인하고, `ans`에 추가한다. 그리고 `tmp`와 `cnt`를 초기화한다.
- 가로 혹은 세로 끝까지 갔으면 `ans`에 추가하고, `tmp`와 `cnt`를 초기화한다.

</br>

</br>

**소스코드**

```python
R, C = map(int, input().split())

arr = [input() for _ in range(R)]
ans = []
tmp = ""
cnt = 0

for i in range(R):
    for j in range(C):
        if arr[i][j] == "#":
            if len(tmp) > 1:
                ans.append(tmp)
            tmp = ""
            cnt = 0
        else:
            tmp += arr[i][j]
            cnt += 1
        if cnt == R or j == C-1:
            if len(tmp) >= 2:
                ans.append(tmp)
            tmp = ""
            cnt = 0

for i in range(C):
    for j in range(R):
        if arr[j][i] == "#":
            if len(tmp) > 1:
                ans.append(tmp)
            tmp = ""
            cnt = 0
        else:
            tmp += arr[j][i]
            cnt += 1
        if cnt == C or j == R-1:
            if len(tmp) >= 2:
                ans.append(tmp)
            tmp = ""
            cnt = 0

ans.sort()
print(ans[0])
```

