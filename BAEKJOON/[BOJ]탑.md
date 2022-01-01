```python
'''
1) 뒤에서부터 완전탐색 -> 시간초과 (실패코드1)
2) 앞에서부터 완전탐색 -> 시간초과 (실패코드2)
3) 스택 사용 -> 성공!!
'''

# 성공코드
N = int(input())
arr = list(map(int, input().split()))
stack = []       # 탑 크기를 저장하는 리스트 
ans = []         # 답(레이저 신호 수신 탑) 저장할 리스트
stack.append([0, arr[0]])    # 첫번째 탑 정보(인덱스, 탑 크기)를 stack에 저장
ans.append(0)       # 레이저는 왼쪽으로 쏘기 때문에 첫번째 탑은 무조건 값이 0

for i in range(1, len(arr)):    # 두번째 탑부터 비교
    # 현재 탑보다 큰 탑 중에서 가장 가까운 값이 레이저 신호 수신하는 탑이므로 스택의 마지막부터 비교
    for j in range(len(stack), -1, -1):    
        if stack:               # 스택에 값이 있다면
            tmp, temp = stack[-1]    # 인덱스와 탑 크기 정보를 변수로
            if temp > arr[i]:        # 현재 탑보다 크기가 크다면
                ans.append(tmp+1)    # ans에 레이저 신호 수신하는 탑 인덱스 추가 (인덱스 1부터)
                stack.append([i, arr[i]])   # 스택에 현재 탑 정보 추가
                break                # 답 찾았으므로 break
            elif temp < arr[i]: # 현재 탑보다 크기 작으면
                stack.pop(-1)   # 필요없으므로 스택에서 제거
        else:                   # 스택에 값이 없으면 (현재 탑이 앞에 탑들보다 큼)
            ans.append(0)       # 레이저 수신 탑 못찾았은 것이므로 ans에 0 추가
            stack.append([i, arr[i]])    # 현재 탑 정보 stack에 추가

for num in ans:
    print(num, end=" ")
    
    
    
# 실패코드1
from sys import stdin

N = int(input())
arr = list(map(int, stdin.readline().split()))
stack = []

for i in range(len(arr)-1, 0, -1):
    idx = i - 1
    while True:
        if arr[idx] > arr[i]:
            stack.append(idx+1)
            idx -= 1
            break
        if idx == 0:
            stack.append(0)
            break
        elif arr[idx] < arr[i]:
            idx -= 1
stack.append(0)

for j in stack[::-1]:
    print(j, end=" ")

    
    
# 실패코드2
from sys import stdin

N = int(input())
arr = list(map(int, stdin.readline().split()))
stack = []
ans = []
stack.append([0, arr[0]])
ans.append(0)

for i in range(1, len(arr)):
    for j in range(len(stack), -1, -1):
        if stack[j-1][1] > arr[i]:
            ans.append(stack[j-1][0])
            stack.append([i, arr[i]])
            break
        elif j == 0:
            ans.append(0)
            stack.append([i, arr[i]])
        elif len(stack) == 0:
            ans.append(0)
            break


for num in ans:
    if num == 0:
        print(0, end=" ")
    else:
        print(num+1, end=" ")
```

