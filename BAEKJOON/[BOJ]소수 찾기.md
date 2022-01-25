#### 문제

1. 주어진 수 N개 중에서 소수가 몇 개인지 찾아서 출력하기

#### 해결방법

1. 리스트에 있는 숫자 하나씩 꺼내서 2부터 해당 숫자까지 0으로나누어 떨어지는지 확인
2. 0으로 나누어 떨어진다면 소수 아님

```python
N = int(input())
num = list(map(int, input().split()))
count = 0

for i in num:
    flag = 0
    if i == 1:
        continue
    for j in range(2, i):
        if i % j == 0:
            flag = 1
            break
    if flag == 0:
        count += 1

print(count)
```

