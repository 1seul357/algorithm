```python
T = int(input())

for TC in range(T):
    N, M, L = map(int, input().split())
    node = [0]*(N+1)             # 노드번호 1부터 N까지 사용하기 위해 (N+1)

    for i in range(M):
        j, num = map(int, input().split())   # 리프 노드의 개수만큼 입력받기
        node[j] = num            # 리프 노드에 값 저장

    for i in range(N-M, 0, -1):  # 전체노드 - 리프노드. 뒤에서부터 탐색하면서 더하기
        if (i*2)+1 <= N:         # 왼쪽, 오른쪽 자식노드 모두 있는 경우
            node[i] = node[i*2] + node[i*2+1]
        else:              # 맨끝 노드는 왼쪽 자식노드만 있을 수 있음 (Testcase = 2)
            node[i] = node[i*2]

    print('#{} {}'.format(TC+1, node[L]))
```

