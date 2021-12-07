```python
'''
쌍이 되는 괄호의 인덱스 값을 arr 리스트에 추가했다. 
arr 리스트에서 가장 긴 오름차순 구간 구해서 max_cnt 값 출력
만약 arr 리스트의 길이가 0이라면 제대로된 괄호가 없다는 뜻이므로 0 출력

예시 ) ' (())( ' 답 : 4
stack = [0] -> [0, 1] 등 ( 의 인덱스 값 들어감
) 을 만나면
stack에서 맨 마지막 값을 꺼내고, arr 리스트에 쌍이 되는 (과 )의 인덱스 값 추가
arr = [1, 2] -> [1, 2, 0, 3]  한쌍이 한번에 들어가야 하므로 값은 두개씩 추가됨
arr 오름차순으로 정렬하고[0, 1, 2, 3], 가장 긴 값 찾기
'''

N = int(input())
string = list(input())
stack = []     # '(' 인덱스 넣을 리스트
arr = []       # '('과 ')'의 쌍이 되는 인덱스 넣을 리스트
cnt = 1
max_cnt = 0

for i in range(len(string)):
    if string[i] == "(":     # '(' 이면
        stack.append(i)      # '('의 인덱스 추가
    # ')'고, 스택이 비어있지 않다면 (스택에 '('의 인덱스가 있다면)
    elif string[i] == ')' and len(stack) != 0:   
        a = stack[-1]        # 가장 위에 있는 값을 변수 a에 저장
        stack.pop(-1)        # 스택에서 제거
        arr.append(a)        # arr 리스트에 쌍이 되는 (과 )의 인덱스 추가
        arr.append(i)

arr.sort()      # arr 리스트 정렬

# 가장 긴 오름차순 구간 찾기
for i in range(len(arr)):
    if arr[i] == arr[i-1]+1:      # 현재 위치의 값과 바로 전 위치의 값이 1 차이라면
        cnt += 1                  # cnt + 1
        if max_cnt < cnt:         # 최댓값 찾기
            max_cnt = cnt
    else:                         # 현재 위치의 값과 바로 전 위치의 값이 1 차이가 아니라면
        if max_cnt < cnt:         # 최댓값 찾고,
            max_cnt = cnt
        cnt = 1                   # cnt 다시 초기화

if len(arr) == 0:                 # arr의 길이가 0이라면 제대로된 괄호 없다는 뜻
    print(0)                      # 0 출력
else:                             # 아니면
    print(max_cnt)                # 최댓값 출력
```

