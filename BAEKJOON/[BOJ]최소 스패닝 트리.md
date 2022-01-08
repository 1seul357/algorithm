#### 문제

1. 주어진 그래프의 모든 정점들을 연결하는 부분 그래프 중에서 그 가중치의 합이 최소인 트리 구하기

#### 해결방법

1. Union-Find
2. 비용 적은 순서대로 정렬해서 탐색하면 가중치의 합을 최소로 한 트리 구할 수 있음

```python
def Find(x):
    if P[x] != x:
        P[x] = Find(P[x])
    return P[x]

def Union(a, b):
    pa = Find(a)
    pb = Find(b)
    P[pb] = pa


V, E = map(int, input().split())
P = [i for i in range(V+1)]
edges = []
cost = 0

for i in range(E):
    A, B, C = map(int, input().split())
    edges.append([C, A, B])

edges.sort()

for C, A, B in edges:
    if Find(A) == Find(B):
        continue
    Union(A, B)
    cost += C

print(cost)
```



