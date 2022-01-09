#### 문제

1. 3으로 나누기, 2로 나누기, 1 빼기 등 세개의 연산을 적절히 사용해서 1 만들기
2. 1을 만드는 최소 연산 횟수 출력하기

#### 해결방법

1. 값이 3으로 나눠지면 3을 나누고, 2로 나눠지면 2로 나눈다.
2. 1은 무조건 빼야 한다.
3. 1이 만들어지는 과정도 마지막에 함께 출력해야 하기 때문에 리스트 형식으로 q에 추가해야 한다.

```python
N = int(input())
q = []
visited = [0]*1000000
q.append([N, [N]])

while True:
    if len(q) == 0:
        break
    num, ans = q.pop(0)
    if num == 1:
        break
    if num % 3 == 0 and visited[num//3] == 0:
        visited[num//3] = 1
        q.append([num // 3, ans+[num//3]])
    if num % 2 == 0 and visited[num//2] == 0:
        visited[num//2] = 1
        q.append([num // 2, ans+[num//2]])
    if visited[num-1] == 0:
        visited[num-1] = 1
        q.append([num - 1, ans+[num-1]])

print(len(ans)-1)
print(*ans)
```

