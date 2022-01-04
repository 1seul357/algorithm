#### 문제

1. 0 a b 이면 a와 b의 집합 합치기
2. 1 a b 이면 같은 집합에 속해 있는지 확인하기

#### 해결방법

1. Union-Find 
2. 맨 앞 숫자가 0인지 1인지 확인하고, 각각 해당하는 조건문으로 이동
3. 합집합으로 만들 때, 이미 같은 집합에 속해 있으면 다음 반복문으로 넘기기

#### 주의사항

- import sys를 작성하지 않으면 시간초과 발생

```python
import sys

def Find(x):                                  # 부모 노드 찾기
    if P[x] != x:
        P[x] = Find(P[x])
    return P[x]

def Union(a, b):                               # 합집합
    pa = Find(a)
    pb = Find(b)
    P[pb] = pa

N, M = map(int, sys.stdin.readline().split())
P = [i for i in range(N+1)]                    # 부모 노드 값 저장할 리스트 생성

for i in range(M):
    z, a, b = map(int, sys.stdin.readline().split())
    if z == 0:                                 # 0이면 합집합으로 만들기
        if Find(a) == Find(b):                 # 이미 같은 집합에 속해 있는 경우
            continue                           # 넘기기
        Union(a, b)                            # 아니면, 합치기
    elif z == 1:                               # 1이면 같은 집합에 포함되어 있는지 확인하기
        if Find(a) == Find(b):                 # 같은 집합에 속해 있으면
            print('YES')                       # YES 출력
        else:                                  # 아니면
            print('NO')                        # NO 출력
```



