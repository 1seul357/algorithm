### 문제

생태학에서 나무의 분포도를 측정하는 것은 중요하다. 그러므로 당신은 미국 전역의 나무들이 주어졌을 때, 각 종이 전체에서 몇 %를 차지하는지 구하는 프로그램을 만들어야 한다.

</br>

</br>

### 해결방법

- 입력 값의 길이가 0이라면 더 이상 값이 들어오지 않는 것이므로 반복문을 종료시킨다.
- 딕셔너리 사용해서 종의 개수를 계산한다.
- 주의할 점은 소수점 계산할 때, round를 사용하면 에러가 발생하므로 `"%.4f"` 를 사용해야 한다.

</br>

</br>

### 소스코드

```python
import sys
input = sys.stdin.readline

dic = {}
n = 0

while True:
    tree = input().rstrip()
    if len(tree) == 0:
        break
    if tree in dic:
        dic[tree] += 1
    else:
        dic[tree] = 1
    n += 1

ans = sorted(dic.items(), key=lambda x: x[0])

for answer in ans:
    print(answer[0], "%.4f" % (answer[1] * 100 / n))
```



