### 문제

프로그래머스 팀에서는 기능 개선 작업을 수행 중입니다. 각 기능은 진도가 100%일 때 서비스에 반영할 수 있습니다.

또, 각 기능의 개발속도는 모두 다르기 때문에 뒤에 있는 기능이 앞에 있는 기능보다 먼저 개발될 수 있고, 이때 뒤에 있는 기능은 앞에 있는 기능이 배포될 때 함께 배포됩니다.

먼저 배포되어야 하는 순서대로 작업의 진도가 적힌 정수 배열 progresses와 각 작업의 개발 속도가 적힌 정수 배열 speeds가 주어질 때 각 배포마다 몇 개의 기능이 배포되는지를 return 하도록 solution 함수를 완성하세요.

##### 제한 사항

- 작업의 개수(progresses, speeds배열의 길이)는 100개 이하입니다.
- 작업 진도는 100 미만의 자연수입니다.
- 작업 속도는 100 이하의 자연수입니다.
- 배포는 하루에 한 번만 할 수 있으며, 하루의 끝에 이루어진다고 가정합니다. 예를 들어 진도율이 95%인 작업의 개발 속도가 하루에 4%라면 배포는 2일 뒤에 이루어집니다.

##### 입출력 예

| progresses               | speeds             | return    |
| ------------------------ | ------------------ | --------- |
| [93, 30, 55]             | [1, 30, 5]         | [2, 1]    |
| [95, 90, 99, 99, 80, 99] | [1, 1, 1, 1, 1, 1] | [1, 3, 2] |

</br>

</br>

### 해결방법

- 스택
- ans : 남은 작업량을 확인하고, result : 얼마나 걸리는지 날짜를 계산한다.
- 가장 앞의 값을 꺼내서 그 값보다 작은 값들은 모두 pop 시키고, 배포되는 기능의 수(cnt) 에 + 1 한다.
- 안쪽에 있는 반복문 하나 끝날 때마다 동시에 배포되는 기능들은 모두 끝났으므로 answer에 값을 추가한다.

</br>

</br>

### 소스코드

```python
import math

def solution(progresses, speeds):
    answer = []
    result = []
    for i in range(len(progresses)):
        ans = 100 - progresses[i]
        result.append(math.ceil(ans / speeds[i]))
    while len(result) != 0:
        day = result.pop(0)
        cnt = 1
        while result and day >= result[0]:
            cnt += 1
            result.pop(0)
        answer.append(cnt)
    return answer
```

