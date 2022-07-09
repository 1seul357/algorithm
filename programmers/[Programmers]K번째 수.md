**문제**

> 배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다. 배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

</br>

**소스코드**

```python
def solution(array, commands):
    answer = []
    
    for i in range(len(commands)):
        tmp = array[commands[i][0]-1 : commands[i][1]]
        tmp.sort()
        answer.append(tmp[commands[i][2]-1])
    return answer
```

