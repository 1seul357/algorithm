```python
'''
반례 = [['ICN', 'B'], ['ICN', 'C'] ,['C', 'D'], ['D', 'ICN']]
'''
answer = []
def dfs(isvisited, now, route, cnt, li):
    if cnt == len(route):   # 모든 경로를 탐색했으면
        answer.append(li)   # answer에 추가
        return
    for i in range(len(route)):
        # 아직 방문 안했고, 다음 공항으로 이동할 수 있다면
        if isvisited[i] == 0 and now == route[i][0]:  
            isvisited[i] = 1   # 방문 체크
            dfs(isvisited, route[i][1], route, cnt+1, li+[route[i][1]])  # dfs 탐색
            isvisited[i] = 0   # 다시 0으로


def solution(tickets):
    tickets.sort()    # 알파벳 순으로 방문하기 위해 정렬
    visited = [0]*len(tickets)  # 방문체크 리스트

    for i in range(len(tickets)):
        for j in range(len(tickets)):
            # 출발점 찾기
            if tickets[i][0] == "ICN":   # ICN이라면
                visited[i] = 1   # 방문 체크
                dfs(visited, tickets[i][1], tickets, 1, ["ICN"]+[tickets[i][1]])
                visited[i] = 0  # 모든 도시를 방문할 수 있는 출발점이 아닐 수 있으므로 다시 0으로
                if len(answer) >= 1:
                    break
                    
    return answer[:][0]
```

