### 문제

ROR 게임은 두 팀으로 나누어서 진행하며, 상대 팀 진영을 먼저 파괴하면 이기는 게임입니다. 따라서, 각 팀은 상대 팀 진영에 최대한 빨리 도착하는 것이 유리합니다.

지금부터 당신은 한 팀의 팀원이 되어 게임을 진행하려고 합니다. 다음은 5 x 5 크기의 맵에, 당신의 캐릭터가 (행: 1, 열: 1) 위치에 있고, 상대 팀 진영은 (행: 5, 열: 5) 위치에 있는 경우의 예시입니다. 검은색 부분은 벽으로 막혀있어 갈 수 없는 길이며, 흰색 부분은 갈 수 있는 길입니다. 캐릭터가 움직일 때는 동, 서, 남, 북 방향으로 한 칸씩 이동하며, 게임 맵을 벗어난 길은 갈 수 없습니다.

게임 맵의 상태 maps가 매개변수로 주어질 때, 캐릭터가 상대 팀 진영에 도착하기 위해서 지나가야 하는 칸의 개수의 **최솟값**을 return 하도록 solution 함수를 완성해주세요. 단, 상대 팀 진영에 도착할 수 없을 때는 -1을 return 해주세요.

##### 제한사항

- maps는 n x m 크기의 게임 맵의 상태가 들어있는 2차원 배열로, n과 m은 각각 1 이상 100 이하의 자연수입니다.
  - n과 m은 서로 같을 수도, 다를 수도 있지만, n과 m이 모두 1인 경우는 입력으로 주어지지 않습니다.
- maps는 0과 1로만 이루어져 있으며, 0은 벽이 있는 자리, 1은 벽이 없는 자리를 나타냅니다.
- 처음에 캐릭터는 게임 맵의 좌측 상단인 (1, 1) 위치에 있으며, 상대방 진영은 게임 맵의 우측 하단인 (n, m) 위치에 있습니다.

</br>

</br>

### 해결방법

- BFS
- visited 리스트를 사용해서 이동해야 하는 칸의 수 체크
- 만약 다음으로 이동해야 하는 칸이 0이면 아직 확인하지 않은 경로이므로 체크하고, queue에 경로를 추가한다.
- `visited[r-1][c-1]` 이 0이면 도달하지 못한 것이므로 -1, 0이 아니면 이동 경로 칸의 수 return
- 통과는 했지만 효율성이 좋은 코드가 아니라서 좀 더 고민해봐야 할 것 같다.😢

</br>

</br>

### 소스코드

```python
from collections import deque

def solution(maps):
    r = len(maps)
    c = len(maps[0])
    visited = [[0]*c for _ in range(r)]
    queue = deque()
    queue.append([0, 0])
    visited[0][0] = 1

    while queue:
        x, y = queue.popleft()
        dx = [-1, 1, 0, 0]
        dy = [0, 0, -1, 1]
        for i in range(4):
            nx = x + dx[i]
            ny = y + dy[i]
            if 0 <= nx < r and 0 <= ny < c and maps[nx][ny] == 1:
                if visited[nx][ny] == 0:
                    visited[nx][ny] = visited[x][y] + 1
                    queue.append([nx, ny])

    if visited[r-1][c-1] == 0:
        answer = -1
    else:
        answer = visited[r-1][c-1]

    return answer
```

