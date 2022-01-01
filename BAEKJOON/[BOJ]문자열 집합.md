```python
'''
시간이 엄청 오래 걸리지만 통과하기는 함.
집합 S에 들어가는 문자열(array)은 똑같은 문자열들이 있다. 그래서 set을 통해 중복되는 문자열을 제거하면 빠르게 통과할 수 있다. set([input() for _ in range(N)])
'''

N, M = map(int, input().split())
array = [input() for _ in range(N)]
arr = [input() for _ in range(M)]
count = 0

for tmp in arr:             # arr 리스트에서 문자열 하나씩 꺼내서
    if tmp in array:        # array에 있는지 확인하고,
        count += 1          # 있으면 + 1

print(count)
```

