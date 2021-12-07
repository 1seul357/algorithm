```python
def dfs(count, ans):
    global min_count
    if count >= num:
        if min_count > ans:
            min_count = ans
        return
    if min_count < ans:
        return
    tmp = battery[count]
    for j in range(tmp, 0, -1):
        index = j+count
        dfs(index, ans+1)
 
 
T = int(input())
 
for TC in range(T):
    battery = list(map(int, input().split()))
    num = battery[0]
    min_count = 999999
    dfs(1, 0)
 
    print('#{} {}'.format(TC+1, min_count-1))
```

