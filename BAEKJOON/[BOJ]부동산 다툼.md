```python
'''
똑같은 코드인데, import sys 안하면 시간초과 발생..
1) 오리들이 갖고 싶어하는 땅 x부터 1번 땅까지 탐색. 
2) 1번 땅까지 탐색하면서 점유된 땅을 만나면 flag에 점유된 땅 번호 저장.
3) 만약 1번 땅까지 왔는데, flag가 0이라면 중간에 점유한 땅을 만나지 않았다는 뜻이다
4) flag 출력


주의할 점) 오리가 땅을 가질 수 없다면 처음 마주치는 점유된 땅의 번호를 구해야 한다. 그러므로 
뒤에서부터 탐색하다가 점유된 땅을 만나면 break하면 안된다. -> 처음에 이렇게 해서 틀림
1번 땅까지 탐색하는 동안 점유된 땅을 만나면 flag 값이 갱신되므로 처음 마주치는 점유된 땅을 구할 수 있다.
'''

import sys
input = sys.stdin.readline

N, Q = map(int, input().split())
visited = [0]*(N+1)

for i in range(Q):
    x = int(input())                   # 오리들이 갖고 싶어하는 땅 입력받기
    flag = 0                           # 점유된 땅이 있는지 확인할 flag 변수
    arr = []
    arr.append(x)

    while len(arr):
        now = arr.pop(0)
        if now == 1:                   # 만약 1번 땅까지 왔다면
            if flag == 0:              # flag가 0인지 확인한다. (점유된 땅 안 만났는지 확인)
                # 점유된 땅을 안 만났으면 오리가 갖고싶어하는 땅 가질 수 있으므로 점유 표시
                visited[x] = 1
            break                      # 반복문 종료
        if visited[now] != 0:          # 탐색 도중에 점유된 땅을 만난다면
            flag = now                 # 점유된 땅 번호 저장하기
        now = now // 2
        arr.append(now)


    print(flag)
```

