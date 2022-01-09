#### 문제

1. 1로 만들기 2와 똑같은 문제
2. 최소 연산 횟수만 출력하면 된다.

```python
N = int(input())
q = []
visited = [0]*10000000
q.append([N, 0])

while True:
    if len(q) == 0:
        break
    num, cnt = q.pop(0)
    if num == 1:
        break
    if visited[num] == 0:
        visited[num] = 1
        if num % 3 == 0:
            q.append([num // 3, cnt + 1])
        if num % 2 == 0:
            q.append([num // 2, cnt + 1])
        q.append([num - 1, cnt + 1])

print(cnt)
```

