```python
def Find(x):
    if P[x] != x:
        P[x] = Find(P[x])
    return P[x]
 
 
def Union(a, b):
    pa = Find(a)
    pb = Find(b)
    P[pb] = pa
 
 
T = int(input())
for TC in range(T):
    N, M = map(int, input().split())
    P = [i for i in range(N + 1)]
    edges = []
    counts = [0] * (N+1)
    ans = 0
 
    for i in range(M):
        n1, n2= map(int, input().split())
        edges.append((n1, n2))
 
    for i in range(2):                          # 한번만 돌리면 최소값으로 안나올 수 있다. 
        for n1, n2 in edges:
            if Find(n1) == Find(n2):
                continue
            Union(n1, n2)
 
    ans = len(set(P))
 
    print('#{} {}'.format(TC + 1, ans-1))
```

