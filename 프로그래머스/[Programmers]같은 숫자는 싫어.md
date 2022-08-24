### 문제

배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수 완성하기

예시) arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return

</br>

</br>

### 해결방법

- 리스트 맨 위의 값이 새로 들어오는 값과 동일하면 `continue`, 다르면 `answer`에 추가

</br>

</br>

### 소스코드

```python
def solution(arr):
    answer = []
    answer.append(arr[0])
    for i in arr:
        if answer[-1] == i:
            continue
        else:
            answer.append(i)
    return answer
```

