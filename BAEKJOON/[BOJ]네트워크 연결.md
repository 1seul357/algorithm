#### 문제

1. 컴퓨터를 연결하는 최소 비용 구하기

#### 해결방법

1. Union-Find

```python
def Find(x):
    if P[x] != x:
        P[x] = Find(P[x])
    return P[x]

def Union(a, b):
    pa = Find(a)
    pb = Find(b)
    P[pb] = pa


N = int(input())
M = int(input())
P = [i for i in range(N+1)]
edges = []
cost = 0

for i in range(M):
    a, b, c = map(int, input().split())
    edges.append([c, a, b])

edges.sort()
for c, a, b in edges:
    if Find(a) == Find(b):
        continue
    Union(a, b)
    cost += c

print(cost)
```

