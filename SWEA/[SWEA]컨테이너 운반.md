```python
'''
트럭과 컨테이너를 내림차순으로 정렬하고 하면 될 줄 알았는데, 이상한 답 출력. 트럭의 수만큼 옮길 수 있는 
것이므로 for i in range(M)으로 설정하고, i가 증가할 때마다 컨테이너의 무게를 전체 탐색 후 가장 큰 값을
찾아서 합계를 구하고, 제거한다. 트럭의 수가 더 많은 경우 weight는 0에서 갱신되지 않으므로 0보다 큰 
경우에만 제거해야한다. 
'''
T = int(input())
for TC in range(T):
    N, M = map(int, input().split())
    arr = list(map(int, input().split()))
    truck = list(map(int, input().split()))
    ans = 0

    for i in range(M):
        weight = 0
        for container in arr:
            if container <= truck[i] and container > weight: 
                weight = container
        if weight > 0: 
            ans += weight
            arr.remove(weight)

    print('#{} {}'.format(TC+1, ans))
```

