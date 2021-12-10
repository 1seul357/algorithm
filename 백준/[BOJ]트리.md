```python
'''
삭제되는 노드와 연결되어 있는 노드는 dfs로 탐색
자식 노드의 수는 counts 리스트 사용 -> counts에 값이 0이라면 자식 노드가 없다는 뜻
리프 노드의 수 = counts 리스트에서 0의 수 합
삭제되는 노드와 연결되어 있는 노드 값을 모두 -2로 바꿈

반례 ) 0번 인덱스가 루트 노드가 아닐 수 있음
'''


# 삭제되는 노드와 연결되어 있는 노드들의 값을 -2로 바꿔주기 위한 dfs
def dfs(tmp):
    for i in range(0, len(tree)):
        # 아직 노드를 방문하지 않았고, tree에 저장된 값이 삭제되는 부모 노드가 맞으면
        if visited[i] == 0 and tree[i] == tmp:
            visited[i] = 1       # 방문 체크
            temp = tmp         # dfs 탐색이 끝난 후에 값 원래대로 바꿔야하므로 tmp를 temp에 저장
            tmp = i              # tmp에 새로운 부모 노드 저장
            tree[i] = -2         # tree 값을 -2로 바꾸기 (삭제되는 노드)
            dfs(tmp) 
            tmp = temp         # 값 원래대로 바꾸기 (값을 안바꾸면 왼쪽 자식 노드만 제대로 탐색됨)


N = int(input())
tree = list(map(int, input().split()))
n = int(input())
visited = [0]*N                 # 방문 체크
counts = [0]*N                  # 리프 노드의 수 찾기 위한 리스트

tree[n] = -2                    # 삭제되는 노드

dfs(n)                          # dfs(삭제되는 노드의 인덱스)
 
for i in range(len(tree)):      # 자식 노드 개수 세는 반복문
    if tree[i] == -2:           # 값이 -2 라면 (삭제되는 노드들)
        counts[i] = -2          # counts 리스트도 값을 -2로 지정하고,
        continue                # continue
    if tree[i] == -1:           # 값이 -1 라면 (루프 노드)
        continue                # contiune
    counts[tree[i]] += 1        # 특정 노드의 자식 노드가 있으면 + 1


ans = counts.count(0)      # 리프 노드의 개수 찾기

print(ans)
```

