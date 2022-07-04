**문제**

> 서준이는 아빠로부터 N개의 회의를 모두 진행할 수 있는 최소 회의실 개수를 구하라는 미션을 받았다. 각 회의는 시작 시간과 끝나는 시간이 주어지고 한 회의실에서 동시에 두 개 이상의 회의가 진행될 수 없다. 단, 회의는 한번 시작되면 중간에 중단될 수 없으며 한 회의가 끝나는 것과 동시에 다음 회의가 시작될 수 있다. 회의의 시작 시간은 끝나는 시간보다 항상 작다. N이 너무 커서 괴로워 하는 우리 서준이를 도와주자.

</br>

**해결방법**

1. 그리디 (탐욕 알고리즘)
2. 강의실 배정과 똑같은 풀이방법으로 풀 수 있음
3. heapq 사용

</br>

**소스코드**

```python
import heapq

N = int(input())
study = [list(map(int, input().split())) for _ in range(N)]
room = []

study.sort()                 # 스터디 시간이 빠른 순서대로 정렬한다.
heapq.heappush(room, study[0][1])    # 가장 빨리 끝나는 스터디 시간을 room에 추가한다.

for i in range(1, N):
    if study[i][0] >= room[0]:     # 만약 스터디 시간이 이전의 스터디에 이어서 할 수 있다면
        heapq.heappop(room)            # room 스터디 시간을 갱신하기 위해 기존의 값 제거
        heapq.heappush(room, study[i][1])   # 새로운 스터디 시간의 끝나는 시간 추가
    else:                          # 이어서 할 수 없다면 새로운 스터디 방을 만들어야 하므로
        heapq.heappush(room, study[i][1])     # 새로운 스터디의 끝나는 시간 추가

print(len(room))        # 스터디 방 개수
```

