```python
'''
값을 입력받을 때, 맨 위에 있는 값부터 순서대로 리스트에 들어가기 때문에 arr[-1]이 아닌 arr[0]과 비교
'''

N = int(input())
arr = []        # 입력 값 넣을 리스트
array = []      # 수열 만들 수 있는지 확인하기 위해 만든 리스트
result = []     # +, - 넣을 리스트

for i in range(N):                       # 입력 받기
    num = int(input())
    arr.append(num)

for i in range(1, N+1):                  # 1부터 N까지 반복하면서
    array.append(i)                      # 새로운 array 리스트에 i값 추가
    result.append('+')                   # array 리스트에 값을 append 하면 '+' 추가 
    while arr[0] == array[-1]:    # arr 리스트 첫번째 요소와 array 리스트의 마지막 요소가 같으면
        arr.pop(0)                # arr 리스트 첫번째 값 제거
        array.pop(-1)             # array 리스트 마지막 값 제거
        result.append('-')        # pop인 경우 '-'를 result 리스트에 넣게
        if len(arr) == 0 or len(array) ==0:    # 스택이 비어있게 되면
            break                # 반복문 종료

if len(arr) == 0:                # arr 리스트의 길이가 0이면 수열을 만들 수 있다는 뜻
    for ans in result:
        print(ans)               # 결과 출력
else:                            # 수열 만들 수 없으면
    print('NO')                  # NO 출력
```

