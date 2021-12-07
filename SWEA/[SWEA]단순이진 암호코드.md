```python
def search(password):
    if password == '0001101':
        return 0
    elif password == '0011001':
        return 1
    elif password == '0010011':
        return 2
    elif password == '0111101':
        return 3
    elif password == '0100011':
        return 4
    elif password == '0110001':
        return 5
    elif password == '0101111':
        return 6
    elif password == '0111011':
        return 7
    elif password == '0110111':
        return 8
    elif password == '0001011':
        return 9


T = int(input())
for TC in range(T):
    N, M = map(int, input().split())
    arr = [list(input()) for _ in range(N)]
    answer = ''
    result1 = 0
    result2 = 0
    answer2 = 0

    for k in range(N - 1, -1, -1):       # 뒤에서부터 1 찾기
        for j in range(M - 1, -1, -1):
            if arr[k][j] == '1':
                index1 = j
                index2 = k
                break

    for i in range(index1, 0, -7):       # 뒤에서부터 7개씩 꺼내기
        str1 = arr[index2][i-6:i+1]
        tmp = ''  
        if len(str1) == 7:               # 꺼낸 데이터의 길이가 총 7이라면
            for li in str1:              # 리스트 -> 문자열로 변환하기
                tmp += li
            if tmp != '0000000':         # 0000000이라면 암호코드 끝났을 것이므로 함수 호출 X
                temp = search(tmp)       # 비밀번호 찾기
                answer = str(temp) + answer   # 문자열로 나열해야 하므로 str 변환
        else:                            # 데이터의 길이가 7이 아니라면 리스트 끝난 것
            break

    for i in range(1, 8):
        if i % 2 != 0:                   # 홀수와 짝수 자리의 데이터 다르게 계산해야 함
            result1 += int(answer[i-1])
        else:
            result2 += int(answer[i-1])
    ans = (result1 * 3) + result2 + int(answer[7])   # 계산. answer[7]은 검증코드

    print('#{} '.format(TC + 1), end="")
    if ans % 10 == 0:                    # 10의 배수이면 올바른 암호코드
        for i in answer:
            answer2 += int(i)            # 코드 다 더하기
        print(answer2)
    else:
        print(0)                         # 10의 배수 아니므로 0 출력
```

