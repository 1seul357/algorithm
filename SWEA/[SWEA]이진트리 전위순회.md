```python
def preorder(num):
    print(num, end=" ")
    if node[num*2] != 0:   # 0은 출력되지 않도록 조건문 설정
        preorder(node[num*2])
    if node[num*2+1] != 0:
        preorder(node[num*2+1])

T = int(input())

for TC in range(T):
    N = int(input())
    node = ([0]*(N+1))*2  # 노드를 1번부터 사용할 것이므로 총 N+1개를 만들고, 왼쪽자식과 오른쪽 자식을 저장해야하기 때문에 *2를 해준다.
    for i in range(N-1):  # 반복은 총 N번
        a, b = map(int, input().split())
        if node[a*2] == 0:      # 이진트리가 아니지만 리스트와 인덱스를 이진트리처럼 사용한다.
            node[a*2] = b       # 왼쪽자식은 짝수번째 노드에
        else:
            node[a*2+1] = b     # 오른쪽자식은 홀수번째 노드에 저장

    print('#{} '.format(TC+1), end="")
    preorder(1)
```

