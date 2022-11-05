### 문제

자연수 n이 매개변수로 주어집니다. n을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

------

##### 제한사항

- n은 1 이상 100,000,000 이하인 자연수입니다.

</br>

</br>

### 해결방법

- 3진법으로 바꾸고, 앞 뒤 반전 시킬 수 있도록 `answer += str(r)` 로 작성한다.
- 10진법으로 다시 표현한다.

</br>

</br>

### 소스코드

```python
def solution(n):
    answer = ''
    while n >= 1:
        r = n % 3
        n //= 3
        answer += str(r)
    answer = int(answer, 3)
    return answer
```

