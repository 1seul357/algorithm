```python
"""
while문이 아닌 if문으로 설정하면 조건문이 많아져서 코드가 복잡해진다. 처음에는 n의 값에 따라 cnt-2, 
cnt-1 혹은 cnt+1, cnt+2 이런식으로 작성했는데, 이렇게하면 테스트케이스를 통과하지 못한다. 
왜냐하면 이전 코드는 숫자가 0이거나 혹은 9가 아니라면 모두 cnt-1, cnt, cnt+1 값이 1이상인지 확인했는데, 
실제로는 cnt-2, cnt-1, cnt가 run일수도 있고, cnt, cnt+1, cnt+2가 run일 수도 있기때문이다. 
그러므로 while문을 통해 0부터 7번까지 돌면서 triple과 run을 확인해주면 된다. 값을 입력받자마자 바로 
함수를 호출해야 run 혹은 triple이 먼저 나온 사람을 찾기 쉽다.
"""
def check(count, n):
    cnt = 0
    while cnt < 8:
        if count[cnt] >= 1 and count[cnt+1] >= 1 and count[cnt+2] >= 1:
            return 1
        elif count[n] >= 3:
            return 1
        cnt += 1
    return 0

T = int(input())
for TC in range(T):
    num = list(map(int, input().split()))
    count1 = [0]*10
    count2 = [0]*10
    flag = 0

    for i in range(len(num)):
        if i % 2 == 0:
            count1[num[i]] += 1
            result = check(count1, num[i])
            if result == 1:
                flag = 1
                break
        else:
            count2[num[i]] += 1
            result = check(count2, num[i])
            if result == 1:
                flag = 2
                break
    print('#{} {}'.format(TC+1, flag))
```

