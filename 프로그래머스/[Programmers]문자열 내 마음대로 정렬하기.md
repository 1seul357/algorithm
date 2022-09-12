### 문제

문자열로 구성된 리스트 strings와, 정수 n이 주어졌을 때, 각 문자열의 인덱스 n번째 글자를 기준으로 오름차순 정렬하려 합니다. 예를 들어 strings가 ["sun", "bed", "car"]이고 n이 1이면 각 단어의 인덱스 1의 문자 "u", "e", "a"로 strings를 정렬합니다.

##### 제한 조건

- strings는 길이 1 이상, 50이하인 배열입니다.
- strings의 원소는 소문자 알파벳으로 이루어져 있습니다.
- strings의 원소는 길이 1 이상, 100이하인 문자열입니다.
- 모든 strings의 원소의 길이는 n보다 큽니다.
- 인덱스 1의 문자가 같은 문자열이 여럿 일 경우, 사전순으로 앞선 문자열이 앞쪽에 위치합니다.

</br>

</br>

### 해결방법

- strings를 가장 먼저 정렬해서 특정 인덱스의 문자가 같은 문자열이 여러개인 경우, 사전순으로 정렬할 수 있도록 한다.
- `key=lambda x: x[n]` 식을 이용해서 특정 인덱스 순서대로 문자열을 정렬할 수 있도록 만든다.
- answer에 추가해서 리턴한다.

</br>

</br>

### 소스코드

```python
def solution(strings, n):
    answer = []
    strings.sort()
    strings.sort(key=lambda x: x[n])
    for ans in strings:
        answer.append(ans)
    return answer
```

