```python
def solution(price, money, count):
    answer = -1
    cnt = 0
    sum_price = 0
    
    while cnt < count:
        cnt += 1
        sum_price += (price * cnt)
    answer = sum_price - money
    
    if money >= sum_price:
        answer = 0
        
    return answer
```

