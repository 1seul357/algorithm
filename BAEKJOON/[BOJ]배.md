**문제**

> 지민이는 화물을 배에 실어야 한다. 모든 화물은 박스에 안에 넣어져 있다. 항구에는 크레인이 N대 있고, 1분에 박스를 하나씩 배에 실을 수 있다. 모든 크레인은 동시에 움직인다.
>
> 각 크레인은 무게 제한이 있다. 이 무게 제한보다 무거운 박스는 크레인으로 움직일 수 없다. 모든 박스를 배로 옮기는데 드는 시간의 최솟값을 구하는 프로그램을 작성하시오. 단, 모든 박스를 배로 옮길 수 없으면 -1을 출력한다.

</br>

**해결방법**

1. 탐욕 알고리즘 (그리디)

2. 박스와 크레인을 내림차순으로 정렬하고, 박스를 옮길 수 있으면 remove 해서 제거

3. 반복문 하나 돌 때마다 time + 1 추가

4. 옮길 수 없는 경우 -1을 출력해야 하는데 이것은 반복문 들어가기 전에 해야 함

   > for문 뒤에 if len(boxes) != 0 으로 확인하고, 옮길 수 없는지 확인했는데, 시간초과 발생함 

</br>

**소스코드**

```python
import sys
input = sys.stdin.readline

N = int(input())
crane = list(map(int, input().split()))
M = int(input())
boxes = list(map(int, input().split()))
time = 0

crane.sort(reverse=True)
boxes.sort(reverse=True)

if crane[0] < boxes[0]:
    print(-1)
    sys.exit()

while True:
    for i in crane:
        for j in boxes:
            if i >= j:
                boxes.remove(j)
                break
    time += 1
    if len(boxes) == 0:
        break

print(time)
```

