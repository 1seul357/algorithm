### 문제

자연수 n이 주어졌을 때, n의 다음 큰 숫자는 다음과 같이 정의 합니다.

- 조건 1. n의 다음 큰 숫자는 n보다 큰 자연수 입니다.
- 조건 2. n의 다음 큰 숫자와 n은 2진수로 변환했을 때 1의 갯수가 같습니다.
- 조건 3. n의 다음 큰 숫자는 조건 1, 2를 만족하는 수 중 가장 작은 수 입니다.

예를 들어서 78(1001110)의 다음 큰 숫자는 83(1010011)입니다.

자연수 n이 매개변수로 주어질 때, n의 다음 큰 숫자를 return 하는 solution 함수를 완성해주세요.

##### 제한 사항

- n은 1,000,000 이하의 자연수 입니다.

</br>

</br>

### 해결방법

- 이진수로 변환할 때, 내장함수를 사용할 수 있지만 사용하지 않는 방법으로 풀이
- binary_check 함수를 만들어서 1의 수를 리턴한다.
- 반복문을 통해 n부터 시작해서 1의 수가 같은 숫자가 나올 때 까지 n + 1 하면서 반복한다.
- 만약 1의 수가 같은 숫자가 나오면 반복문을 종료한다.

</br>

</br>

### 소스코드

```python
def binary_check(num):
    tmp = ''
    while num != 0:
        if num % 2 == 1:
            tmp = '1' + tmp
        else:
            tmp = '0' + tmp
        num //= 2
    count = tmp.count('1')
    return count

def solution(n):
    ans = binary_check(n)
    while True:
        n += 1
        cnt = binary_check(n)
        if ans == cnt:
            break
    return n
```

