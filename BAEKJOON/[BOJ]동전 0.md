#### 문제

1. 동전을 적절히 사용해서 그 가치의 합을 K로 만들기
2. 합 K로 만들 때, 필요한 동전 개수의 최솟값을 구하기

#### 해결방법

1. 가지고 있는 동전을 큰 수부터 차례대로 꺼내기
2. i 값이 K보다 작거나 같으면 K - i 반복하면서 ans에 1씩 추가
3. K가 0이 되면 반복문 종료

```python
N, K = map(int, input().split())
money = []
ans = 0

for i in range(N):
    num = int(input())
    money.append(num)

for i in money[::-1]:
    if K == 0:
        break
    while i <= K:
        K -= i
        ans += 1

print(ans)
```

