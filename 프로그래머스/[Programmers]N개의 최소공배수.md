### 문제

두 수의 최소공배수(Least Common Multiple)란 입력된 두 수의 배수 중 공통이 되는 가장 작은 숫자를 의미합니다. 예를 들어 2와 7의 최소공배수는 14가 됩니다. 정의를 확장해서, n개의 수의 최소공배수는 n 개의 수들의 배수 중 공통이 되는 가장 작은 숫자가 됩니다. n개의 숫자를 담은 배열 arr이 입력되었을 때 이 수들의 최소공배수를 반환하는 함수, solution을 완성해 주세요.

##### 제한 사항

- arr은 길이 1이상, 15이하인 배열입니다.
- arr의 원소는 100 이하인 자연수입니다.

</br>

</br>

### 해결방법

- 내림차순으로 정렬하고, 가장 큰 값을 기준으로 모든 값을 나눈다.
- 나누는 과정에서 공배수가 될 수 없으면 break 하고, 공배수가 될 수 있으면 `ans` 리스트에 추가한다.
- `ans` 리스트와 `arr` 리스트의 길이가 같으면 모든 값이 공배수가 될 수 있는 것이므로 값을 출력한다.

 </br>

</br>

### 소스코드

```python
def solution(arr):
    n = 1
    arr.sort(reverse=True)

    while True:
        ans = []
        n += 1
        answer = arr[0] * n
        for num in arr:
            if answer % num != 0:
                break
            else:
                ans.append(num)
        if len(ans) == len(arr):
            return answer
            break
```

