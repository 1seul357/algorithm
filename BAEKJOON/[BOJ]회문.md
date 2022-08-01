**문제**

> 회문(回文) 또는 팰린드롬(palindrome)은 앞 뒤 방향으로 볼 때 같은 순서의 문자로 구성된 문자열을 말한다. 만일 그 자체는 회문이 아니지만 한 문자를 삭제하여 회문으로 만들 수 있는 문자열이라면 우리는 이런 문자열을 “유사회문”(pseudo palindrome)이라고 부른다. 예를 들어 ‘summuus’는 5번째나 혹은 6번째 문자 ‘u’를 제거하여 ‘summus’인 회문이 되므로 유사회문이다.
>
> 여러분은 제시된 문자열을 분석하여 그것이 그 자체로 회문인지, 또는 한 문자를 삭제하면 회문이 되는 “유사회문”인지, 아니면 회문이나 유사회문도 아닌 일반 문자열인지를 판단해야 한다. 만일 문자열 그 자체로 회문이면 0, 유사회문이면 1, 그 외는 2를 출력해야 한다. 

</br>

**해결방법**

- 완벽한 회문인 경우 0 출력하고, 다음 반복문으로 넘어간다.
- 완벽한 회문이 아닌 경우에는 유사회문인지, 아닌지를 확인해야 한다.
- 문자열 전체를 탐색할 필요는 없으므로 문자열의 길이를 반으로 나눠서 맨 앞과 맨 뒤부터 동시에 탐색한다.
- 탐색하다가 문자가 다르면 하나를 삭제할 경우 유사회문이 되는지 확인한다.
- 왼쪽과 오른쪽 하나씩 삭제해보고 유사회문이라면 1을 출력하고, 아니면 2를 출력하고 반복문을 종료한다.

</br>

**소스코드**

```python
N = int(input())

for _ in range(N):
    arr = []
    word = input()
    if word == word[::-1]:
        print(0)
        continue
    else:
        for str in word:
            arr.append(str)
            temp = arr
        i = 0
        while i != len(arr) // 2:
            if arr[i] == arr[len(arr)-i-1]:
                i += 1
            else:
                tmp = arr.pop(i)
                if arr == arr[::-1]:
                    print(1)
                    break
                elif arr != arr[::-1]:
                    arr.insert(i, tmp)
                    arr.pop(len(arr)-i-1)
                    if arr == arr[::-1]:
                        print(1)
                        break
                    else:
                        print(2)
                        break
```

