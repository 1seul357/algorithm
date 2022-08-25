### 문제

씬디는 애너그램(anagram) 프로그램을 만들어 줄 수 있는 남자를 좋아한다. 참고로 씬디는 매우 예쁘다.

애너그램 프로그램이란, 입력받은 영단어의 철자들로 만들 수 있는 모든 단어를 출력하는 것이다. 가령 "abc" 를 입력받았다면, "abc", "acb", "bac", "bca", "cab", "cba" 를 출력해야 한다.

입력받은 단어내에 몇몇 철자가 중복될 수 있다. 이 경우 같은 단어가 여러 번 만들어 질 수 있는데, 한 번만 출력해야 한다. 또한 출력할 때에 알파벳 순서로 출력해야 한다.

</br>

</br>

### 해결방법

- 처음에 `visited` 체크할 때, 딕셔너리를 사용하지 않고, 리스트를 사용했는데 시간초과가 발생한다.
- 딕셔너리로 각 문자열의 수를 저장하고, `dfs` 사용해서 문자를 조합하면 된다.
- 문자를 사용하면 -1, 돌아오면 다시 +1 한다.

</br>

</br>

### 소스코드

```python
import sys

def dfs(tmp):
    if len(tmp) == len(word):
        print(tmp)
        return
    for w in visited:
        if visited[w] != 0:
            visited[w] -= 1
            temp = tmp
            tmp += w
            dfs(tmp)
            visited[w] += 1
            tmp = temp


N = int(input())


for _ in range(N):
    word = sorted(list(map(str, sys.stdin.readline().strip())))
    visited = {}

    for i in range(len(word)):
        if word[i] in visited:
            visited[word[i]] += 1
        else:
            visited[word[i]] = 1

    dfs("")
```

