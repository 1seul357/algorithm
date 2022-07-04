**문제**

> 정수 A를 B로 바꾸려고 한다. 가능한 연산은 다음과 같은 두 가지이다.
>
> - 2를 곱한다.
> - 1을 수의 가장 오른쪽에 추가한다. 
>
> A를 B로 바꾸는데 필요한 연산의 최솟값을 구해보자.

</br>

**해결방법**

1. B -> A가 가능한지 확인하는 것이 빠르다.
2. 만약 B가 2로 나누어진다면 2로 나누고, B 마지막 숫자가 1이라면 1을 제거한다.
3. 2번에 해당하지 않는다면 A로 만들 수 없는 것이므로 -1을 출력하기 위해 flag를 1로 바꿔준다.
4. 반복문이 끝나면 flag를 확인한다. flag가 0이라면 A로 만들 수 있는 것이므로 count를 출력한다.
5. flag가 1이라면 A로 만들 수 없는 것이므로 -1을 출력한다.

</br>

**소스코드**

```python
a, b = map(int, input().split())
count = 1
flag = 0

while a != b and b != 0:
    if a > b:
        flag = 1
        break
    if b % 2 == 0:
        b //= 2
        count += 1
    elif b % 10 == 1:
        b //= 10
        count += 1
    else:
        flag = 1
        break

if flag == 0:
    print(count)
else:
    print(-1)
```

