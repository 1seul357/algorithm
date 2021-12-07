```python
def inorder(num):
    if num != 0:                   # num이 0이면 리턴
        inorder(arr1[num])         # 왼쪽 자식 노드 탐색
        print(array[num], end="")  # 왼쪽 자식 노드 탐색 후 노드 출력 <리턴 후 출력>
        inorder(arr2[num])         # 오른쪽 자식 노드 탐색

T = 10
for TC in range(T):
    N = int(input())
    array = [0]*(N+1)
    arr1 = [0]*(N+1)    # 왼쪽 자식 노드
    arr2 = [0]*(N+1)    # 오른쪽 자식 노드

    for i in range(N):
        li = input().split()
        index = int(li[0])   # 첫번째 요소 정수로 바꾸기
        array[index] = li[1]   # 영문 저장
        if len(li) >= 3:     # 왼쪽 자식 노드 있으면
            arr1[index] = int(li[2])
            if len(li) >=4:  # 오른쪽 자식 노드 있으면
                arr2[index] = int(li[3])
    print('#{} '.format(TC+1), end="")
    inorder(1)
    print()
```

