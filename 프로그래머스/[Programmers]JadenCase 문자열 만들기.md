### 문제

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

##### 제한 조건

- s는 길이 1 이상 200 이하인 문자열입니다.
- s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
  - 숫자는 단어의 첫 문자로만 나옵니다.
  - 숫자로만 이루어진 단어는 없습니다.
  - 공백문자가 연속해서 나올 수 있습니다.

</br>

</br>

### 해결방법

- 숨겨진 반례들이 많다. 문제 자체는 쉬웠지만 반례 처리가 오래 걸림.
- 첫번째 문자가 숫자여도 그 다음 문자에 대문자가 섞여 있을 수 있다. 그러므로 for 문을 통해 확인할 수 있도록 해야 한다.
- 공백이 연속해서 나올 수 있다. 공백도 출력되어야 하므로 `tmp += ''` 을 통해 공백도 더해준다.
- 공백 이후 문자를 대문자로 처리하기 위해 flag 변수를 사용했다. flag가  0이면 첫 번째 문자를 아직 대문자로 바꾸지 않은 것이다. 대문자로 바꾸면 flag를 1로 만들어서 그 다음 문자열부터는 대문자로 바뀌지 않게 처리한다.

</br>

</br>

### 소스코드

```python
def solution(s):
    arr = s.split(' ')
    answer = []
    
    for word in arr:
        tmp = ''
        j, flag = 0, 0
        if word == '':
            tmp += ''
        elif word[0].isdigit():
            j = 1
            tmp = word[0]
        for i in range(j, len(word)):
            if i == 0 and flag == 0:
                tmp = word[i].upper()
                flag = 1
            elif word[i].upper():
                tmp += word[i].lower()
        answer.append(tmp)
    

    return ' '.join(answer)
```

