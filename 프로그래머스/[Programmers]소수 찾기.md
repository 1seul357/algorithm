### 문제

한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.

각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.

##### 제한사항

- numbers는 길이 1 이상 7 이하인 문자열입니다.
- numbers는 0~9까지 숫자만으로 이루어져 있습니다.
- "013"은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.

</br>

</br>

### 해결방법

- 완전탐색, dfs
- dfs와 visited 리스트 사용해서 만들 수 있는 숫자를 모두 만든다.
- lstrip 함수 사용해서 앞에 0, 00, 000 으로 시작하는 숫자들은 0을 모두 제거한다.
- 소수가 아니라면 flag를 0으로 만들고, 반복문을 종료한다.
- flag가 1이라면 소수이므로 answer + 1 한다.

</br>

</br>

### 소스코드

```python
def solution(numbers):
    def dfs(str):
        tmp = str.lstrip("0")
        if len(tmp) != 0:
            ans.add(int(tmp))
        for j in range(len(numbers)):
            if visited[j] == 0:
                visited[j] = 1
                dfs(str + numbers[j])
                visited[j] = 0

    answer = 0
    ans = set()
    visited = [0]*len(numbers)
    for i in range(len(numbers)):
        dfs("")
    for num in ans:
        flag = 1
        if num == 1:
            continue
        for i in range(2, num):
            result = num % i
            if result == 0:
                flag = 0
                break
        if flag == 1:
            answer += 1
    return answer
```

