### 문제

정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

------

##### 제한사항

- numbers의 길이는 2 이상 100 이하입니다.
  - numbers의 모든 수는 0 이상 100 이하입니다.

</br>

</br>

### 해결방법

- 완전탐색
- 결과값만 나오면 되므로 반복할 때, `i+1` 부터 전체 길이까지로 범위를 설정한다.
- answer 리스트에는 중복되지 않게 저장하고, 마지막에 정렬

</br>

</br>

### 소스코드

```python
def solution(numbers):
    answer = []
    for i in range(len(numbers)-1):
        for j in range(i+1, len(numbers)):
            result = numbers[i] + numbers[j]
            if result not in answer:
                answer.append(result)
    answer.sort()
    return answer
```

