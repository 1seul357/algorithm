### 문제

네트워크란 컴퓨터 상호 간에 정보를 교환할 수 있도록 연결된 형태를 의미합니다. 예를 들어, 컴퓨터 A와 컴퓨터 B가 직접적으로 연결되어있고, 컴퓨터 B와 컴퓨터 C가 직접적으로 연결되어 있을 때 컴퓨터 A와 컴퓨터 C도 간접적으로 연결되어 정보를 교환할 수 있습니다. 따라서 컴퓨터 A, B, C는 모두 같은 네트워크 상에 있다고 할 수 있습니다.

컴퓨터의 개수 n, 연결에 대한 정보가 담긴 2차원 배열 computers가 매개변수로 주어질 때, 네트워크의 개수를 return 하도록 solution 함수를 작성하시오.

##### 제한사항

- 컴퓨터의 개수 n은 1 이상 200 이하인 자연수입니다.
- 각 컴퓨터는 0부터 `n-1`인 정수로 표현합니다.
- i번 컴퓨터와 j번 컴퓨터가 연결되어 있으면 computers[i][j]를 1로 표현합니다.
- computer[i][i]는 항상 1입니다.

</br>

</br>

### 해결방법

- DFS
- 만약 컴퓨터가 방문체크가 되어 있는 상태라면 이전의 컴퓨터 DFS 탐색에서 연결되어 있는 것이므로 DFS 탐색을 하지 않는다.
- 방문체크가 되어 있지 않다면 이전 탐색에서 연결되지 않은 새로운 네트워크 이므로 탐색 후 `answer + 1` 한다.

</br>

</br>

### 소스코드

```python
def solution(n, computers):
    def dfs(k):
        for i in range(n):
            if computers[k][i] == 1 and visited[i] == 0:
                visited[i] = 1
                dfs(i)
                
    answer = 0
    visited = [0]*n
    num = visited.count(1)
    
    for i in range(n):
        if visited[i] == 0:
            visited[i] = 1
            dfs(i)
            answer += 1
                
    return answer
```

