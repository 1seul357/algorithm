### 문제

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

##### 제한사항

- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

</br>

</br>

### 해결방법

- 해시
- 완주한 선수들의 목록을 딕셔너리에 넣는다.
- 참가한 사람들 중 딕셔너리에 없는 선수가 있다면 해당 선수가 완주하지 못한 선수이므로 바로 반복문을 종료한다.
- 만약 모든 선수가 딕셔너리에 있다면 딕셔너리의 value 값이 0이 아닌 선수를 찾는다. 해당 선수가 완주하지 못한 선수이다.

</br>

</br> 

### 소스코드

```python
def solution(participant, completion):
    answer = ''
    dic = {}
    
    for people in completion:
        if people in dic:
            dic[people] += 1
        else:
            dic[people] = 1
            
    for people in participant:
        if people in dic:
            dic[people] -= 1
        else:
            answer = people
            exit
            
    for key, value in dic.items():
        if value != 0:
            answer = key
            
    return answer
```

