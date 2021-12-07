```python
def Find(x):
    if P[x] != x:   # 값과 부모 노드의 값이 다르면 
        P[x] = Find(P[x])   # 부모 노드 찾기 (리턴되면서 P[x]에 부모 노드 값 저장)
    return P[x]     # 부모 노드의 값 리턴


def Union(a, b):
    pa = Find(a)     # 부모 노드 찾기
    pb = Find(b)     # 부모 노드 찾기
    P[pb] = pa


T = int(input())
for TC in range(T):
    N, M = map(int, input().split())
    P = [i for i in range(N+1)]
    edges = []

    for i in range(M):
        f, t, cost = map(int, input().split())
        edges.append((cost, f, t))

    edges.sort()   # 가중치의 최소합을 구하기 위해서는 정렬해야 함
    ans = 0
    for cost, f, t in edges:    
        if Find(f) == Find(t):     # 부모가 같은가? 노드의 중복을 방지
            continue
        Union(f, t)                # 다르다면 아직 연결 안한 노드이므로 Union
        ans += cost

    print('#{} {}'.format(TC+1, ans))
```

