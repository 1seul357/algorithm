**문제**

> IPv6의 주소는 32자리의 16진수를 4자리씩 끊어 나타낸다. 이때, 각 그룹은 콜론 (:)으로 구분해서 나타낸다.
>
> ```
> 2001:0db8:85a3:0000:0000:8a2e:0370:7334
> ```
>
> 1. 각 그룹의 앞자리의 0의 전체 또는 일부를 생략 할 수 있다. 위의 IPv6을 축약하면, 다음과 같다
>
> ```
> 2001:db8:85a3:0:00:8a2e:370:7334
> ```
>
> 1. 만약 0으로만 이루어져 있는 그룹이 있을 경우 그 중 한 개 이상 연속된 그룹을 하나 골라 콜론 2개(::)로 바꿀 수 있다.
>
> ```
> 2001:db8:85a3::8a2e:370:7334
> ```
>
> 2번째 규칙은 모호함을 방지하기 위해서 오직 한 번만 사용할 수 있다.
>
> 올바른 축약형 IPv6주소가 주어졌을 때, 이를 원래 IPv6 (32자리의 16진수)로 복원하는 프로그램을 작성하시오.

</br>

**해결방법**

- `:` 기준으로 잘라서 문자열의 길이가 4가 아니라면 앞에 0을 붙여주면 된다.
- 만약 문자열의 길이가 0이라면 `:`이므로 0000 추가
- flag 통해서 `:` 인지 `::` 인지 체크 

</br>

**소스코드**

```python
arr = input().split(":")
array = []
flag = 0


if arr[-1] == "":
    arr = arr[:-1]
if arr[0] == "":
    arr = arr[1:]

for tmp in arr:
    if len(tmp) == 0 and flag == 0:
        for _ in range(9-len(arr)):
            flag = 1
            array.append("0000")
    elif len(tmp) == 0 and flag == 1:
        array.append("0000")
    elif len(tmp) == 4:
        array.append(tmp)
    elif len(tmp) < 4:
        while True:
            tmp = "0" + tmp
            if len(tmp) == 4:
                break
        array.append(tmp)

for i in range(len(array)):
    if i == len(array)-1:
        print(array[i])
    else:
        print(array[i], end=":")
```

숨겨진 테스트케이스가 있어서 반례 찾아서 해결했다. 맨 앞에 `1:2:3:4:5:6:7::` `::1:2:3:4:5:6:7` 인 경우 앞 뒤를 자르고 해야 한다.