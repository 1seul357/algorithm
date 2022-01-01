```python
'''
counts 범위 지정때문에 오래 걸림.
수열의 각 원소가 N 이하가 아닐 수 있다.
'''

# 성공 코드
N = int(input())
arr = list(map(int, input().split()))
counts = [0]*10000001
result = [-1]*N

for i in arr:
    counts[i] += 1

stack = []

for i in range(N):
    while stack and counts[arr[stack[-1]]] < counts[arr[i]]:
        result[stack[-1]] = arr[i]
        stack.pop(-1)
    stack.append(i)


for num in result:
    print(num, end=" ")
    
    
# 시간초과
import sys

N = int(input())
arr = list(map(int, sys.stdin.readline().split()))
counts = [0]*10000001
result = [-1]*N

for i in arr:
    counts[i] += 1

stack = []

for i in range(N):
    for j in range(i, N):
        if counts[arr[j]] > counts[arr[i]]:
            result[i] = arr[j]
            break

for num in result:
    print(num, end=" ")
    
    
# 런타임 에러 (인덱스 에러)
N = int(input())
arr = list(map(int, input().split()))
counts = [0]*N
result = [-1]*N

for i in arr:
    counts[i] += 1

stack = []

for i in range(len(arr)):
    while stack and counts[arr[stack[-1]]] < counts[arr[i]]:
        result[stack[-1]] = arr[i]
        stack.pop(-1)
    stack.append(i)


print(*result)
```

