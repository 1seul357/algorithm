```python
def perm(M, k):
    global max_num
    ans = ''
    for i in arr:
        ans += str(i)              # 리스트에 있는 숫자를 문자열로 나열한 다음에
    ans = int(ans)                 # 숫자로 변환
    answer = ans + k               # 중복 확인하기 위한 변수 설정, 특정 값과 K번째 횟수 확인
    if k == M:                     # 총 M번째만큼 숫자를 바꿨다면
        if ans > max_num:		   # 최댓값보다 큰지 확인하고,
            max_num = ans		   # 크다면 최댓값이 ans
        return      # if문을 통과하거나 못하거나 모두 return 해야하므로 if문과 같은 줄에서 return
    if answer in visited:          # visited 리스트에 answer값이 있다면
     # 가지치기. k번째 횟수에서 특정 값(ans)을 확인했다면 그 뒤를 중복해서 확인할 필요 없다. 가지치기        없으면 시간초과로 Fail
        return					  
    visited.append(answer)         # 아직 확인 안했으면 visited 리스트에 append
    for i in range(len(arr)):     
        for j in range(i + 1, len(arr)):    # 선택정렬은 i와 i+1번째 확인해야 하므로
            arr[i], arr[j] = arr[j], arr[i]    # 선택정렬
            perm(M, k + 1)         # dfs
            arr[i], arr[j] = arr[j], arr[i]    # 다시 원위치로 


T = int(input())

for TC in range(T):
    N, M = map(int, input().split())
    N = str(N)
    max_num = 0
    arr = []
    visited = []    # visited = [[0]*1000000 for _ in range(11)]로 하면 메모리 초과로 Fail
    for i in N:
        arr.append(int(i))
    perm(M, 0)
    print('#{} {}'.format(TC + 1, max_num))
```

