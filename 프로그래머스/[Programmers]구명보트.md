### 문제

무인도에 갇힌 사람들을 구명보트를 이용하여 구출하려고 합니다. 구명보트는 작아서 한 번에 최대 **2명**씩 밖에 탈 수 없고, 무게 제한도 있습니다.

예를 들어, 사람들의 몸무게가 [70kg, 50kg, 80kg, 50kg]이고 구명보트의 무게 제한이 100kg이라면 2번째 사람과 4번째 사람은 같이 탈 수 있지만 1번째 사람과 3번째 사람의 무게의 합은 150kg이므로 구명보트의 무게 제한을 초과하여 같이 탈 수 없습니다.

구명보트를 최대한 적게 사용하여 모든 사람을 구출하려고 합니다.

사람들의 몸무게를 담은 배열 people과 구명보트의 무게 제한 limit가 매개변수로 주어질 때, 모든 사람을 구출하기 위해 필요한 구명보트 개수의 최솟값을 return 하도록 solution 함수를 작성해주세요.

##### 제한사항

- 무인도에 갇힌 사람은 1명 이상 50,000명 이하입니다.
- 각 사람의 몸무게는 40kg 이상 240kg 이하입니다.
- 구명보트의 무게 제한은 40kg 이상 240kg 이하입니다.
- 구명보트의 무게 제한은 항상 사람들의 몸무게 중 최댓값보다 크게 주어지므로 사람들을 구출할 수 없는 경우는 없습니다.

</br>

</br>

### 해결방법

- deque 사용하지 않으면 효율성 테스트 1번에서 실패한다.
- 리스트에서 값을 꺼내고, 가장 적은 무게와 함께 보트를 태울 수 있으면 합해서 태운다.
- 만약 가장 적은 무게를 함께 태울 수 없다면 그 다음으로 적은 무게도 태울 수 없으므로 가장 적은 값만 확인하면 된다.

</br>

</br>

### 소스코드

**성공**

```python
from collections import deque

def solution(people, limit):
    answer, weight = 0, 0
    people.sort(reverse=True)
    people = deque(people)

    while len(people) >= 1:
        weight = 0
        answer += 1
        weight += people.popleft()
        if people and limit >= people[-1] + weight:
            weight += people.pop()
    return answer
```

**실패**

```python
def solution(people, limit):
    answer, weight = 0, 0
    people.sort()

    while len(people) >= 1:
        weight = 0
        answer += 1
        weight += people.pop()
        if people and limit >= people[0] + weight:
            weight += people.pop(0)
    return answer
```

