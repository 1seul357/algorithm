```python
'''
deque 써야 함. 아니면 런타임 에러. bfs를 통해서 풀면 최소 count를 체크할 필요 없다. 
주의할 점은 for i in range(4)를 통해 4번 반복해야 하는 건데, 저렇게 하지 않으면 에러가 발생한다. 
'''
from collections import deque
 
def cal():
    global ans
    while len(q) != 0:
        tmp, count = q.popleft()
        if tmp == M:
            ans = count
            return
        for i in range(4):
            if i == 0:
                if tmp+1 <= 1000000 and visited[tmp+1] == 0:
                    visited[tmp+1] = 1
                    q.append([tmp+1, count+1])
            if i == 1:
                if tmp-1 <= 1000000 and visited[tmp-1] == 0:
                    visited[tmp-1] = 1
                    q.append([tmp-1, count+1])
            if i == 2:
                if tmp*2 <= 1000000 and visited[tmp*2] == 0:
                    visited[tmp*2] = 1
                    q.append([tmp*2, count+1])
            if i == 3:
                if tmp-10 <= 1000000 and visited[tmp-10] == 0:
                    visited[tmp-10] = 1
                    q.append([tmp-10, count+1])
 
 
T = int(input())
for TC in range(T):
    N, M = map(int, input().split())
    visited = [0]*1000001
    q = deque()
    ans = 0
    q.append([N, 0])
    cal()
 
    print('#{} {}'.format(TC+1, ans))
```

