**문제**

> 일우는 블로그를 운영하면서 문제를 해결한 경우 파란색, 해결하지 못한 경우 빨간색으로 칠한다. 각 문제를 주어진 색으로 칠할 때 필요한 최소한의 작업 횟수를 구하는 프로그램을 작성하라.

</br>

**해결방법**

1. 그리디 (탐욕 알고리즘)
2. 처음부터 끝까지 빨간색으로 칠한 경우와 파란색으로 칠한 경우를 모두 구한다.
3. flag 변수를 통해 이전의 색깔과 다른 경우에만 +1 을 더한다.
4. 빨간색으로 모두 칠한 경우와 파란색으로 모두 칠한 경우 중 최소값을 출력한다.

</br>

**소스코드**

```python
num = int(input())
arr = input()
count1 = 1
count2 = 1
flag = 0

for i in range(num):
    if arr[i] == "B":
        flag = 0
        continue
    elif arr[i] == "R" and flag == 0:
        flag = 1
        count1 += 1


flag = 0
for i in range(num):
    if arr[i] == "R":
        flag = 0
        continue
    elif arr[i] == "B" and flag == 0:
        flag = 1
        count2 += 1

print(min(count1, count2))
```

</br>

이 문제는 접근 방법을 잘못 설정해서 풀지 못했던 문제이다. 이전의 색깔과 같은 경우는 다시 칠할 필요가 없으므로 이를 flag 변수를 추가하여 구분했다.