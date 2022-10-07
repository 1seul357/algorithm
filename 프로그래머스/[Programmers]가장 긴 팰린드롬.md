### 문제

앞뒤를 뒤집어도 똑같은 문자열을 팰린드롬(palindrome)이라고 합니다.
문자열 s가 주어질 때, s의 부분문자열(Substring)중 가장 긴 팰린드롬의 길이를 return 하는 solution 함수를 완성해 주세요.

예를들면, 문자열 s가 "abcdcba"이면 7을 return하고 "abacde"이면 3을 return합니다.

##### 제한사항

- 문자열 s의 길이 : 2,500 이하의 자연수
- 문자열 s는 알파벳 소문자로만 구성

</br>

</br>

### 해결방법

- 뒤에서부터 시작해서 팰린드롬인지 확인한다.
- 만약 현재 저장된 가장 긴 길이보다 확인하는 문자열의 길이가 작다면 다음 인덱스로 넘긴다. (효율성 해결)
- 팰린드롬이라면 가장 긴 문자열인지 확인하고, answer에 저장한다.
- 팰린드롬이 없다면 1을 반환해야 한다.

</br>

</br>

```python
def solution(s):
    answer = 1

    for i in range(len(s)):
        for j in range(len(s), -1, -1):
            if len(s[i:j]) <= answer:
                continue
            if s[i:j] == s[i:j][::-1]:
                answer = max(len(s[i:j]), answer)

    return answer
```

