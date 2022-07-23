**문제**

> 그룹 단어란 단어에 존재하는 모든 문자에 대해서, 각 문자가 연속해서 나타나는 경우만을 말한다. 예를 들면, ccazzzzbb는 c, a, z, b가 모두 연속해서 나타나고, kin도 k, i, n이 연속해서 나타나기 때문에 그룹 단어이지만, aabbbccb는 b가 떨어져서 나타나기 때문에 그룹 단어가 아니다.
>
> 단어 N개를 입력으로 받아 그룹 단어의 개수를 출력하는 프로그램을 작성하시오.

</br>

**해결방법**

- 문자열 체크. 하나씩 자르면서 체크하기
- array 배열에 동일한 값이 있고, array의 가장 최근 문자가 현재의 문자와 일치하지 않는다면 break (연속해서 나타나는 것이 아니라 떨어져서 나타난 것이므로)
- 조건문을 통과하면서 하나씩 더한 cnt가 문자열의 길이와 일치하면 문자열 끝까지 체크한 것이므로 count + 1

</br>

**소스코드**

```python
N = int(input())

string = []
count = 0

for i in range(N):
    str = input()
    string.append(str)

for tmp in string:
    array = []
    cnt = 0
    for temp in tmp:
        if temp in array and temp != array[-1]:
            break
        else:
            cnt += 1
            array.append(temp)
    if cnt == len(tmp):
        count += 1

print(count)
```

