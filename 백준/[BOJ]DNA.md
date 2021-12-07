```python
'''
열에서 가장 많이 나온 문자 찾기(counts[idx][1] += 1)
가장 많이 나온 문자 = Hamming Distance를 최소로 만들 수 있음
Hamming Distance += N-max_cnt
'''
N, M = map(int, input().split())
arr = [list(map(str, list(input()))) for _ in range(N)]
result = 0     # Hamming Distance
answer = ''    # DNA 만들 변수
ans = 'Z'

for i in range(M):
    counts = [['T', 0], ['A', 0], ['G', 0], ['C', 0]]   # 열 바뀔때마다 값 초기화
    for j in range(N):
        if arr[j][i] == 'T':    # 문자가 T이면
            counts[0][1] += 1   # counts[0][1]에 +1
        elif arr[j][i] == 'A':
            counts[1][1] += 1
        elif arr[j][i] == 'G':
            counts[2][1] += 1
        elif arr[j][i] == 'C':
            counts[3][1] += 1
            
	max_cnt = 0      # 가장 많이 나온 문자의 개수 찾기
    for k in range(4):
        if counts[k][1] > max_cnt:  # counts[k][1]이 max_cnt보다 크다면
            max_cnt = counts[k][1]  # 갱신
            ans = counts[k][0]      # ans에 해당 문자 저장
        elif counts[k][1] == max_cnt:    # counts[k][1]과 max_cnt가 같으면
            if ord(counts[k][0]) < ord(ans):   # 사전순으로 앞서는거 찾기!
                ans = counts[k][0]  # ans에 해당 문자 저장

    answer += ans    # 여기까지 온 ans가 모든 조건을 만족하는 문자
    result += (N - max_cnt)   # N - max_cnt하면 Hamming Distance 구할 수 있음

print(answer)
print(result)
```

