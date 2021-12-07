```python
T = int(input())
 
for TC in range(T):
    N, M = map(int, input().split())
    arr1 = list(map(int, input().split()))
    arr2 = list(map(int, input().split()))
    arr1.sort()
    count = 0
 
    for n in range(len(arr2)):
        tmp = arr2[n]
        l = 0
        r = len(arr1)-1
        flag = 0
        while l <= r:
            mid = (l+r)//2
            if tmp == arr1[mid]:
                count += 1
                break
            elif tmp < arr1[mid] and flag != -1:
                r = mid-1
                flag = -1
            elif tmp > arr1[mid] and flag != 1:
                l = mid+1
                flag = 1
            else:
                break
 
    print('#{} {}'.format(TC+1, count))
```

