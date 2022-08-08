**문제**

> 상근이는 카드 n(4 ≤ n ≤ 10)장을 바닥에 나란히 놓고 놀고있다. 각 카드에는 1이상 99이하의 정수가 적혀져 있다. 상근이는 이 카드 중에서 k(2 ≤ k ≤ 4)장을 선택하고, 가로로 나란히 정수를 만들기로 했다. 상근이가 만들 수 있는 정수는 모두 몇 가지일까?
>
> 예를 들어, 카드가 5장 있고, 카드에 쓰여 있는 수가 1, 2, 3, 13, 21라고 하자. 여기서 3장을 선택해서 정수를 만들려고 한다. 2, 1, 13을 순서대로 나열하면 정수 2113을 만들 수 있다. 또, 21, 1, 3을 순서대로 나열하면 2113을 만들 수 있다. 이렇게 한 정수를 만드는 조합이 여러 가지 일 수 있다.
>
> n장의 카드에 적힌 숫자가 주어졌을 때, 그 중에서 k개를 선택해서 만들 수 있는 정수의 개수를 구하는 프로그램을 작성하시오.

</br>

**해결방법**

- DFS
- 중복 체크하면서 조합하기
- 순서대로 append 해야하기 때문에 방문 체크 후에 ans에 추가하고, return 되어서 돌아오면 ans에서 제거
  - cnt가 k와 같을 때, ans에 추가하는 방식으로 하면 안된다.

</br>

**소스코드**

```python
def dfs(cnt):
    if cnt == k:
        answer.add(''.join(map(str, ans)))
        return
    for i in range(n):
        if visited[i] == 0:
            visited[i] = 1
            ans.append(arr[i])
            dfs(cnt + 1)
            visited[i] = 0
            ans.pop(-1)


n = int(input())
k = int(input())
arr = []
ans = []
answer = set()
visited = [0] * n

for _ in range(n):
    arr.append(int(input()))

dfs(0)

print(len(answer))
```

