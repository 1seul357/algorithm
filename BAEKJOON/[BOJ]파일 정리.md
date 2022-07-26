**문제**

> 바탕화면의 파일들에는 값진 보물에 대한 정보가 들어 있어. 하나라도 지우게 된다면 보물은 물론이고 다시는 노트북을 쓸 수 없게 될 거야. 파일들을 잘 분석해서 보물의 주인공이 될 수 있길 바랄게. 힌트는 “확장자”야.
>
> - 파일을 확장자 별로 정리해서 몇 개씩 있는지 알려줘
> - 보기 편하게 확장자들을 사전 순으로 정렬해 줘
>
> 그럼 보물의 절반을 얻어내기 위해 얼른 스브러스의 노트북 파일 정리를 해줄 프로그램을 만들자!

</br>

**해결방법**

- 리스트 전체 탐색하면 시간초과 -> 딕셔너리 사용해야 함
- `split(".")[1]` 로 하면 확장자만 딕셔너리에 키 값으로 넣을 수 있다.
- 반복문을 통해 딕셔너리에 동일한 확장자가 있으면 값만 + 1 하고, 확장자가 없으면 1을 추가해준다.
- key를 기준으로 정렬하고, 출력한다.

</br>

**소스코드**

```python
N = int(input())
ans = {}

for i in range(N):
    tmp = input().strip()
    file_name = tmp.split(".")[1]
    if file_name in ans:
        ans[file_name] += 1
    else:
        ans[file_name] = 1

answer = sorted(ans.keys())

for i in range(len(answer)):
    print(answer[i], ans[answer[i]])
```

