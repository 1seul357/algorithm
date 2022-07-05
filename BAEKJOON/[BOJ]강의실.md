**문제**

> N개의 강의가 있다. 우리는 모든 강의의 시작하는 시간과 끝나는 시간을 알고 있다. 이때, 우리는 최대한 적은 수의 강의실을 사용하여 모든 강의가 이루어지게 하고 싶다.
>
> 물론, 한 강의실에서는 동시에 2개 이상의 강의를 진행할 수 없고, 한 강의의 종료시간과 다른 강의의 시작시간이 겹치는 것은 상관없다. 필요한 최소 강의실의 수를 출력하는 프로그램을 작성하시오.

</br>

**해결방법**

1. 그리디 (탐욕 알고리즘)
2. heapq
3. 강의 번호는 중요하지 않음. 강의 시작 시간과 종료 시간만 사용하면 된다.
4. 강의 시작 시간을 기준으로 정렬해야 하므로 `lambda`를 사용한다.

</br>

**소스코드**

```python
import heapq

N = int(input())
room = []
study_time = [list(map(int, input().split())) for _ in range(N)]

study_time.sort(key=lambda x:x[1])

heapq.heappush(room, study_time[0][2])

for i in range(1, N):
    if room[0] <= study_time[i][1]:
        heapq.heappop(room)
        heapq.heappush(room, study_time[i][2])
    else:
        heapq.heappush(room, study_time[i][2])

print(len(room))
```

