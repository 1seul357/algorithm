**문제**

> 문자열 S가 주어졌을 때, S의 서로 다른 부분 문자열의 개수를 구하는 프로그램을 작성하시오.
>
> 부분 문자열은 S에서 연속된 일부분을 말하며, 길이가 1보다 크거나 같아야 한다.
>
> 예를 들어, ababc의 부분 문자열은 a, b, a, b, c, ab, ba, ab, bc, aba, bab, abc, abab, babc, ababc가 있고, 서로 다른것의 개수는 12개이다.

</br>

**해결방법**

- 이중 반복문을 통해 만들 수 있는 문자열 모두 ans에 추가
- set을 통해 중복 제거하고, 수 출력

</br>

**소스코드**

```python
str = input()
ans = []

for i in range(len(str)):
    tmp = ''
    for j in range(i, len(str)):
        tmp += str[j]
        ans.append(tmp)

print(len(set(ans)))
```

