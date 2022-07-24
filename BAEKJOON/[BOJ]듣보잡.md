**문제**

> 김진영이 듣도 못한 사람의 명단과, 보도 못한 사람의 명단이 주어질 때, 듣도 보도 못한 사람의 명단을 구하는 프로그램을 작성하시오.

</br>

**해결방법**

- 반복문을 다 돌면서 체크하면 시간초과 발생
- set을 통해 이름 입력받으면서 중복 제거
- 공통되는 이름 꺼내서 arr 리스트에 저장

</br>

**소스코드**

```python
N, M = map(int, input().split())
check = set()
check_name = set()

for _ in range(N):
    check.add(input())

for _ in range(M):
    check_name.add(input())

arr = sorted(list(check & check_name))

print(len(arr))

for i in range(len(arr)):
    print(arr[i])
```

