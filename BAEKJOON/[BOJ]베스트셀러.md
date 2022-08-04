**문제**

> 김형택은 탑문고의 직원이다. 김형택은 계산대에서 계산을 하는 직원이다. 김형택은 그날 근무가 끝난 후에, 오늘 판매한 책의 제목을 보면서 가장 많이 팔린 책의 제목을 칠판에 써놓는 일도 같이 하고 있다.
>
> 오늘 하루 동안 팔린 책의 제목이 입력으로 들어왔을 때, 가장 많이 팔린 책의 제목을 출력하는 프로그램을 작성하시오.

</br>

**해결방법**

- 딕셔너리 사용
- 가장 큰 수를 꺼내서 그 수에 해당하는 책의 제목 ans 리스트에 추가
- ans 정렬 후 가장 큰 값 출력

</br>

**소스코드**

```python
N = int(input())
dic = {}
ans = []

for i in range(N):
    book = input()
    if book in dic:
        dic[book] += 1
    else:
        dic[book] = 1

max_book = max(dic, key=dic.get)
max_num = dic[max_book]

for key in dic:
    if dic[key] == max_num:
        ans.append(key)

ans.sort()
print(ans[0])
```

