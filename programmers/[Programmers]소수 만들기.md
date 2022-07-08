**문제**

> 주어진 숫자 중 3개의 수를 더했을 때 소수가 되는 경우의 개수를 구하려고 합니다. 숫자들이 들어있는 배열 nums가 매개변수로 주어질 때, nums에 있는 숫자들 중 서로 다른 3개를 골라 더했을 때 소수가 되는 경우의 개수를 return 하도록 solution 함수를 완성해주세요.

</br>

**해결방법**

- 세개의 반복문을 통해 총 3개의 숫자 뽑을 수 있도록 함
- flag 변수 만들고, 반복문을 돌면서 소수가 안되면 flag를 1로 바꾸고, break 실행
- 반복문이 끝나면 flag가 0인지 확인하면서 answer += 1

</br>

**소스코드**

```python
def solution(nums):
    answer = 0
    flag = 0
    for i in range(0, len(nums)-2):
        for j in range(i+1, len(nums)-1):
            for k in range(j+1, len(nums)):
                flag = 0
                tmp = nums[i] + nums[j] + nums[k];
                for l in range(2, tmp):
                    if tmp % l == 0:
                        flag = 1
                        break
                if flag == 0:
                    answer += 1

    return answer
```

