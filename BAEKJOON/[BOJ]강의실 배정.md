**문제**

>  Si에 시작해서 Ti에 끝나는 N개의 수업이 주어지는데, 최소의 강의실을 사용해서 모든 수업을 가능하게 해야 한다. 참고로, 수업이 끝난 직후에 다음 수업을 시작할 수 있다.

</br>

**해결방법**

1. heapq
2. 오름차순으로 정렬한 후에 가장 빨리 끝나는(값이 가장 작은) 수업 첫번째 값으로 추가
3. 반복문을 돌면서 수업 시작 시간이 이전 수업의 끝나는 시간보다 빠르면 새로운 강의실 추가해야 하므로 `heappush`
4.  수업 시작 시간이 이전 수업의 끝나는 시간보다 빠르지 않다면 해당 강의실에서 이어서 수업할 수 있으므로 `heappop` 하고, 끝나는 시간 `heqppush`

</br>

**소스코드**

```python
import heapq

N = int(input())
study = [list(map(int, input().split())) for _ in range(N)]
room = []

study.sort()

heapq.heappush(room, study[0][1])

for i in range(1, N):
    if study[i][0] < room[0]:
        heapq.heappush(room, study[i][1])
    else:
        heapq.heappop(room)
        heapq.heappush(room, study[i][1])

print(len(room))
```

