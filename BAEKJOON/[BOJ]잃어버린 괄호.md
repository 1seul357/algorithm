### 문제

세준이는 양수와 +, -, 그리고 괄호를 가지고 식을 만들었다. 그리고 나서 세준이는 괄호를 모두 지웠다.

그리고 나서 세준이는 괄호를 적절히 쳐서 이 식의 값을 최소로 만들려고 한다.

괄호를 적절히 쳐서 이 식의 값을 최소로 만드는 프로그램을 작성하시오.

</br>

</br>

### 해결방법

- 입력 받을 때, -를 기준으로 잘라서 `array` 리스트에 추가
- `array` 반복문을 돌면서 +를 기준으로 잘라서 덧셈하기
- `answer` 리스트에 모든 값 추가하고, - 계산하기

</br>

</br>

### 소스코드

```python
array = input().split("-")
answer = []

for arr in array:
    ans = 0
    tmp = arr.split("+")
    for i in tmp:
        ans += int(i)
    answer.append(ans)


sum = answer[0]
for i in range(1, len(answer)):
    sum -= answer[i]

print(sum)
```

